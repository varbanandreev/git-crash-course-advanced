# Git Crash Course Advanced

## Commands reference
```
git clone https://github.com/varbanandreev/git-crash-course-advanced.git
git checkout -b remove-quote
git add linus.txt
git commit -m "Remove last quote"
git checkout master
git merge remove-quote
git push
git merge origin/microsoft
git add linus.txt
git merge --continue
git push
```

```
git checkout microsoft
git rebase origin/microsoft-software
git add linus.txt
git rebase --continue
git push --force
git checkout microsoft-software
git pull
```

```
git checkout bugfix/extract-quotes
git rebase -i master
```

## Challenge 1
- Open a browser of your choice and log into your GitHub account. Navigate to https://github.com/varbanandreev/git-crash-course-advanced and fork the **git-crash-course-advanced** repository.
- When forking the repo, make sure to copy all branches by unselecting the checkbox next to "Copy the master branch only".
- Clone the forked repo locally.
- Create a new branch and name it **remove-quote**.
- Open **linus.txt** and remove the last line - the one starting with "Microsoft ...". Save the file.
- Commit the changes with "Remove last quote" as a commit message.
- Merge the newly created branch **remove-quote** into **master**. In order to do so, you need to checkout **master** and then execute the merge command.
- Push the changes made on **master**. You may have to enter your GitHub credentials.
- Execute the merge command to merge branch **origin/microsoft** into **master**. You should receive a message, saying that there are merge conflicts in **linus.txt**.
- Open **linus.txt** and resolve the merge conflicts by accepting the changes made by both branches. You need to delete the extra lines starting with ```<<<<<<<```, ```=======``` and ```>>>>>>>```. Save and close the file.
- Complete the merge by staging the changes and executing ```git merge --continue```. Name your commit "Merge microsoft branch".
- Push your changes.
- Your log should look like this:
  - (HEAD -> master, origin/master, origin/HEAD) Merge microsoft branch
  - (remove-quote) Remove last quote
  - Add README
  - (origin/microsoft) Change Microsoft quote
  - Add linus text file
- If you compare **master** to **remove-quote** you should have one new line starting with "In my opinion ...".

## Challenge 2
- Checkout branch **microsoft** and use the rebase command to rebase **microsoft** on **origin/microsoft-software**. A message should appear, saying that there are merge conflicts in **linus.txt**.
- Open the file and resolve the merge conflicts by accepting the changes made by both branches. You need to delete the extra lines starting with ```<<<<<<<```, ```=======``` and ```>>>>>>>```. Save and close the file.
- Finish the rebase process by staging your changes and instructing Git to continue with the rebase.
- Push the changes made on the **microsoft** branch. Keep in mind that you have changed existing branch history.
- Submit a pull request to merge **microsoft** to **microsoft-software** in your forked repo. After clicking on 'New pull request', make sure to change the value of the first dropdown - `base fork: varbanandreev/git-crash-course-advanced` to your own repo - `<github-account>/git-crash-course-advanced`.
- Select **microsoft-software** for the base branch and set the compare branch to **microsoft**. Click on the 'Create pull request' button and then confirm the merge.
- Now, let's complete the pull request. Click the 'Merge pull request' button.
- After you have completed the pull request, checkout the **microsoft-software** branch and pull the latest changes.
- After pulling, your log should look like this:
  - (HEAD -> microsoft-software, origin/microsoft-software) Merge pull request #1 from varbanandreev/microsoft
  - (origin/microsoft, microsoft) Change Microsoft quote
  - Change 'operating systems' to 'software'
  - Add linus text file

## Challenge 3
- Let's say we want to extract the **quotes** section from **linus.txt** into another file. We already have a branch that does it - **bugfix/extract-quotes**.
- However, this branch does the work in multiple commits, which can be squashed into a single commit. That is what you must do.
- Checkout **bugfix/extract-quotes**. Notice that its log contains 6 commits. Begin an interactive rebase on **master**.
- Squash all trivial commits - the commits starting with "Remove ...". Reword the first commit to give it a better commit message - "Extract quotes into separate file".
- Complete the interactive rebase.
- Your log should now be shortened to:
  - (HEAD -> bugfix/extract-quotes) Extract quotes into separate file
  - (origin/master, origin/HEAD, master) Add README
  - Add linus text file
- Push your changes in the **bugfix/extract-quotes** branch. Keep in mind that you have changed existing branch history.
