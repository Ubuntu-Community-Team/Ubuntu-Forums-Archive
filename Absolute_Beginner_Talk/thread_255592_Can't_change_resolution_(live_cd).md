---
title: "Can't change resolution (live cd)"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Bushfire on 2006-09-11
Hi there. I have a copy of an Ubuntu 5.04 live cd. It runs fine apart from the fact that it only runs at a resolution of 640*480 @ 60hz. I've done a search but I can't really find any answers.

Thanks for any replies,
-Bernard.

---

### Post by StickyStyle on 2006-09-11
Any reason for not using the Ubuntu 6.06 live cd? 5.04 is a little over two years old.

---

### Post by Bushfire on 2006-09-11
> **StickyStyle said:**
> Any reason for not using the Ubuntu 6.06 live cd? 5.04 is a little over two years old.
Because I don't have a copy of it. I'm just checking out Linux, not for this computer, as it is not my own. When I get my own, and if I decide to use Linux, then I would get the latest version. I had 5.04 from a pc magazine cover disc; I didn't order it (or download it.)

---

### Post by Bushfire on 2006-09-12
Alright. I've been doing some snooping, and most solutions seem to require the editing of korg.conf, which I assume is the configuration for the entire system. I also assume that I can not edit it from the live CD, therefore I can not change the resolution without installing ubuntu. Am I correct?

---

### Post by StickyStyle on 2006-09-12
> **Bushfire said:**
> Alright. I've been doing some snooping, and most solutions seem to require the editing of korg.conf, which I assume is the configuration for the entire system. I also assume that I can not edit it from the live CD, therefore I can not change the resolution without installing ubuntu. Am I correct?

I assume you mean the xorg.conf? Yes, that file would contain all the valid display resolutions for the detected video card.  Once you are in running on the livecd though you should be able change the resolution for that session in the System -> Preferences ->  Screen Resolution.  Although if i understand you correctly, 640x480 may be the only one listed to select.  

Do you know what kind of video card is in the computer? You can find out by opening a terminal and typing ```
lspci
``` at the '$' prompt. 

Also to answer your question about editing on the livecd.  Yes you can edit the xorg.conf file once the livecd has booted as the file system is loaded in memory, although you would lose your changes after a reboot.  So you could edit the file, and then restart the xserver (not a full reboot) with Ctrl-Alt-Backspace

I whole heartedly recommend that you get 6.06, a lot has changed since 5.04 and I wouldn't want anybody to get discouraged trying to use an older version.  you can even have the cd shipped to your home at no charge at [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Bushfire on 2006-09-12
Yeah, it's the only one listed. And you can edit xorg.conf? When I brought it up, I couldn't actually write anything, and I assumed that was because it was on the cd. I can't check out the lspci thing at the moment, but it's an integrated intel graphics card (piece of crap). And I probably will get it shipped, 'cause you can't beat the price!

EDIT:

However, what do you think about waiting until 6.10 is released 'til I order?

---

### Post by Bushfire on 2006-09-13
Okay, I don't know what's wrong with it. xorg.conf lists the other resolutions, but I can't edit it anyway.

---

### Post by StickyStyle on 2006-09-13
Are you trying to edit the xorg.conf file as your normal user?  You need root priv's to be able to edit it even in the live cd.  
Run this command at the command line.
```
gksudo gedit /etc/X11/xorg.conf
```

The gksudo is a pretty graphic version of the 'sudo' which will cause your user to switch to root privileges for the duration of that running process.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

And gedit is simply the default text editor for gnome.

[QUOTE] However, what do you think about waiting until 6.10 is released 'til I order?[/QUTOE]
Excellent point, edgy is slated to be released Oct 26th ([https://wiki.ubuntu.com/EdgyReleaseSchedule](https://wiki.ubuntu.com/EdgyReleaseSchedule)) and is supposed to include all kinds of nice enhancements.  Although I would just say get the current 6.06 cd; 6.06 will have much larger user base still after the release of 6.10 with 6.06 being the  long term support version. Also you will find more people able to help you with the versions of software released in 6.06 (because of the larger base) which is an important quality for someone being new to linux.

---

### Post by Bushfire on 2006-09-13
I've tried the gksudo thing before. All that comes up is a blank gedit document named xorg.conf (I typed it out letter for letter)

(Cheers for all the help, by the way! :) )

---

### Post by Bushfire on 2006-09-15
It's okay, I managed to fix it.

All I had to do was change the (correct) i810 driver to the (incorrect) vesa driver, which works perfectly.

Thanks for all the help, StickyStyle.

---

### Post by Najand on 2006-09-15
Can you use 
```

sudo dpkg-reconfigure xserver-xorg

```
and see can it solve your problem or not?

---

### Post by Bushfire on 2006-09-15
> **Najand said:**
> Can you use 
```

sudo dpkg-reconfigure xserver-xorg

```
and see can it solve your problem or not?

Well, like I said in my previous post, I managed to fix it already. But I do remember running that, and crashing the windowing thing and having to reboot.

---

