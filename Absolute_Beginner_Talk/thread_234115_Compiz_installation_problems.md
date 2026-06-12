---
title: "Compiz installation problems"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Betta on 2006-08-11
Hello, I am trying to install compiz, however, in the Synaptic Package manager, it says that I need a libsvg-cairo >= 1.6.0. I have libsvg-cairo, but it is only 1.5.0, and all googling suggests that this is the latest version. Help?

-Betta

---

### Post by em3raldxiii on 2006-08-11
Hi Betta, I figured I'd come by and see if I can be of assistnace.  I have Compriz installed, and using Synaptic to check my libsvg-cairo version, it says I have **0.1.6-0ubuntu1**.

If installing compriz with Synaptic (or apt-get) doesn't automatically install **libsvg-cairo** for you, then you should be able to install it separately with this:

start your favorite terminal applications (Applications > Accessories > Terminal) and type this:

```
sudo apt-get install libsvg-cairo

```

Alternatively, you could search for **libsvg-cairo** in Synaptic Package Manager.

If you still don't get 0.1.6, then you may need to update your repositories.  If this is the case, you could search for a thread about repositories, or you could ask here.

PS.  What version of Ubuntu are you using?  6.06 or 5.10?

---

### Post by Betta on 2006-08-11
I am using the latest version of Ubuntu, I will an apt-get install, and hope that it works. 

EDIT: I tried installing it over the apt-get program, and it installed 1.5.0, how do I get an updated repisitory that will contain the correct version?

-Betta

---

### Post by em3raldxiii on 2006-08-11
If you are using the latest Ubuntu, then you have "Dapper Drake" :D

Try reading this thread, it should help you out.  I'm not sure what skill-level you are at, so if you have any questions, please don't hesitate to ask!

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

Once you have updated your sources.list (repositories), you should be able to get the latest version.  It seems to me that it may be the "development" version of the file because compriz is also very much beta.  Good luck!! (and welcome to the forums).

---

### Post by Betta on 2006-08-11
The post says those repositories aren't for AMD64 architecture, which is what I'm using. Also, I am trying to install compiz under KDE, so you could call my installation Kubuntu, though I installed KDE after I installed Ubuntu. Thanks for all the help so far, I really appreciate it.

Edit: Hooray, I googled the package I need for awhile and finally found it on a site (5 others that I visted didn't have correct links). I have the latest compriz version. I'd like to leave this thread open in case I need more help, thanks!

EDIT 2: I'm already having trouble. This is the guide I am following:
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

I am using Method B since I have the KDE environment, when I restart GDM, it goes to command line and I do not see anything about "Selecting compiz".

-Betta

---

