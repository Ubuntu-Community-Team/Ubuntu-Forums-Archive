---
title: "ubuntu-6.06.1-desktop-powerpc.iso does not boot..."
date: 2006-10-11
forum: Apple PPC Users
---

### Post by casta_baga on 2006-10-11
i downloaded ubuntu-6.06.1-desktop-powerpc.iso to  try it on my powerbook G4 without in fact installing it but...
I tried already all the possible keys to let the powerbook boot with the CD...
the manual indicates C + hold  key during starting process but nothing happens..

can anyone just give me some light on what I'm doing wrong in here...

---

### Post by michaelj_99 on 2006-10-11
With the CD inserted, hold the OPTION key during startup.  When permitted select the CD icon and press ENTER.

FYI... It locked up during boot on my G5 desktop. :(

---

### Post by munchbach on 2006-10-12
> **casta_baga said:**
> i downloaded ubuntu-6.06.1-desktop-powerpc.iso to  try it on my powerbook G4 without in fact installing it but...
I tried already all the possible keys to let the powerbook boot with the CD...
the manual indicates C + hold  key during starting process but nothing happens..

can anyone just give me some light on what I'm doing wrong in here...

Are you sure you burned the ISO with disk utility and didn't just burn the file itself onto a disc?

You need to open "Disk Utility" click the "Burn" icon and point disk utility to the Kubuntu ISO file.

Otherwise, as mentioned above try holding down the option key with the Kubuntu disc in your optical drive on boot.

Good luck.

---

### Post by casta_baga on 2006-10-12
yes,, unfortunately u are right...
i made a mistake i burned the mounted image and not like u said...

now is cool.. thank you guys.. 

the desktop resolution is only 640X480 and it is not possible to change...
can u guys tell me why is this? do i have to install an extra drivers or  my powerbook's video card is just not compatible?

thank you once again

---

### Post by freshmeat on 2006-10-12
it seemed work for me at the beginning. it started to boot up and loading the linux image. I could see the "UBUNTU" logo, but after a while, the screen was blank up and it looked like hang overthere. i would like to know what was happen to that. :confused:

---

### Post by seatea on 2006-10-13
casta_baga, if you can, find a manual with your computer specifications for your monitor and video card and run:


sudo dpkg-reconfigure xserver-xorg

Be sure and double check that what is being detected matches your computer specifications. It seems the installer does not correctly configure /etc/xorg.conf.

---

### Post by casta_baga on 2006-10-14
first of all thank you for all the replays so far..

well.. the thing is.. for me to input that command i'll have to restart... myself using the  desktop CD....  no way to display the screen in full blast dimensions because I'm not able to restart the pbook....
i thought about installing it but displaying 640x480 theres no way to see the installations options...

do i have to download the installation CD?

best
t salazar

---

### Post by 3rdalbum on 2006-10-16
When you've got a super-low resolution, you should be able to scroll around on it by moving the mouse onto one of the sides of the screen.

But anyway, go to a terminal and type:

```
sudo nano /etc/X11/xorg.conf
```

Near the bottom of the file, you should see something like this:

```

        SubSection "Display"
                Depth     24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

```

There should be one for each colour depth - I've posted my 24-bit entry. The "Modes" bit shows which resolutions have been entered in for that particular colour depth. You've probably just got "640x480" under your Modes, so just change that to "800x600" or whatever. After you've changed it, press Control-X to exit, the Y key to tell it to save changes, and then the Return key to confirm.

Now press Control-Option-Delete. If you're lucky, the X server (graphical display) will quit and restart, with your new resolution setting.

If you're unlucky, the changes will only take effect after restart... which is pretty useless on the Desktop CD unfortunately :-)   If the mouse-scroll thing or the Xorg.conf editing works, you can install Ubuntu from the Desktop CD.

---

