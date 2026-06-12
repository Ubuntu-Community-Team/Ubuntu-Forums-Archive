---
title: "How do i download?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Fowlwing on 2007-03-23
Hi i am completely new to Ubuntu.   I tried searching the forums to see if any one has seen this 

I dont know how to download programs.

For example i want to download azureus... but dunno how... if some could help i would be grateful

---

### Post by AndrewBarber on 2007-03-23
Go to Appplications >> Add/Remove Software. Then look for azureus

---

### Post by ardchoille42 on 2007-03-23
> **Fowlwing said:**
> Hi i am completely new to Ubuntu.   I tried searching the forums to see if any one has seen this 

I dont know how to download programs.

For example i want to download azureus... but dunno how... if some could help i would be grateful

When you are looking for a program to install, it's best to follow these rules in this order

1. Open System -> Administration -> Synaptic Package Manager and look for the program there. You can [enable more repositories]("https://help.ubuntu.com/community/Repositories") to have more programs in Synaptic

2. If the program you want isn't in the repos, you can search for a .deb package that was made for Ubuntu. Avoid ever using debian .deb's or using alien to convert package meant for other distros (ie, .rpm's, debian .deb's, etc).

3. If the program you want is not in the repos and you cannot find an Ubuntu .deb package, you may compile the program yourself. Youmight need to install build-essential to enable you to compile.

4. Finally, if the above is no help. Try to find a different program that will suit your tasks and then search the repos or for a Ubuntu .deb package.

I always recommend the above order because those are the recommended steps. I have been using Ubuntu since Warty and have never had problems. It's when you start using other distro's packages or converting .rpm's that you can start having problems.

---

