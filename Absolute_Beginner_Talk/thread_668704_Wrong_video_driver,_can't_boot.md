---
title: "Wrong video driver, can't boot"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by RobN on 2008-01-15
I'm stuck. I have a laptop with an nVidia GEforce4 go card. The initial, fresh install of ubuntu gutsy gibbon worked okay, but I couldn't turn on any of the desktop effect (and I so loved those wobbly windows from feisty fawn) -- when I try to switch to standard or enhanced mode, it says it can't do it and switches me back. So I tried switching video drivers, and restarted. Oops.

Now ubuntu won't boot -- I get a corrupted video screen, where you can't see or do anything. If I boot it to "safe" mode, I get a command prompt, with no idea how to tell it to switch back to the old driver.

So...what do I do now? Short of reinstalling ubuntu from scratch, which is an option I suppose, how can I tell it to switch back to the old video driver? And once I'm there...any idea how to get it to let me turn on those desktop effects again?

---

### Post by Omnios on 2008-01-15
k from recovery mode or text mode try the following command. 

 Sudo dpkg-reconfigure xserver.xorg

 this will launch a turtle likes graphics screen for setting up the keyboard, mouse and video. Just use the standard stuff for the keyboard and monitor. When you get to the vid you can shoose the driver.

 Another option is to boot into recover or text mod and use 
sudo nano  /etc/X11/xorg.config  

This is a shell text editor.

 Go to the driver option and input nv or nvidia pertaining to what driver you had. nv is the driver that it installs with.

---

### Post by joruz on 2008-01-18
I had similar problems with xserver, after trying to configure ati fglrx. xserver did not want to start. After a lot of dpkg-reconfigure 's, I thought of just putting back the old (prior to the fglrx configuration) xorg.conf file. 

```
mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

You may want to make a backup of the current xorg.conf first.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backupfirst
```

This worked for me. Back in bizniz

---

### Post by sjd on 2008-01-18
SOLVED:  By installing Nvidia driver through the system/admin/restricted drivers manager after logging in using the option ?safe mode (whatever is the Ubuntu alternative available through the lower left "options" menu at login screen.


I have a similar problem and, unfortunately, my son the Linux guru is OOT and unreachable.

I am thinking restoring the old xorg.conf file (making a copy of the current one first, might be an answer).  However, I can only login as my daughter (with limited access/menu options) right now and am not sure how to do it for my config.

Details of what happened:

Trying to get screen resolution to work better for new wide screen monitor, went into system/administration/screen ?something and changed the driver -  I had previously installed the proprietary driver downloaded from Nvidia and all was good (but the letters looked a little squished compared to my daughter's screen) - anyway it showed Nvidia Rav? TNT something, something, something and I changed it to Nvidia FX (generic) - I have an Nvidia FX 5700.  Got the must logoff to get changes to take affect.

Logged off - screen went totally wacky.  Waited about five minutes and turned computer off (power button)

Rebooted into same kernel/restricted (?maintenance) mode - got the enter root pwd, did.  Got the $ prompt.  Didn't have a clue what to do.  Turned off machine, restarted in normal mode.  When I enter my normal ID/Password just keeps looping back to the sign on screen.

Signed on as my daughter - looks normal (for her)

In etc/x11/ there are multiple xorg.conf files with the last on ending in 9 and having today's date and about the same time that I messed things up.

But, I am signed in as my daughter and am wondering if the same xorg.conf file is used for both of us and/or how I would restore the xorg.conf file to my 'settings' area, if not.

Thanks for any assistance.

---

### Post by spiderbatdad on 2008-01-18
> **sjd said:**
> I have a similar problem and, unfortunately, my son the Linux guru is OOT and unreachable.

I am thinking restoring the old xorg.conf file (making a copy of the current one first, might be an answer).  However, I can only login as my daughter (with limited access/menu options) right now and am not sure how to do it for my config.

Details of what happened:

Trying to get screen resolution to work better for new wide screen monitor, went into system/administration/screen ?something and changed the driver -  I had previously installed the proprietary driver downloaded from Nvidia and all was good (but the letters looked a little squished compared to my daughter's screen) - anyway it showed Nvidia Rav? TNT something, something, something and I changed it to Nvidia FX (generic) - I have an Nvidia FX 5700.  Got the must logoff to get changes to take affect.

Logged off - screen went totally wacky.  Waited about five minutes and turned computer off (power button)

Rebooted into same kernel/restricted (?maintenance) mode - got the enter root pwd, did.  Got the $ prompt.  Didn't have a clue what to do.  Turned off machine, restarted in normal mode.  When I enter my normal ID/Password just keeps looping back to the sign on screen.

Signed on as my daughter - looks normal (for her)

In etc/x11/ there are multiple xorg.conf files with the last on ending in 9 and having today's date and about the same time that I messed things up.

But, I am signed in as my daughter and am wondering if the same xorg.conf file is used for both of us and/or how I would restore the xorg.conf file to my 'settings' area, if not.

Thanks for any assistance.

You could reconfigure xesrver or copy an xorg.conf(#) that you think works well. The one thats gets used is the one without any further tag: /etc/X11/xorg.conf
However, you can not do anything without su privileges.

---

