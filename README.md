# Branching Policies

I am [Òscar Tarrés](https://github.com/oscarta3), student of the [Bachelor’s Degree in Video Games by UPC at CITM](https://www.citm.upc.edu/ing/estudis/graus-videojocs/). This content is generated for the second year's subject Project 2, under supervision of lecturer [Ramon Santamaria](https://github.com/raysan5).

This research project is about Branching Policies.

## Concept

Branch policies help teams protect their important branches of development, organize, solve problems in simpler ways and to work in parallel. They allow us to isolate work in progress from the already completed work in our master branch, guarantee changes before they get to master and limit who can contribute to specific branches.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/1.png)


To see the utility and all the advantages of Branching Policies, we will see two different ways of working. First of all we will check the Trunk-Based Development, a light branch policy, and then we will see the Feature Branching Development, used by most companies in the industry.

## Trunk-based Development

On this branching model all the developers work and collaborate on code in a single branch called ‘trunk’ or ‘master’ and then there is a separate branch for the releases. It resist any pressure to create other long-lived development branches by employing documented techniques. In this case if someone checks-in wrong code everyone has to wait for it to get fixed in order to continue working on the other parts. This model has been outdated by the Feature Branching Development.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/trunk-image.PNG)


**There are two types of trunk based development.**

**Trunk-Based Development for smaller teams**: Normally used when a team is small (not always the case but usually larger teams uses the PR process). Where you can take all your commits and commit them directly to your branch (usually called master). **All the implementations must run the build first.**

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/trunk1b.png)


**Trunk-Based Development**: This type is the most common one. Developers commit into a feature branch (short-lived and product of a single person) and then create a PR (pull request). After reviewing the code, we merge the feature branch into the main branch (master branch). 

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/trunk1c.png)


## Feature Branching Development

The Feature Branching Development in which all the features are made external to the main branch and are integrated at the time they are totally completed. As a result, the problem of waiting until the errors were solved in the Trunk-Based development has disappeared but some other inconveniences have appeared. For example, feature branches are used for a large amount of time and, if they are not updated, they could end up giving problems when merging with the main branch. Gitflow is one of the best examples of this branch policy.


### Gitflow

The need of this policy emerge from the fact that organising a group of people to work together, for the same standards, and make it all work perfectly is almost impossible with no clear instructions on what to do in every situation that comes up. Having this rules protects the main branches from possible repository damage since nobody can manipulate them except for the administrators.

The administrator is the only one who has the permission to allow modifications to the main branches, release and hotfixes while the members of the team can pull request and merge branches on which they work. 

There should be more than one kind of administrator, for example Lead programmer and QA Lead. The lead programmer should only manage develop and hotfixes and the QA lead should manage the releases and master branches.


### Structure

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/git-model.png)


### Main branches (master and develop)

The central repo holds two main branches with an infinite lifetime: master and develop. They are both created at the beginning of the project and last until the end of it.

The master branch is only updated with the main stable versions of the project.

The develop branch is the main branch where the code always reflects a state with the latest delivered development changes for the next release. When the code in the develop branch reaches a stable point and is ready to be released, all of the changes should be merged back into master and then tagged with a release number.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/main-branches.png)


### Supporting branches (feature, release and hotfix)

This model uses a variety of supporting branches to work parallelly between team members,  easy tracking of features, prepare the releases and to assist in quickly fixing live production problems. Unlike the main branches, these branches will be removed eventually (limited life time).

**Feature:**
- Branch off from:  develop
- Merge back to: develop
- Branch naming: Anything except master, develop, release or hotfix.

These branches are used to develop new features for the future releases. Every developer works on their own field and tasks to develop those new features mentioned above. These branches have to be updated to avoid problems while merging.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/feature-branchesb.png)


**Release:**
- Branch off from: develop
- Merge back to: develop or master
- Branch naming: release-*

Release branches support preparation of a new production release. When everything from the develop branch is ready and works fine, the release branch is created to fix minor bug and preparing metadata of the launch (version number, build dates, etc.). By doing all of this work on a release branch, the develop branch is cleared to receive features for the next big release.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/release-branches.PNG)


**Hotfix:**
- Branch off from: master
- Merge back to: develop and master
- Branch naming: hotfix-*

Hotfix branches are similar to release branches to prepare for a new release, although they are unplanned. They are created when  there is a critical bug in a version and must be resolved immediately.

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/hotfix-branches.png)


## Github branch protection rules

![Alt Text](https://github.com/oscarta3/BranchingPolicies/blob/master/docs/gitrules.PNG)


## AppVeyor

AppVeyor is one of the multiple apps like Travis CI, Jenkins, etc. that are made to help in the QA process. 

By connecting Appveyor with your Github account and giving it access to the project, their servers will generate a build of the project (needs to be adjusted by the user). 

We can configure Appveyor to do the builds only when a commit is made in some specific branches such as develop, releases, master and hotfix, making the QA team easier to work with.
