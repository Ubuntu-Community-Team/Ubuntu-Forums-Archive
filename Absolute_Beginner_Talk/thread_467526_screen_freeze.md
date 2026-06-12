---
title: "screen freeze"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by patpacman1214 on 2007-06-07
i have been trying to install ubuntu on my new system. i go through the loading screen, but when it gets to the orange screen where the mouse curser pops up, it freezes. anyone have any idea whats going on?

---

### Post by dbbolton on 2007-06-07
> **patpacman1214 said:**
> i have been trying to install ubuntu on my new system. i go through the loading screen, but when it gets to the orange screen where the mouse curser pops up, it freezes. anyone have any idea whats going on?
did you check the md5sum on the ISO before burning it and/or select "check CD for errors" from the menu?

---

### Post by wulf29 on 2007-06-07
I'm having the same issues as patpacman1214.  During the installation from the LiveCD I get past the splash screen and then freeze at desktop.  Only an orange desktop is shown.  The mouse works for about 5 seconds and then it freezes.

I have done an md5sum of my iso's (this happens with both Fiesty and Dapper) and both come out perfect.  I've also tested the disc, which reports no errors.  In an effort to eliminate the LiveCD issue, I tried the alternateCD for Dapper which installed fine.  But on the first boot it hung at the same point.

The crazy part is that I had this issue two nights ago and found a fix for it.   by adding noacpi noapci nolapic to the boot options it made it into the desktop.  But there was a fourth option that I put in and, for the life of me, I can no longer find the post where I found the fix.  Btw, I decided to try to go backwards to Dapper Drake in hopes of better compatibility with Cedega.

I have also tried xforcevesa thinking that might have been the fourth option, but still get the same results.

My system currently consists of:
AMD 64
Gigabyte K8Triton Mobo
1 gig ram (passed memtest)
nVidia 6600 graphics card
Sound Blaster Audigy Platinum
Edit:  Also a 250gig SATA drive

---

### Post by patpacman1214 on 2007-06-07
let me know if you remember what the fourth thing was. i will try the noacpi noapci nolapci and see if that helps.

my system is 
ati rage 2c
500 gig sata
amd 64 dual core
asus m2n32
the video card is only temporary

---

### Post by dbbolton on 2007-06-08
did you try the alternate install cd?

---

### Post by patpacman1214 on 2007-06-08
downloading it now.

---

### Post by wulf29 on 2007-06-08
It's really bugging me that I can not figure this out.  I had it up and running night before last and messsing with it last night.. but just HAD to try going back to Dapper this morning.  

Does anyone know if there a list of available boot options that I might peruse to find the fourth option?

---

### Post by patpacman1214 on 2007-06-08
alternate cd works so far. its installing the base program right now. im not sure why it didnt load the desktop, then works fine with this cd, but whatever, im happy.

---

### Post by patpacman1214 on 2007-06-08
nvm, i get to the username sreen and now its freezing there.

---

### Post by wulf29 on 2007-06-08
Same here.

Username:

Frozen

Edit:  I can get into Ubuntu by booting into Recovery mode and then typing gdm at the prompt.  Doing this popped up a window for me saying "Internal Error  failed to initialize HAL!"

---

### Post by patpacman1214 on 2007-06-08
yea same here. thanks for the gdm. im on right now and so far hasn't frozen,but it makes me wonder how important HAL is.

---

### Post by wulf29 on 2007-06-08
Apparently it's pretty important unless you don't want to add any other devices to the computer. :)

---

### Post by dbbolton on 2007-06-08
> **patpacman1214 said:**
> alternate cd works so far. its installing the base program right now. im not sure why it didnt load the desktop, then works fine with this cd, but whatever, im happy.
the alternate CD is text-only.


you can always double check your xorg.conf :
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by patpacman1214 on 2007-06-08
so what are we supposed to do about it then? the error log says "creating directory"/var/run/cups/certs"

---

### Post by wulf29 on 2007-06-08
Still trying to resolve this issue.  After finding a suggestion on another forum, I inputed:

> /usr/sbin/hald --daemon=no --verbose=yes

at the tail end of the resulting spam was this:

> 12:08:53.654 [I] blockdev.c:353: entering; exit_type=0, return_code=0
12:08:53.659 [I] blockdev.c:125: Add callouts completed udi=/org/freedesktop/Hal/devices/volume_uuid_bce1dba1_da63_4545_b1f5_68ccb3e76692
12:08:53.659 [I] hald.c:106: Added device to GDL; udi=/org/freedesktop/Hal/devices/volume_uuid_bce1dba1_da63_4545_b1f5_68ccb3e76692
12:08:53.659 [I] acpi.c:1225: acpi_add: acpi_path=/proc/acpi/processor/CPU0 acpi_type=1, parent=0x00000000
12:08:53.667 [I] acpi.c:1197: Add callouts completed udi=/org/freedesktop/Hal/devices/acpi_CPU0
12:08:53.668 [I] hald.c:106: Added device to GDL; udi=/org/freedesktop/Hal/devices/acpi_CPU0
12:08:53.668 [I] hald.c:619: Device probing completed
12:08:53.668 [I] hald_dbus.c:4074: entering
12:08:53.668 [E] hald_dbus.c:4081: dbus_bus_get(): Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Sent kill to 4695
Sent kill to 4673
Sent kill to 4681
/usr/lib/hal/hald-addon-acpi exited
/usr/lib/hal/hald-addon-storage exited
/usr/lib/hal/hald-addon-keyboard exited

If anyone can decipher this for me and get back to me, this would be great.  For my untrained eye, it almost looks like a possible acpi issue.  Which is odd since I stated earlier that using noacpi did not work in the boot up process.  I'll dig into the hald_dbus.c file and see just what's going on around line 4081.  Thanks in advance.

Edit:  correction, I won't look at hald_dbus.c since it's already compiled.

---

### Post by dbbolton on 2007-06-08
> **wulf29 said:**
> Still trying to resolve this issue.  After finding a suggestion on another forum, I inputed:



at the tail end of the resulting spam was this:



If anyone can decipher this for me and get back to me, this would be great.  For my untrained eye, it almost looks like a possible acpi issue.  Which is odd since I stated earlier that using noacpi did not work in the boot up process.  I'll dig into the hald_dbus.c file and see just what's going on around line 4081.  Thanks in advance.

Edit:  correction, I won't look at hald_dbus.c since it's already compiled.
first of all, how is that spam?

second question- are you still working with the liveCD, or did you install ubuntu to your hard drive?

---

### Post by wulf29 on 2007-06-08
There was much more scrolling than what I posted.  For sake of ease to read I only posted the last part before hald stopped.

I have it installed via the alternate disc, but if I boot up in normal mode it hangs at the same spot the LiveCD does.  I have to boot up into Recovery Mode and then type gdm in the prompt in order to get in.

I'm working with Terminal right now to get enough history to post a .txt file with all the scroll.

---

### Post by wulf29 on 2007-06-08
Here is a link to my log file of the hald.

[http://webpages.charter.net/cravenm/hald_log.txt](http://webpages.charter.net/cravenm/hald_log.txt)

---

### Post by DREMA on 2007-07-30
Just update your the BIOS of your motherboard (M2N32-SLI Deluxe)

---

### Post by Cheese Roller on 2007-07-30
When I installed Ubuntu, I couldn't use the latest version.

I had to use Edgy and upgrade from there. Feisty wouldn't work at first.

---

