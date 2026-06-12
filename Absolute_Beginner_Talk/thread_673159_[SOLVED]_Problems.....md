---
title: "[SOLVED] Problems...."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-01-20
Ok the Livecd worked fine and installed ok but now when i try and boot ubuntu i get a blank screen...i have had this before with ubuntu gutsy on my last install but didn't have it with the beta versions of gutsy or any other version of ubuntu only since the formal release of ubuntu 7.10 so obviously its somthing they have done since :) im using an ATI Mobility Radeon 9600 M10 graphics card


thanks for any help!

Full list of hardware is here
[http://www.freewebs.com/proproxy/hardware%5Finfo.html](http://www.freewebs.com/proproxy/hardware%5Finfo.html)

---

### Post by mgmiller on 2008-01-20
You could try booting off the live CD and then navigating to the /etc/X11/xorg.conf on the installed hard drive and changing the video driver from ati to vesa.  That shuold at least get you a visible gui desktop on reboot.  You could then try installing the fglrx driver using the restricted drivers manager.  Some ati video cards work well with fglrx, but not at all with ati.  Vesa should work with anything.

---

### Post by Mud.Knee.Havoc on 2008-01-20
Try adding these options at boot: "noapic" and "acpi=off"
Most distros give me trouble if I don't use them.

---

### Post by kamitsukai on 2008-01-20
ok but how would i "navigate" im a complete newb :P and how would i edit 

well I'm using the livecd at the moment so...

---

### Post by Mud.Knee.Havoc on 2008-01-20
Oh, there is a possibility that it's just the splash screen that you can't see.  Leave it for a few minutes and see if it boots up OK.  If so, there's a workaround.

---

### Post by kamitsukai on 2008-01-20
> **Mud.Knee.Havoc said:**
> Oh, there is a possibility that it's just the splash screen that you can't see.  Leave it for a few minutes and see if it boots up OK.  If so, there's a workaround.

:lolflag: thanks I'm so impatient i didn't let it load obviously! so what is the workaround?

---

### Post by mgmiller on 2008-01-20
Here is a link to explain how to change the boot parameters at startup to see if mud.knee.havoc's suggestion will work:

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

If you are running the live CD, look in Places/Computer and you should see the hard drive that Ubuntu installed to.  For a session run from the Live Cd, the hard drive should be mounted in /media, so  you can also try looking in Places > Computer and then clicking on file system and look in the /media folder.  

After you see what the drive is called, open a terminal (Applications > Accessories > Terminal) and type:
```
cd /media/"name of drive" (without the quotes)
```
where "name of drive" is the name you saw in media.

Next you will change to the directory where your xorg.conf is located:
```
cd etc/X11
```

next, make a backup of your xorg.conf file
```
sudo cp xorg.conf xorg.backup
```

Next, edit the file:
```
gksudo gedit xorg.conf
```

scroll down to the line that looks like this:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "ati"
EndSection

and change it to look like this:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection

Note, the Identifier in yours may give the name of your video card instead of "Generic Video Card"

click save and close all open windows and reboot without the live CD.

---

### Post by mgmiller on 2008-01-20
> 
Quote:
Originally Posted by Mud.Knee.Havoc View Post
Oh, there is a possibility that it's just the splash screen that you can't see. Leave it for a few minutes and see if it boots up OK. If so, there's a workaround.
thanks I'm so impatient i didn't let it load obviously! so what is the workaround?


Doh!!  ](*,).  Disregard my previous post, and listen to Mud.knee.Havoc for the work around.

---

### Post by kamitsukai on 2008-01-20
lol thanks :P

---

### Post by rosegarden78 on 2008-01-20
> **kamitsukai said:**
> ok but how would i "navigate" im a complete newb :P and how would i edit 

well I'm using the livecd at the moment so...

From a terminal or command line type:

man man = help on help
cp = copy files
cd = change directory
ls = list files
mkdir = make directory
nano = text editor

1) type 
ls 
to see a list of files and folders
2) type 
cd fileOrFolder/path/etc 
to change to that folder

To navigate doww type
cd ..

Sound like you may need Introduction to Computing classes or books.

---

