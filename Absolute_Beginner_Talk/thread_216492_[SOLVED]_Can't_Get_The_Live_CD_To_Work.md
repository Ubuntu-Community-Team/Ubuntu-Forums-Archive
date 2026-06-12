---
title: "[SOLVED] Can't Get The Live CD To Work"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by BigDave708 on 2006-07-15
Ok, here's the situation. I'm trying to install Dapper Drake on a computer. I've put the CD in, booted my PC and selected the 'install or run ubuntu' option. The CD starts loading and then where the desktop should appear, I get a black and white screen that says this:

> Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0

I've tried and successfully installed Ubuntu on another machine using this CD, so I don't think it has anything to do with this CD. The computer I'm trying to install Ubuntu on is currently a Windows XP computer. I fear it may be a hardware problem - it's 4 years old - but XP does run perfectly on it . . . .

Anybody got a clue? :mrgreen:

---

### Post by rockfloyd on 2006-07-15
i had the same problem trying to use the hoary live cd with my laptop, although the dapper live cd works. sometimes certain computers just don't work with the live cd. if you're not able to get it to work, maybe you should try the kubuntu live cd and see if that makes any difference.

---

### Post by skale on 2006-07-15
How much memory does it have?

---

### Post by BigDave708 on 2006-07-16
> **skale said:**
> How much memory does it have?

It has 256MB. It's SDRAM not DDR (not sure if that should make a difference though).

---

### Post by Arisna on 2006-07-16
This likely means that your video card is not supported by the Live CD.  What kind of video card do you have?

---

### Post by BigDave708 on 2006-07-16
> **Arisna said:**
> This likely means that your video card is not supported by the Live CD.  What kind of video card do you have?

A 3dfx Voodoo 3. Quite old, I know 8).

---

### Post by Arisna on 2006-07-18
I suspect you will need to install using the "Alternate" (as opposed to "Desktop" or "Server") Installation CD and possibly reconfigure X11 through dpkg or by tweaking /etc/X11/xorg.conf manually.  I would advise you to ensure that you will have access to the Internet and a graphical environment on another machine, as you will probably need to come back here and/or do other research on the Internet before this gets resolved.

The card is definitely compatible with the Linux kernel.  See this site:

[http://www.linuxquestions.org/hcl/showproduct.php/product/48](http://www.linuxquestions.org/hcl/showproduct.php/product/48)

Also, this thread may be of use to you:

[http://ubuntuforums.org/showthread.php?t=210258](http://ubuntuforums.org/showthread.php?t=210258)

---

### Post by BigDave708 on 2006-07-18
> **Arisna said:**
> I suspect you will need to install using the "Alternate" (as opposed to "Desktop" or "Server") Installation CD and possibly reconfigure X11 through dpkg or by tweaking /etc/X11/xorg.conf manually.  I would advise you to ensure that you will have access to the Internet and a graphical environment on another machine, as you will probably need to come back here and/or do other research on the Internet before this gets resolved.

The card is definitely compatible with the Linux kernel.  See this site:

[http://www.linuxquestions.org/hcl/showproduct.php/product/48](http://www.linuxquestions.org/hcl/showproduct.php/product/48)

Also, this thread may be of use to you:

[http://ubuntuforums.org/showthread.php?t=210258](http://ubuntuforums.org/showthread.php?t=210258)

This is kind of odd - I followed this advice . . . .

> **rockfloyd said:**
> i had the same problem trying to use the hoary live cd with my laptop, although the dapper live cd works. sometimes certain computers just don't work with the live cd. if you're not able to get it to work, maybe you should try the kubuntu live cd and see if that makes any difference.

. . . and surprisingly I got it to boot from a Kubuntu Live CD and then install successfully on the computer.

Now here's problem number two: Once I had installed Kubuntu, I tried to install GNOME on it because I'm not really a huge fan of KDE. I ran 'sudo apt-get install ubuntu-desktop' and it installed GNOME for me, and then rebooted my computer and when it asked me to log in, I tried to select GNOME from the menu, but only KDE was available. I thought that was all I had to do to install GNOME. Am I missing something or is it really yet another problem? ](*,)

---

### Post by Arisna on 2006-07-18
I'm not sure exactly how apt-get handles dependencies, but with aptitude, it is a bit tricky to get ubuntu-desktop and kubuntu-desktop to co-exist.  Basically, it is possible that Gnome did not actually get installed, or that some config did not get installed.  That said, the following may be helpful:

```
sudo aptitude install gnome
```

Also try installing gdm that way if the above does not help.

You may have to remove the kubuntu-desktop meta-package, but that should be okay because that will not remove KDE and it is not your preferred environment anyway.

---

