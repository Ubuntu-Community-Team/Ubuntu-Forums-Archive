---
title: "how can i convert ubuntu to kubuntu kde4 ?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by DO55 on 2008-01-16
how can i convert ubuntu to kubuntu kde4 ?

---

### Post by thelatinist on 2008-01-16
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
```

Then follow the instructions at [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php) for installing KDE 4.0.

Please note that this will not uninstall all the gnome applications Ubuntu installs by default.  I suggest Add-Remove for that.  Also, this will not actually remove Gnome from your system. You will still have the option to boot into a Gnome session from the login screen.

Have you tried out KDE 4.0 yet?  Please be aware that KDE 4.0, even in its release version, does not contain some functionality you might take for granted (such as the ability to resize panels).  Lots of things in 4.0 are still in progress.

---

### Post by .nedberg on 2008-01-16
I would recomend the LiveCD from [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

KDE4 lacks a lot of stuff atm, but it will bee great I am sure!

---

### Post by jaytek13 on 2008-01-16
> **thelatinist said:**
> ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
```

Then follow the instructions at [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php) for installing KDE 4.0.

Please note that this will not uninstall all the gnome applications Ubuntu installs by default.  I suggest Add-Remove for that.  Also, this will not actually remove Gnome from your system. You will still have the option to boot into a Gnome session from the login screen.

Have you tried out KDE 4.0 yet?  Please be aware that KDE 4.0, even in its release version, does not contain some functionality you might take for granted (such as the ability to resize panels).  Lots of things in 4.0 are still in progress.


I don't believe all that is necessary, actually. The instructions in the announcment on kubuntu's website are directed at those who were beta testing kde4 and so it begins with telling you how to remove those beta files... I would assume he wasn't beta testing it, but the directions don't hurt to follow, anyways.

But, ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
``` shouldn't be necessary at all. Following these instructions, it will first install kde3, and then he will proceed to kde4. The 2 are not dependent. 

Also, for the OP, keep in mind that this is simply a release of kde4. It is not optimized or made for Kubuntu and won't be for a while. You are simply installing the kde4 files.

In the end, all that is necessary is to ```
sudo apt-get install kde4-core
```... after adding the source repository from the announcement linked. And yes, I would recommend keeping gnome around. You might find you don't care for kde4 and it's incompleteness at the moment (I did).

---

### Post by thelatinist on 2008-01-16
> **jaytek13 said:**
> But, ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
``` shouldn't be necessary at all. Following these instructions, it will first install kde3, and then he will proceed to kde4. The 2 are not dependent.

The OP did not say only that he wanted to install KDE4 on his Ubuntu system, he said that he wanted Kubuntu *with* KDE4.  I assume this means he would like all of Kubuntu's default applications and customizations, not just KDE4.  To get Kubuntu, he has to do what I suggested.

---

### Post by SOULRiDER on 2008-01-16
Mind you that although KDE4 has been released is still buggy and installing it can actually cause lots of trouble.. juts look at how many people are posting aobut KDE4 breaking their systems. If you just wanna try it out, i suggest you get a KDE4 live CD and leave your poor Ubuntu installation alone.

---

### Post by thelatinist on 2008-01-16
> **SOULRiDER said:**
> Mind you that although KDE4 has been released is still buggy and installing it can actually cause lots of trouble.. juts look at how many people are posting aobut KDE4 breaking their systems. If you just wanna try it out, i suggest you get a KDE4 live CD and leave your poor Ubuntu installation alone.

I agree.  I keep a separate partition just for testing such things.  KDE4 looks promising, but it's not ready to replace Gnome on my computer yet.

---

### Post by DO55 on 2008-01-19
thanks all for help 

im using kubuntu with virtualbox
looks good

---

### Post by EXCiD3 on 2008-01-19
KDE 4.1 is the release intended to replace KDE 3.5.6, KDE 4.0 has LOTS of missing functionality. I'm going to stick with gnome for a while too.

---

