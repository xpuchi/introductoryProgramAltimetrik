# What are Git Merge and Git Rebase?
Git Merge and Git Rebase are both used to combine the changes of branches but in a distinct way.

- **Git Merge** - For developers using version control systems, merging is a prevalent method. Merging takes the contents of a source branch and combines them with a target branch. Only the target branch is updated in this process. The history of the source branch remains similar.

- **Git Rebase** - Another way to integrate modifications from one branch to another is by Rebase. Rebase compresses all the modifications into a single patch. The patch is then inserted into the target branch. This operation works by going to the common ancestor of the two branches (the one you’re on and the one you’re rebasing onto), getting the diff introduced by each commit of the branch you’re on, saving those diffs to temporary files, resetting the current branch to the same commit as the branch you are rebasing onto, and finally applying each change in turn.
"The golden rule of git rebase is to never use it on public branches".
The goal of a rebase is to change the start (or base) of a branch. So, instead of the branch starting from the original point (ie: commit 2) you’re bringing it forwards or backwards to a different point in time. **Rebasing allows you to maintain a clean commit history showing the exact chain of development for your product**.

The key difference between merge and rebase is that while **merge preserves history as it happened, rebase rewrites it**.

![DifferenceBetweenMergeReverse](https://miro.medium.com/max/1400/1*Y77kjfj3xgPz_YRYa8Zmsg.png)
As we can see above, the merge operation intertwined the branches together by creating a new single merge commit (C7), causing a diamond shaped non-linear history — essentially preserving history as it happened. By comparing this result with the outcome from the rebase action we see that no merge commit was created, instead the two commits C5 and C6 simply got rewinded and reapplied straight on top of C4, keeping the history linear. If we scrutinise the two reapplied commits even further, we can see that the hashes have changed, indicating that rebase truly rewrites history.

- **Squash** - To "squash" in Git means to combine multiple commits into one. You can do this at any point in time (by using Git's "Interactive Rebase" feature), though it is most often done when merging branches.

There is no such thing as a stand-alone git squash command. Instead, squashing is rather an option when performing other Git commands like interactive rebase or merge. You can merge all of your commits from a feature branch into a single commit, which can then be added to the end of the main branch

![squashrebase](https://miro.medium.com/max/1358/1*ZmKOAvJJFCmn05WFPiIaBw.png)
In this example, after the 2 feature branches have been rebased and merged in, instead of being 3 commits each, they’re now just 1. All of the changes inside those branches have been turned into a single “Feature” commit.

---

Sources:
- https://betterprogramming.pub/differences-between-git-merge-and-rebase-and-why-you-should-care-ae41d96237b6
- https://www.loginradius.com/blog/engineering/git-rebase-vs-git-merge/
- https://medium.com/swlh/squash-and-rebase-git-basics-5cb1be1e0dac
- https://www.git-tower.com/learn/git/faq/git-squash