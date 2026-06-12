---
title: "freezing at desktop loading splash screen"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by stingman777 on 2007-07-21
I'm nearly brand new to Ubuntu/Linux so any suggestions...please dumb down your ideas to ubernoob levels, or at least nearly so.  I'd installed Edgy and clicked around a bit, but that's about it.  I'm now trying to install Feisty on my computer that I've built and not getting very far.

I've gotten it installed fine as far as I can tell...it went through the entire install process and worked great.  I've got it dual-booting Vista Ultimate x64 and Ubuntu 7.04 AMD64.  GRUB is working great, showing both OS's.  I tried loading into Ubuntu though and ran into problems and so far am still not able to do anything with it.  It'll get through the initial Ubuntu splash screen fine and go on to the login screen.  I get a little quirkiness here...when I'm typing my login and/or password sometimes it acts like I'm holding the key down and a letter will repeat itself across the login text box.  I'll have to delete all the extra letters and start typing it again.  As long as I type really slowly, pausing between each letter for a few seconds it doesn't seem to do this.  It's a bit annoying, but no big deal, or at least so I thought.  Once I get the login done it moves on to the tan screen where the desktop usually begins to load along with Nautilus and whatever other applications start then.  Unfortunately it freezes here.  Mouse still works, but I can't do anything else.  The top left quadrant of the screen, nearly a forth of the screen, is just a light gray rectangle.  When I move the cursor into the box it changes to the cursor that I'd expect to appear in a text editing box, but I can't type, and I can't highlight any hidden text.  The small rectangle that appears in the center of the screen that says "Ubuntu" on the right side of it where it shows the icons for programs as they load also appears, but nothing happens.  It just sits there, with nothing loading.  I left it here for several minutes and nothing changed.  Tried restarting a couple of times and the same thing happens.

I can do about anything in Windows, but would like to broaden my horizons and start working with Linux. Unfortunately this is making for a rather rocky start.  If any of your suggestions involve using the command line, please be very specific as I've never had to use it before and won't have any idea what you're talking about.  Thanks for any help in advance!

---

### Post by AceofSpades19 on 2007-07-24
can you log into failsafe gnome?
to do that just go into options(i belive its called) on the login screen and select session and select failsafe gnome and see if that works

---

### Post by stingman777 on 2007-07-25
Nope...got the exact same thing.  Gray box in upper left corner, loading screen in middle with nothing loading.  Any thoughts?

---

### Post by AceofSpades19 on 2007-07-26
can you log into failsafe terminal?

---

### Post by stingman777 on 2007-07-30
yes. I was able to log in to the terminal.

---

### Post by nimajiman on 2007-07-31
Perhaps try booting from a ubuntu live cd (preferably feisty as this is the one you are trying to install), and see whether you get the same problems or not. This should at least tell you whether the problem lies with your install of ubuntu, or if it is a hardware problem. If it is a hardware problem my guess is that you will get the same thing happen from live cd, as your install should be the same.

If the live cd works fine you could try formatting your ubuntu partition and reinstalling - sometimes this just works!

If none of that works, it may be a problem within your xorg.conf, which may explain the funny display issues and the keyboard problems. From your failsafe terminal, you may need to log in (ie just type your username that you specified when you installed ubuntu, press enter, then password and enter, though can't remember if failsafe terminal automatically logs you in as root), then type

sudo dpkg-reconfigure xserver-xorg

This should open up the xserver config screen - follow the instructions as best you can. Often the defaults are best if you are not sure, but you may find a setting that fixes your problem. I am no expert on configuring X however, so cant help much more than that, except to tell you that it is a little risky. My advice would be to backup xorg.conf first (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup), so you can restore the original later from failsafe terminal if necessary (sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf)

Hopefully that will help get you started anyway!

---

