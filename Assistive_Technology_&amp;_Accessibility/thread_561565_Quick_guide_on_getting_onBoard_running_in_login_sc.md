---
title: "Quick guide on getting onBoard running in login screen"
date: 2007-09-27
forum: Assistive Technology &amp; Accessibility
---

### Post by t0rtois3 on 2007-09-27
Add the below to your /etc/apt/sources.list

```

deb     http://ppa.launchpad.net/onboard/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.launchpad.net/onboard/ubuntu feisty main restricted universe multiverse

```

Update and a new version of onBoard will install.  It includes a few fixes and the ability to specify where onBoard will appear on the screen.

To start onBoard in GDM (Ubuntu) insert the below in /etc/gdm/Init/Default just before exit 0, for KDM (Kubuntu) add to the end of /etc/kde3/kdm/Xsetup

```

exec onboard -x 0 -y 470 --size=800x300

```

Note the numbers will depend on your size of screen so play with them until you are happy.

NOTE:
GDM has to run either as "plain" or "plain with face browser".  Configurable in gdmsetup.

For Gutsy users replace all instances of feisty with gutsy

---

### Post by frafu on 2007-09-29
Hello Chris, 

Thanks for making onboard available in a repositry. 

Could you please tell me what repository ppa.ubuntu.com is? It might be interesting to also offer mousetweaks in such a repository, as long as it is not available in any official repository of Ubuntu. 

Further, could you please tell me whether the version that you are offering in that repository includes all the changes you made during August? If that is the case and you don't have any objections, I will modify the documentation that I prepared a few weeks ago to include your new repository. 
[https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM](https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM)

Cheers 

Francesco

---

### Post by t0rtois3 on 2007-09-29
[https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)

Well done on those docs

---

### Post by frafu on 2007-09-29
Thanks for the link. 

Cheers

---

### Post by baosheng on 2008-02-17
Hi, I just found a problem. I have tried to use the line you mentioned in your post, but only an onboard dialog window appeared on my screen, no login window, and the mouse icon was "running". 

So I tried to modify it,
I put an "&" at the end of that line. This time, both login window and onboard were displayed. But, I couldn't input stuff into login window via onboard, though i could see the keys were "pressed down" when I clicked them by mouse.

Can you tell me what should I do?

---

### Post by frafu on 2008-02-18
Hello,

Here is another documentation about a way to start onboard during login: 
[https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

If you use it, onboard does not automatically start, but you have to start it manualy with a gesture after the login screen has appeared. How to do it, is explained in the page referred by the link. Moreover, if you don't need dwelling, you can skip the corresponding parts. 

Cheers

Francesco

---

### Post by baosheng on 2008-02-18
Hi,

I have followed the instructions on that page and it works fine. The information on that page is fairly useful. But still has some tiny problem. I will try to edit it when I have time.

---

### Post by frafu on 2008-02-18
@ baosheng

Thanks for improving it if you have time. 

Francesco

---

