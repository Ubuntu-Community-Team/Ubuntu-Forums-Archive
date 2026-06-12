---
title: "Empty xorg.conf file; what to do?"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by mfox on 2008-05-25
I have a newly installed Hardy running as a dual boot on my PowerBook G4 Al.  For the most part, everything is working well (including my wireless connection), but I'm having four problems with settings that I would expect require some editing of the xorg.conf file:
- funny colours on the Ubuntu splash screen at startup
- horizontal lines at shutdown
- can't get trackpad tap to stick between startups
- can't configure MOL - I get horizontal lines and a freeze when I try

Problem is that there doesn't appear to be an xorg.conf file in my file system; at least I can't find one.  Under /etc/x11/ there is a file there now, but it's totally empty.  Should I just put commands in that empty file (with gedit), or might there be the proper file for it somewhere I can't access, owned by Root?

---

### Post by sisco311 on 2008-05-25
Try to open the file with this command (from a terminal):
```
gksu gedit /etc/X11/xorg.conf
```
If it's still empty try to generate a new file:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by stream303 on 2008-05-25
Hardy's xorg.conf looks pretty bare everywhere now with the new xorg 7.3 server. :) Unfortunately, the old standby of doing a dpkg-reconfigure no longer takes into account your video card setup - you either have to accept the defaults, or manually modify your /etc/X11/xorg.conf.  Kind of a retro-thing if you ask me. :)

If that is a PPC machine, you could try passing the *nosplash* kernel parameter at the second-stage yaboot prompt and make it permanent later in yaboot.conf with a ybin.

---

### Post by ssam on 2008-05-26
the splash screen is before X is started, so no amount of xorg.conf is going to help. the odd strange colours at boot, shutdown, and suspend are something you may have to live with.

for the tap stuff, you could try putting the command in /etc/rc.local . that get run at startup.

---

### Post by mfox on 2008-05-26
Thanks everyone.  I don't know how to explain this, but when I checked my xorg.conf file last night, there was something in it.  I did find a trackpad entry and added to it.  When I restarted it, the tap was enabled, but I haven't tried starting after a shutdown yet.

I can live with the odd colours at startup and the horizontal lines at shutdown, but I will try the nosplash command at startup and see how that works.

Despite a lot of fiddling around, I haven't yet been able to get MOL to work.  I'm hoping there is a fix or a workaround for that, as I would want to have access to the Mac side while Ubuntu is operating.  Speaking of which, is there any way besides MOL to at least be able to read and write to the Mac side while Ubuntu is operating.  That's the nice thing about running it on an Intel Mac with Parallels or VMware.

---

### Post by Brightbelt on 2008-05-26
Just to put in my two cents worth, I get those horizontal lines at shut down all the time (on Macs and PCs that run Ubuntu). I have long since accepted that it's part of Ubuntu's structure somehow.

It may be simplistic, but my way of thinking about it is that since my hardware does not perfectly match Ubuntu (hence the workarounds we have to do etc), there are going to be 'holes' so to speak in the Ubuntu system install.

Just a thought,...Frank B.

---

### Post by stream303 on 2008-05-26
Which powerbook are you running?
[http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html](http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html)

Depending on what video card you are using, we might be able to get some cleaner startup and shutdowns for you, even though xorg.conf seems to work by editing yaboot.conf or passing kernel parameters..

---

### Post by mfox on 2008-05-26
My PowerBook is a G4/1.33 Al with a 15" display (model #M9422LL/A).  The video card is the ATI mobility Radeon 9700, with 64mb RAM.  That would be great if there is anything you can do to improve the startup and shutdown experience, and I'm happy to try out any ideas you have.  I'm already pleasantly surprised by how well Hardy works on this PowerBook, given how recently Hardy came out.  Now if I can only get MOL working on it.... :)

---

### Post by stream303 on 2008-05-26
Check out what another G4 radeon user is doing:

[http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974)

In your case, I'd probably try doing the following instead

```
nosplash video=radeonfb:1280x854@60
```

Assuming that the native resolution specs I found for your machine were correct:
[http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html](http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html)

After editing /etc/yaboot.conf, you'd have to make it noticed by the system with

```
sudo ybin -v -C /etc/yaboot.conf
```

You could also test it without messing with yaboot.conf by trying it at the second-stage yaboot boot: prompt when it comes up by hitting -tab- to stop the countdown, and issuing

```
Linux nosplash video=radeonfb:1280x854@60
```

And see how that does before doing a dedicated edit to your yaboot.conf....

---

### Post by mfox on 2008-05-27
Unfortunately, issuing the Linux nosplash ... command at the second boot stage didn't change anything; the weird colour pattern on the word and symbol of Ubuntu was as before.  Does this mean there's no point in editing the yaboot.conf file?

---

### Post by stream303 on 2008-05-27
You'd think so, but in perhaps a dream, I seem to remember somebody saying that it only worked from yaboot.conf.

Any chance for a typo like nospalsh instead of nosplash?

---

