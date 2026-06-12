---
title: "Wubi Boot Options"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by seandgibbonsy on 2008-04-19
**This post could be related to an Ubuntu bug filed at**: [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I understand that Ubuntu 8.04 is coming with Wubi.  This let's it install like any normal program then you can select which OS to boot when the computer boots up.  My question is, when the boot screen comes up does Wubi automatically select what OS to load after a few seconds and can I set which OS it automatically loads?  My parents and sister still use this computer and they like Windows XP so I don't want them to get mad when it automatically loads Ubuntu or they have to click Launch Windows everytime they want to boot up the computer.  So I want to make Wubi automatically launch Windows (after like 5 seconds) when The power is turned on.

---

### Post by alzie on 2008-04-19
Wubi installs the Grub menu which gives you time to select which OS you want to use.  I can't remember which OS a WUBI install defaults to ( I used WUBI for a time )

Anyway,  If it defaults to Ubuntu and you don't want it to, you just need to change the boot order in Grub.

There is a program in Synaptic Package Manager called "startupmanager" which can change your boot order.   I wish I found it sooner  lol

I hope this helps

---

### Post by seandgibbonsy on 2008-04-19
> **alzie said:**
> Wubi installs the Grub menu which gives you time to select which OS you want to use.  I can't remember which OS a WUBI install defaults to ( I used WUBI for a time )

Anyway,  If it defaults to Ubuntu and you don't want it to, you just need to change the boot order in Grub.

There is a program in Synaptic Package Manager called "startupmanager" which can change your boot order.   I wish I found it sooner  lol

I hope this helps

But how much time does it give you?  And  can you also change how much time it gives you?  I don't want any more than a few seconds.

---

### Post by ACMarina on 2008-04-19
If I remember right, it generally takes 3 seconds to boot unless you try to change it.. I'm sure you can change the time it takes, but I don't know how offhand..

---

### Post by avtolle on 2008-04-19
I just did it; without a stopwatch on it, it seemed to boot (in my case Vista) into Windows (first selection) in under three seconds (manual count).

---

### Post by seamustry on 2008-04-19
Yeah I've tried it and it also picked Vista as default value...

---

### Post by alzie on 2008-04-19
If you decide using startupmanager it will let you set your time.  Otherwise you can go into grub and set it manually.

The other nice thing with Wubi is if you break it can be uninstalled from windows add and remove and reinstalled.  I did that a few times  :lolflag:

---

### Post by harpazo on 2008-04-28
To change the Wubi default boot options from Windows to Ubuntu do this:

"How do I make Ubuntu the default boot option?

Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well."

This is a quote from the official Wubi Guide found here: 

[Wubi Guide]("https://wiki.ubuntu.com/WubiGuide")  

Enjoy ( I am!)
Harpazo

---

