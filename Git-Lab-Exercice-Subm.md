# Git-Lab-Exercise-Submission

## Exercice 1

### Main Task

1. Create a new directory and change into it. <br>
    ```mkdir Git-Lab-Exercise && cd Git-Lab-Exercise```
2. Use the init command to create a Git repository in that directory.<br> ```git init```
3. Observe that there is now a .git directory.<br> ```ls -a```
4. Create a README file.<br> ```touch README.md```
5. Look at the output of the status command; the README you created should appear as an
untracked file.<br> ```git status``` <br> 
    ```
    //STDOUT
    On branch master

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        README.md

    nothing added to commit but untracked files present (use "git add" to track)
    ```
6. Use the add command to add the new file to the staging area. Again, look at the output of
the status command. <br> 
    ```git
    git add .
    git status
    ```
    ```
    //STDOUT

    On branch master

    No commits yet

    Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
        new file:   README.md
    ```
7. Now use the commit command to commit the contents of the staging area.<br> 
```git commit -m "Add README.md"```
8. Create a src directory and add a couple of files to it.<br> ```mkdir src```
9. Use the add command, but name the directory, not the individual files. Use the status
command. See how both files have been staged. Commit them. <br> 
    ```
    git add src
    git status
    ```
10. Make a change to one of the files. Use the diff command to view the details of the change.<br>
    ```
    echo This File contains the basic details >> README.md
    git diff
    ```
    ```
    //STDOUT
    diff --git a/README.md b/README.md
    index e69de29..7cec9d2 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +This File contains the basic details
    ```
11. Next, add the changed file, and notice how it moves to the staging area in the status
output. Also observe that the diff command you did before using add now gives no output. <br>
    ```
    git stage .
    git diff
    ```
    Why not? What do you have to do to see a diff of the things in the staging area? (Hint:
    review the slides if you can’t remember.)<br> 
    ```
    Because diff shows changes of files unstaged only. 
    To view diff simply add the option --staged : 
    git diff --staged
    ```

12. Now – without committing – make another change to the same file you changed in step 10.
Look at the status output, and the diff output. Notice how you can have both staged and
unstaged changes, even when you’re talking about a single file. Observe the difference when
you use the add command to stage the latest round of changes. Finally, commit them. You
should now have started to get a feel for the staging area.<br> 
    ```
    open README.md
    git status
    git diff
    git add .
    git commit -m "Updated README.md"
    ```
  - Status and Diff both give different output of the same file README.md as diff only looks at unstaged changes in files. 
13. Use the log command in order to see all of the commits you made so far.<br> 
    ```git log -a```<br> 

    ```
    //STDOUT
    commit 07591e933e87a07fa99a288f97bb293747301cc9 (HEAD -> master)
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 18:03:25 2024 +0530

        Updated README.md

    commit 808ee58d2dfce75ffc455ac63c1bd33b24cc4f5b
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 17:43:43 2024 +0530

    Add README.md
    ```
14. Use the show command to look at an individual commit. How many characters of the
commit identifier can you get away with typing at a minimum? <br> 
    ```
    git show 07591e9
        commit 07591e933e87a07fa99a288f97bb293747301cc9 (HEAD -> master)
        Author: Yash Kabra <yash292kab@gmail.com>
        Date:   Wed Jan 24 18:03:25 2024 +0530

            Updated README.md

        diff --git a/README.md b/README.md
        index e69de29..1b28f9a 100644
        --- a/README.md
        +++ b/README.md
        @@ -0,0 +1,2 @@
        +This File contains the basic details
        +Added some more details
    ```
    - Only 1 Character ;)
15. Make a couple more commits, at least one of which should add an extra file.
    ```
    touch index.html
    git add. 
    git commit -m "Add index.html"
    ```
    ```
    git add. 
    git commit -m "Add content to Index.html"
    ```

## Exercise 2

### Main Task

1. Run the status command. Notice how it tells you what branch you are in. <br> 

    ```git status```
    ```
    On branch master
    nothing to commit, working tree clean
    ```
2. Use the branch command to create a new branch.<br> 
    ```git branch about-page```
3. Use the checkout command to switch to it.<br> 
    ```git checkout about-page```
4. Make a couple of commits in the branch – perhaps adding a new file and/or editing existing
ones. <br> 
    ```
    touch about.html
    git add .
    git diff --staged
    ```
    ```
    //stdout
    diff --git a/about.html b/about.html
    new file mode 100644
    index 0000000..8f67623
    --- /dev/null
    +++ b/about.html
    @@ -0,0 +1,14 @@
    +<!DOCTYPE html>
    +<html>
    +    <head><title> About us</title></head> 
    +    <body>
    +        <h1>About</h1>
    +            <p>This is a sample project for the <strong>Awesome Git Project</p>
    +            <p>
    +                <em>
    +                    Learn Enough™ Git to be dangerous
    +                    Updated About
    +                </em>
    +            </p>
    +    </body>
    +</html>
    ```
    ```git commit -m "Add about.html```
5. Use the log command to see the latest commits. The two you just made should be at the
top of the list.
    ```git log -a```
    
    ```
    //Top two commits
    commit 114da49c8bed7beafb2176efafaf19bb35e2a5ff (HEAD -> about-page)
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 18:20:29 2024 +0530

        Add About.html

    commit b8a13d954720355832f2e2f23ddda0b6522da3b5 (master)
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 18:11:47 2024 +0530

        Add content to Index.html
    ```
6. Use the checkout command to switch back to the master branch. Run log again. Notice
your commits don’t show up now. Check the files also – they should have their original
contents.<br>
    ```
    checkout master
    git log
    ls -a
    ```
7. Use the checkout command to switch back to your branch. Use gitk to take a look at the
commit graph; notice it’s linear.<br>
    ```
    //gitk not found. log --graph similar 
    git log --graph
    ```
8. Now checkout the master branch again. Use the merge command to merge your branch in
to it. Look for information about it having been a fast-forward merge. Look at git log, and
see that there is no merge commit. Take a look in gitk and see how the DAG is linear.
<br>
    ```
    git checkout master
    git merge about-page
    ```
    ```
    //stdout
    Updating b8a13d9..114da49
    Fast-forward
    about.html | 14 ++++++++++++++
    1 file changed, 14 insertions(+)
    create mode 100644 about.html
    ```
9. Switch back to your branch. Make a couple more commits.<br>
    ```
    git checkout about-page 
    git add.
    git commit -m "Removed text describing Image"
    ```
10. Switch back to master. Make a commit there, which should edit a different file from the
ones you touched in your branch – to be sure there is no conflict.<br>
    ```
    git checkout master
    git add .
    git commit -m "Update README for Describing index and about"  
    ```
11. Now merge your branch again. (Aside: you don’t need to do anything to inform Git that you
only want to merge things added since your previous merge. Due to the way Git works, that
kind of issue simply does not come up, unlike in early versions of Subversion.) <br> 
    ```git merge about-page```
12. Look at git log. Notice that there is a merge commit. Also look in gitk. Notice the DAG
    ```
    git log --all --graph
    ```
    ```
    //git graph
        *   commit ed627c362cd27051d34acf59e278aed1983e74e1 (HEAD -> master)
    |\  Merge: f885ee8 174bf46
    | | Author: Yash Kabra <yash292kab@gmail.com>
    | | Date:   Wed Jan 24 18:35:10 2024 +0530
    | | 
    | |     Index Updated
    | | 
    | * commit 174bf46b7a92955a650245546a9dcec5cb872b91 (about-page)
    | | Author: Yash Kabra <yash292kab@gmail.com>
    | | Date:   Wed Jan 24 18:30:34 2024 +0530
    | | 
    | |     Removed Text describing image
    | | 
    * | commit f885ee80be6b4a4b945d79ee2d997610debce6d2
    |/  Author: Yash Kabra <yash292kab@gmail.com>
    |   Date:   Wed Jan 24 18:32:40 2024 +0530
    |   
    |       Update README for Describing index and about
    | 
    * commit 114da49c8bed7beafb2176efafaf19bb35e2a5ff
    | Author: Yash Kabra <yash292kab@gmail.com>
    | Date:   Wed Jan 24 18:20:29 2024 +0530
    | 
    |     Add About.html
    | 
    * commit b8a13d954720355832f2e2f23ddda0b6522da3b5
    | Author: Yash Kabra <yash292kab@gmail.com>
    | Date:   Wed Jan 24 18:11:47 2024 +0530
    | 
    |     Add content to Index.html
    | 
    * commit 4cf82e10243a54a2e55063875fc5b5057c33d49f
    | Author: Yash Kabra <yash292kab@gmail.com>
    | Date:   Wed Jan 24 18:09:01 2024 +0530
    | 
    |     Add index.html
    | 
    * commit 07591e933e87a07fa99a288f97bb293747301cc9
    | Author: Yash Kabra <yash292kab@gmail.com>
    | Date:   Wed Jan 24 18:03:25 2024 +0530
    | 
    |     Updated README.md
    | 
    * commit 808ee58d2dfce75ffc455ac63c1bd33b24cc4f5b
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 17:43:43 2024 +0530
  
      Add README.md
    ```

## Exercise 4

### Main Task
1. Make a commit, and make a silly typo in the commit message.
    <br> 
    ```
    git add .
    git commit -m "Updapeed README.md"
    ```
2. Use the --amend flag to enable you to fix the commit message.<br>
    ```git commit --amend -m "Updated Readme.md"```

3. Look at the log and notice how the mistake is magically gone.<br>
    ```
    //stdout (last 2 commits)

    commit ab256677f3fb031c39622cc0bc63d5aa47bde123 (HEAD -> master)
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Thu Jan 25 11:11:37 2024 +0530

        Updated Readme.md

    commit ed627c362cd27051d34acf59e278aed1983e74e1
    Merge: f885ee8 174bf46
    Author: Yash Kabra <yash292kab@gmail.com>
    Date:   Wed Jan 24 18:35:10 2024 +0530

    Index Updated
    ```
4. Now make a commit where you make a typo in one of the files. Once again, use --amend to
magic away your problems. <br>
    ```
     git diff .

    diff --git a/README.md b/README.md
    index 8ed2cd5..b389af5 100644
    --- a/README.md
    +++ b/README.md
    @@ -1,4 +1,6 @@
    This File contains the basic details
    Added some more details
    The website contains index and about 
    -This is an update
    \ No newline at end of file
    +This is an update
    +
    +The webssssssssite contains information about SDE
    \ No newline at end of file
    ```
    ```
    git commit -m "This message will be changed"
    git diff .
        //STDOUT
    diff --git a/README.md b/README.md
    index b389af5..8c2d7fd 100644
    --- a/README.md
    +++ b/README.md
    @@ -3,4 +3,4 @@ Added some more details
    The website contains index and about 
    This is an update
    
    -The webssssssssite contains information about SDE
    \ No newline at end of file
    +The website contains information about SDE
    \ No newline at end of file
    ```

    ```
    git add .
    git commit --amend -m "Updated README to include SDE info"  
    ```
    ```
    cat README.md
    This File contains the basic details
    Added some more details
    The website contains index and about 
    This is an update
    The website contains information about SDE

    ```
5. Create a branch. Make a commit. <br>
    ```
    git checkout -b contactPage
    git add .
    git commit -m "Add Contact.html" 
    ```
    
6. Now switch back to your master branch. Make a (non-conflicting) commit there also.<br>
    ```
    git checkout master
    git add .
    git commit -m "Add Paragraph about SDE"
    ```
7. Now switch back to your branch.<br>
    ```git checkout contactPage```
8. Use the rebase command in your branch. Look at the DAG in gitk, and note that you have
the commit from the master branch, but no merge commit.<br>
    ```
    git rebase master
        //STDOUT
        Successfully rebased and updated refs/heads/contactPage.
    git merge contactPage
        //STDOUT
        Already up to date.
    ```
9. Make one more commit in your branch.<br>
     ```
    git commit -m "Add refference to contactPage on index"

    //STDOUT
    [contactPage 47e9c52] Add refference to contactPage on index
    2 files changed, 2 insertions(+), 2 deletions(-)
    create mode 100644 Image.jpg
    ```
10. Return to master. Merge your branch. Notice how, thanks to the rebase, this is a fast-
forward merge.<br>
    ```
    git merge contactPage
        Already up to date
        !! because of rebase!!
    ```


## Exercise 5

### main
1. Any time we have for this exercise, you are free to spend practicing whatever you find most
interesting, or feel you have not fully grasped from the previous exercises and want another go
through. Refer to the final section of the course for features you might like to explore.

- **For Ex. 5, Published the complete local repo on github which can be accessed at :** https://github.com/yaxhkabra/GitLabExercise
- Included the Git-Lab-Exercise-Submission.md (this file) in the repo for quick access. 
- Every commit, question, History can be accessed through the repo

    ```
    git remote add Origin https://github.com/yaxhkabra/GitLabExercise.git
    git push -u Origin master
    git log --all --graph
    ```