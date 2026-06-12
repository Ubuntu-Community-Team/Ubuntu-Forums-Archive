---
title: "Trying to Install"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by aphouser on 2007-01-31
Hey all,

I've been browsing for some time and have found a few things similar to my situation but nothing that fixes anything yet, so I figured I'd put it to the masses.  =D

I'm trying to install Edgy on a second HD but am having a couple issues.  Issue #1 is what I assume to be a video card issue.  I can boot off the Live CD (burned i386 version) and when the bootup gets to the "Knightrider" effect the display gets a little corrupted (I see multiple progress bars).  After that the video goes to black and my monitor reads "Out of Range."  I can hear the distinctive Ubuntu sound on bootup, but no image.

My first attempt to fix this was to hit Alt + Ctrl + F2 to get into the console and do
--sudo dpkg-reconfigure xserver-xorg
to try and take care of my NVidia driver as I have read about a lot of issues.  When I got to the choice of 24 colors I think it is (I've been searching the forums too long and didn't write it down like I should've) the program freezes.

I also tried simply running in video safe mode and no luck there, same "out of range" on the monitor and same results when I ran the above code. 

Any suggestions/comments/hints would be greatly appreciated.  I'm trying to make the switch full time and attempting to bring the family along, but I've got to prove my machine out first.  

Thanks a million, sorry for the long post.

---

### Post by Wim Sturkenboom on 2007-01-31
Check the file */etc/X11/xorg.conf* and make sure that the values for *VertRefresh* and *HorizSync* in the *monitor* section reflect the capabilities of your monitor (check the manual or on the internet). If not, adjust (you need root permissions for this). This should solve the out-of-range problem.

While at it, you can also check the *driver* in the *device* section. 'vesa' is the safest choice while you're experiencing problems although it might not give you the full potential of the card.

Did you install drivers for the videocard?

Please tell us which monitor and which videocard you have. (make and models)

---

### Post by aphouser on 2007-01-31
Videocard is Nvidia GeForce 6800 GS
Monitor is Viewsonic VA902b

I'll give the couple suggestions you listed a whirl and see what I get.  

I have not installed any drivers as I have not been able to get ubuntu to install yet.

Thanks for the quick response.

---

### Post by Wim Sturkenboom on 2007-01-31
I was not sure if it failed during the install or after the install. Unfortunately I'm not very famailiar with the live-CD and how to change settings.

You can always try *the alternate CD* (which uses a text-based user interface).

---

### Post by AndyCooll on 2007-01-31
Just to get you up and running try the following:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```

At the video card section select "vesa". You should then get a display. It's only a bog standard video card driver, however it works with pretty much everything. 

Of course once you have that up and running you can always play around and try to get your card working with the proper nvidia drivers.

:cool:

---

### Post by batasrki on 2007-02-01
Hi all,
This is my first post. I too have a live version of Ubuntu 6.10 and I have the same problem as the original poster, only my video card is GeForce 6800 XT. I tried out the commands listed here, but was unsuccessful in fixing the problem, since I got error messages stating that xserver is not installed, which would make sense since it runs from the CD. I did fiddle around with the VGA setting on boot and at resolution 1280x1024 32, I got a desktop, but the display was a bit f----d up. 
So, my advice to the original poster is to try out a few different VGA settings on boot. If anyone has any advice as to how to get the display to show properly, I'd be more than grateful.

Thanks

---

### Post by aphouser on 2007-02-10
Thanks to the above, I tried 1024x768x32 and got my display working.  I was without a mouse arrow, though the mouse was working as I could see the highlights on icons.

I used 

```
Option "HWCursor" "Off"
```

and that fixed the mouse pointer issue.  So my big question now is:  What do I put in the Grub loader to keep these settings now that I've got Ubuntu installed.

I'm running a dual boot with Win XP and that's all loading fine.

Any help would be greatly appreciated.  Thanks!

---

