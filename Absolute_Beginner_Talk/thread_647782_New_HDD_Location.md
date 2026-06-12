---
title: "New HDD Location"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by kjhud on 2007-12-22
I put my HDD that had Linux 7.1 on there onto a new computer. I turned it on and it loaded to the Linux but I have no GUI. It says

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

I click Yes and then it says

"/etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning: Could not retrieve EDID because get -edid is not installed (1)"

Then

"The X server is now disabled. Restart GDM when it is configured correctly."

Help?

---

### Post by Ub1476 on 2007-12-22
The computer has different hardware than the previous one, which Ubuntu has stored th settings for. Run this in the terminal to reconfigure X:

```
sudo dpkg-reconfigure xserver-xorg
```

I advice you to do a clean install so Ubuntu will get the correct drivers and such.

---

### Post by taurus on 2007-12-22
Press <Ctrl><Alt>F2 and login.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure xserver-xorg
```
Reboot and see if it works this time.

```
sudo shutdown -r now
```

---

### Post by markharding557 on 2007-12-22
you will need to reinstall the o/s to suit the new hardware
you can't just rip an o/s out of one pc and put it in another

---

### Post by kjhud on 2007-12-22
I have a 6GB (Linux) and an 80 (XP), why cant i boot to xp though? Or how do i

---

### Post by Ub1476 on 2007-12-22
What error do you get when trying to boot to XP? I guess it has the same problem as Ubuntu..

---

### Post by kjhud on 2007-12-22
> **Ub1476 said:**
> What error do you get when trying to boot to XP? I guess it has the same problem as Ubuntu..Thx the following advice help and Ubuntu is working, now xp...

XP has always been on this PC, I just put the old HDD on this PC in order to have better specs so i can learn/enjoy Ubuntu.

 I have 2 HDDs , when i do a IDE Drive Diagnostics I get:

Primary IDE
             Drive 0: FUJITSU MPC3064AT - Diagnostics not supported
             Drive 1: No device
Secondary IDE
             Drive 0: HL-DT-STDVD-ROM GDR8162B - Diagnostics not supported
             Drive 1: _NEC DVD+RW ND-2100AD - Diagnostics not supported

---

### Post by jken146 on 2007-12-22
I don't think you can take XP out of one box and put it into another like that.  As the dirvers aren't already installed (as they are in Linux), you'd have to install the right drivers for your new hardware before XP will use it.  I guess this might be possible with an XP CD and some Recovery Console work, but I don't know that much about Windows and I'll bet the easiest way is to reinstall it.

---

### Post by kjhud on 2007-12-22
> **jken146 said:**
> I don't think you can take XP out of one box and put it into another like that.  As the dirvers aren't already installed (as they are in Linux), you'd have to install the right drivers for your new hardware before XP will use it.  I guess this might be possible with an XP CD and some Recovery Console work, but I don't know that much about Windows and I'll bet the easiest way is to reinstall it.XP has always been on the PC with 2 HDDs, all I did was put the cable from the XP HDD to the old one and the cable had a splitter so i put that end in the XP HDD, that was the only way for me to connect them both

---

### Post by jken146 on 2007-12-22
Firstly, check that the XP hard drive has the correct jumper settings, if you have changed its position on the cable.

Then, your problem is probably that your computer is looking first to the Ubuntu HD to boot, and it finds GRUB there, which has no entry for XP, since Ubunto was installed on a different machine.  You'll need to edit your /boot/grub/menu.list file (search these forums for a guide) to include an entry for XP.

---

### Post by kjhud on 2007-12-22
> **jken146 said:**
> Firstly, check that the XP hard drive has the correct jumper settings, if you have changed its position on the cable.

Then, your problem is probably that your computer is looking first to the Ubuntu HD to boot, and it finds GRUB there, which has no entry for XP, since Ubunto was installed on a different machine.  You'll need to edit your /boot/grub/menu.list file (search these forums for a guide) to include an entry for XP.

No clue what Jumper cables are, im guessing that it is the white caps with colored cables? I just put the next one that was next on the wiring.

Should I just make it to where the XP HDD is plugged in with the first of the cable series of the IDE?

---

### Post by jken146 on 2007-12-22
Apart from the plug that goes in the motherboard, IDE cables have 2 plugs.  If you have 2 devices connected to this one cable, one must be a master and the other must be a slave.  Which one is the master and which is the slave is determined by the positions of jumpers (little plastic things on pins that can be repositioned -- they make an electrical connection between 2 pins) on the back of the devices.  Look on the stickers on the devices to find out how to place the jumpers correctly.

For each hard drive, there will be 3 options: master, slave and cable select.  The best thing to do is probably make one drive master and the other slave, but if you choose cable select, the drive on the black plug will be master and the drive on the grey plug will be slave.

---

### Post by kjhud on 2007-12-22
ok so i see that the pins is what you are talking about but i dont understand, so i am going to try to understand the pics and I will let you know.

---

### Post by kjhud on 2007-12-22
I fixed it, I had to do the pins and then go to the BIOS, is there anyway to boot Slave first because I dont want to open my case again to make Linux master lol

---

