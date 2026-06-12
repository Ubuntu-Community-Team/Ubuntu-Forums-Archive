---
title: "How do I get 1440x900 resolution?"
date: 2006-08-09
forum: Apple PPC Users
---

### Post by conshok26 on 2006-08-09
I'm very very new to linux and I'm having some confusion on what to do.  I'm running ubuntu with parallels on my MacBook Pro.  The largest resolution it shows is 1024x768.  I've tried searching online how to change it and it looks like it's something that needs to be done through the terminal.  Now in OS X I have some experience using terminal and it looks the same but I was wondering if someone could be kind enough to give me a step by step guide on how to have this set up.

Thanks
Andy

---

### Post by psygen on 2006-08-09
my PowerBook G4 I change in xorg.conf:

Section "Device"
  ...
  driver r128
  ...
EndSection

Section "Monitor"
   ...
   HorizSync 28-51
   VertRefresh 43-60
EndSection

Section "Screen"
   ...
   DefaultDepth 24
   ...
EndSection

SubSection "Display"
   Depth 24
   Modes "1152x768"
EndSubSection

You it will be able to try to change Modes until obtaining the resolution that it desires.

---

### Post by conshok26 on 2006-08-09
thanks but how do I get to that point. should i just paste that into the terminal?  I've read to enter in sudo gedit /etc/x11/xorg.conf and it brings up a new window but it's blank.  Like I said I know nothing about linux.

---

### Post by ubusarah on 2006-08-09
I just got 1680x1050 working in Parallels on my new 20" iMac; here's what I did:

1. went to the VM settings pane and added 1680x1050 as a custom resolution

2. went to the terminal and did: 
  sudo dpkg-reconfigure -phigh xserver-xorg
  (I stole this from the comment in /etc/X11/xorg.conf)

3. rebooted ubuntu

And the VM came up in 1680x1050!

Now, a *better* idea might be to try adding the custom resolution BEFORE installing Ubuntu.

I'm still trying to work out how to actually WORK with this resolution; but running in full screen mode it seems rather nice. :-)

BTW I only got the hardware and the software yesterday, so I'm still making it up as I go along...

---

### Post by gwon on 2006-08-09
> **conshok26 said:**
> I'm very very new to linux and I'm having some confusion on what to do.  I'm running ubuntu with parallels on my MacBook Pro.  The largest resolution it shows is 1024x768.  I've tried searching online how to change it and it looks like it's something that needs to be done through the terminal.  Now in OS X I have some experience using terminal and it looks the same but I was wondering if someone could be kind enough to give me a step by step guide on how to have this set up.

Thanks
Andy

I don't have ubuntu running in front of me, so forgive me if I can't describe things in too much detail

Open Terminal
Type "sudo nano /etc/X11/xorg.config"

Find the section about the display, add the resolution you want (just follow the way it's formatted when you see it - it should be pretty obvious).

Save (ctrl+x then yes I think)

restart X (ctrl+alt+backspace)

---

### Post by Isaac Dupree on 2006-08-11
> **conshok26 said:**
> I've read to enter in sudo gedit /etc/x11/xorg.conf and it brings up a new window but it's blank.  Like I said I know nothing about linux.

Linux is case-sensitive and the path is /etc/X11/xorg.conf -- the X in X11 is capitalized (but not the x in xorg.conf). "gedit", "nano" and so forth are names of text editors -- gedit should be fine.

"sudo" allows the command that follows it to make administrative changes that might break your system (if you change things the wrong way). If you are the only user of your system, this is really only a way to reduce the chance of your system breaking by accident (or by possible unknown bugs or security holes in the programs you use) when you're not trying to change it. :)

```
sudo gedit /etc/X11/xorg.conf
```

---

