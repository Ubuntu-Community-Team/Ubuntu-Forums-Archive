---
title: "fglrx issue after kernel upgrade"
date: 2008-12-20
forum: Apple Hardware Users
---

### Post by AlainJLEB on 2008-12-20
Once more, after an upgrade of kernel, the fglrx module does not work anymore. I have tried to remove the xorg-driver-fglrx package, and then install the xorg-driver-fglrx and the amdcccle one, followed by an aticonfig --initial ... but it still does not work. 

I'm using an iMac 24 with an ATI 9600 card. And everytime Ubuntu performs upgrades of kernel &/or header files, I have the same issue

I see during the boot a message about an issue with DKMS related to the fglrx module, but can't find that message in log files.

Question: how to solve this? What are the packages to install ?

---

### Post by AlainJLEB on 2008-12-22
Despite removing and reinstalling modules and fglrx, it still does not work ... so let's go for (I hope) a very basic question: how can I remove/reinstall completely X in order to recover ?

---

### Post by cyberdork33 on 2008-12-22
It is failing to "compile" for some reason. That is the issue. boot up to your older kernel and it will work fine. 

Check the bug reports on launchpad as your are likely not the only fglrx user that had this problem.

---

### Post by AlainJLEB on 2008-12-30
> **cyberdork33 said:**
> It is failing to "compile" for some reason. That is the issue. boot up to your older kernel and it will work fine. 

Check the bug reports on launchpad as your are likely not the only fglrx user that had this problem.
Well, I can't find the bug report on launchpad ... do you have the ID?

---

### Post by cyberdork33 on 2008-12-30
> **AlainJLEB said:**
> Well, I can't find the bug report on launchpad ... do you have the ID?
no, i don't know if there even is one.

Have you tried getting newer updates again as if there was a problem it is likely fixed by now.

---

### Post by AlainJLEB on 2009-01-01
Yes, I have looked for update but nothing related so far. Would it help to completely remove and reinstall Xorg? If yes, what's the best way to do it so that "it" detects correctly the right driver to use ?

---

### Post by cyberdork33 on 2009-01-02
> **AlainJLEB said:**
> Yes, I have looked for update but nothing related so far. Would it help to completely remove and reinstall Xorg? If yes, what's the best way to do it so that "it" detects correctly the right driver to use ?

no. Attempting to remove xorg will uninstall several other packages as well.

If you want xorg to reconfigure itself, just run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by AlainJLEB on 2009-01-03
> **cyberdork33 said:**
> 
If you want xorg to reconfigure itself, just run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Will this behave the same way as if I was running the LiveCD for an installation? I mean will this auto-detect the right server to use?

---

### Post by cyberdork33 on 2009-01-05
> **AlainJLEB said:**
> Will this behave the same way as if I was running the LiveCD for an installation? I mean will this auto-detect the right server to use?
yes. It will not choose to use a proprietary driver though.

If you are concerned, just backup your xorg.conf file first.

---

