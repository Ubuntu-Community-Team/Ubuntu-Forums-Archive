---
title: "[LXLE] desktop glitches I'd prefer to tidy up &#8210;but how?"
date: 2014-01-21
forum: Any Other OS
---

### Post by engine on 2014-01-21
After a (very recent) reasonably successful install of something called LXLE 12.04.3 from a cover CD, I decided to get up to date; I went from 12.04 to 13.04 and then to 13.10

I don't know the terminology for this new-to-me desktop, but I think I can explain a few questions I still have:
[LIST]
[*]the Mac-like launch bar to the left of the screen started off with placeholders for apps that were present in 12.04.3 but absent in the two 13.x &#8210; I've managed to delete the placeholders, but the launch bar itself doesn't resize. Should it?
[*]in the Start-menu equivalent, the commands Terminal, Run and Search do nothing &#8210; how do I attach commands, and which commands should they be?
[*]the taskbar (bottom left) has two occurrences of Gnome Commander and two non-functional placeholders &#8210; how do I edit and tidy up this area?
[*]the "system tray" equivalent (bottom right) has three non-functional placeholders &#8210;  how do I edit and tidy up this area?
[/LIST]

Thanks in advance for hints and tips.

---

### Post by Frogs Hair on 2014-01-21
If you installed LXDE on Ubuntu 12.04 and upgraded the base Ubuntu installation will upgrade. Ubuntu + LXDE doesn't equal Lubuntu. If you installed the LXDE session you have to select it at login. I'm guessing the bar on the left is Unity which is part of the default Ubuntu desktop.

---

### Post by ajgreeny on 2014-01-21
Your problem may be caused by the fact that LXLE is not exactly the same thing as Lubuntu 12.04; it is a separate distro not officially part of the canonical family, though it is based on Lubuntu 12.04.

Lubuntu 12.04 has now lost support, of course, as it was not an LTS version like Ubuntu, Kubuntu or Xubuntu 12.04.  All the extras included in LXLE have probably now become totally confused by your distro upgrade, and all the ppa repos that LXLE uses for those extra applications will have been disabled, so I think you may find it difficult to overcome your problems in any simple way.

---

### Post by vasa1 on 2014-01-21
There's a thread on LXLE here [http://ubuntuforums.org/showthread.php?t=2125764&p=12558221#post12558221](http://ubuntuforums.org/showthread.php?t=2125764&p=12558221#post12558221) . The developer of that distro monitors that thread in case you wish to ask about LXLE.

---

### Post by QIII on 2014-01-21
Since this is likely distro specific and not equally applicable to all distros, moved to Other OS/Distro Support.

---

### Post by engine on 2014-01-23
> **ajgreeny said:**
> Your problem may be caused by the fact that LXLE is not exactly the same thing as Lubuntu (&#8230;)
That explains a lot about how I see things: I hadn't realised that LXLE is a "respin of Lubuntu". (that's the description on the LXLE site)

Still an'all, the last thing I remember doing is installing Lubuntu; and when I check Operating system - system information, I don't see any mention of LXLE. Am I still missing something?

```
-Version-
Kernel: Linux 3.11.0-15-generic (i686)
Compiled: #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013
C Library: Unknown
Default C Compiler: Unknown
Distribution: Ubuntu 13.10
-Current Session-
Computer Name: {computer Name}
User Name: {userName}
Home Directory: /home/ngn
Desktop Environment: LXDE (Lubuntu)
```

---

### Post by ajgreeny on 2014-01-23
When you boot and see the screen with Lubuntu and the animated coloured dots beneath, you may also see in smaller letters the lxle name, in blue/green, if I remember correctly.  That will show you it is actually LXLE and not straight Lubuntu.  If you look in software-sources you will also see lots of ppa repositories in the Other software tab.

---

### Post by engine on 2014-02-15
I'm marking this thread as solved. It isn't, exactly, but I'm now on "pure" out of the box Lubuntu &#8210; so I'll start a new round of questions :-}

Kernel		: Linux 3.11.0-15-generic (i686)
Compiled		: #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014
Distribution		: Ubuntu 13.10
Desktop Environment		: LXDE (Lubuntu)

---

### Post by ronniew on 2014-02-16
They nailed it BTW, to be honest I didn't figure that anyone would want to upgrade the distro to the next version simply because they were using for better support on an older machine. I tend to discourage the practice since support for aging hardware tends to be dropped from release to release. They are also right about support. Try to post them in the lxle forums which you can find on the homepage.

---

