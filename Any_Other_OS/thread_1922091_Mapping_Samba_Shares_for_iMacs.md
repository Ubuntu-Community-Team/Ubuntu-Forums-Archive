---
title: "Mapping Samba Shares for iMacs"
date: 2012-02-08
forum: Any Other OS
---

### Post by Captain Smiley Pants on 2012-02-08
Hello forum,

I am an intern and have been given a task to integrate our iMac computers with Mac OS X (Lion) into the schools network, specifically with Active Directory.

So far I have managed to bind the computers into Active Directory and start logging users in through their domain credentials. Now I face this challenge:

On Windows, with the group policy set up there is a network share given to every student. When they log onto a computer the U: drive is the drive letter used to reach this, where they can save their information to.

Obviously, OS X doesn't care about group policy and Finder doesn't see the share until I mount it with the terminal. I'd like to be able to write some sort of login script that will see that the user has logged into the computer, use their credentials from Active Directory and map their drive to the computer while in on their session. This is ideal since there will be multiple students using the limited computers.

Any ideas?

---

