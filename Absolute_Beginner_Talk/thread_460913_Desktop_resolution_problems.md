---
title: "Desktop resolution problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-01
I recently installed Ubuntu 6.10 then updated to 7.04 in order to get my laptop wireless card (broadcom 4318) working with ndiswrapper and with WEP.  In the process, I seem to have messed up something regarding resolutions, in particular what X seems to think the size of the desktop (between the upper and lower lines -sorry, but nub, so don't know what they're called).  X seems to generate a desktop (note this is 1 of the virtual desktops) which is actually larger than the physical area on the screen for it.  The result is not being able to access "OK" boxes on screens, icons being off the screen to the right but no way to scroll to them.  My laptop (Gateway MX3215) uses a S3 video of some sort - i have installed the chrome driver but still no difference.  If it helps in diagnosing the problem, when I go to system/preferences/screen resolution it only comes up with 800x600 or 640x400 with a refresh of 61.  Trying to change the resolution on this screen from the default 800x600 to 640x400 results in an unreadable screen.   What I'd like to be able to do is to be able to the screen to 1024x751 (I think that's it) or 800x600 or 640x400 via the screen resolution box.  I have search through xorg.conf and can't even find an entry with a resolution of only 800x600 or 640x400.

As a nub, but also a retired systems administrator and systems programmer for large scale boxes, I would appreciate any details as to WHY I should make the changes suggested - i.e., what do the changes do?

Thanks;)>

---

### Post by goatflyer on 2007-06-01
boot into revcvery mode, and at the root command prompt type
```

dpkg-reconfigure xserver-xorg

```

Go through all the questions (I know, slow), but pay attention to the questions about the video. try letting it autodetect your graphics adapter.  When you come to the screen asking which resolutions you want, make sure to only enable those resolutions your laptop supports. - gnome will always pick the highest one you enabled.

then reboot.

---

### Post by Sequent on 2007-06-01
The Chrome driver appears to be the correct one but is X actually using it? If it is you can try manually adding an "800x600" option to the screen section of xorg.conf (I've had to take this action just 30 minutes ago to get my nvidia card working). 1024x751 seems an unlikely figure, it's usually even numbers in my experience anyway.

---

### Post by gcos7 on 2007-06-01
Thanks for the replies.  I tried running the config for X and it shows as just a generic video card driver S3 (the only one that looked like I should choose it, but again I'm a newbie at all of this) but that didn't seem to work.  What would I have to do to get it set to the unichrome pro driver as the driver in X (it shows with the device under system/preference/hardware info (device manager).  I have no idea how/where drivers are stored in Linux.  Is that enough information for you to give me more help?

Thanks!

---

### Post by gcos7 on 2007-06-02
Okay, let's try this again.  When I boot using the live CD, my screen is set as default monitor, default depth 24, with a device of vesa.  At that point, I am running a higher resolution than I am once I have installed from the same disk.  I used package manager and installed the unichrome pro stuff that showed, but if I put "via" in xorg.conf , X won't boot.  I have to boot up using the command line option instead of the graphical boot, then copy the old conf over the top of the file I edited (using sudo cp).  Then it boots again, but again the desktop area is larger than the physical screen, so I can't get to everything on the desktop.  Since my laptop is a Gateway MX3215, it uses a Gateway Via S3 driver in Windows.  The hardware manager in linux shows it as Via unichrome pro igp, that's why I used package manager to install the unichrome pro stuff.  Now if I try to vesa in xorg.conf, X does not boot again.  I am really stuck here, and I know that as a person new to linux, that there have to MANY people out there with similar problems and no technical expertise in linux.  PLEASE, can someone provide a step by step solution to this with an explanation as to WHY each step is needed?  This type of reply would really help me, and would be beneficial to all the other new users who are not technical people who are trying linux.

THANKS!;)

---

