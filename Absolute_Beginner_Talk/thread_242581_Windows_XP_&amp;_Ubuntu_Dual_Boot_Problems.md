---
title: "Windows XP &amp; Ubuntu Dual Boot Problems"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by wtr_sprts4life on 2006-08-23
Having problems with dual booting. i already have windows xp, but im trying to run ubuntu on a seperate harddrive, but ubuntu keeps over-writing the windows MBR. Im wondering if i swap the windows harddrive which is currently a master, with my linux harddrive which is currently a slave, will the dual boot work, detecting windows & ubuntu, or just ubuntu?

thanks, JB.

---

### Post by bodhi.zazen on 2006-08-23
You have several optins.

Easiest may be to allow Ubuntu to overwrite your MBR. Ubuntu will install GRUB which will give you the option to boot either Windows or Ubuntu.

---

### Post by wtr_sprts4life on 2006-08-23
i did this, but it came up with with a few error msgs, first one i had was error 17 (this was from grub) then i got 21 last night. Any ideas? Thanks fellas.

---

### Post by Changeling on 2006-08-23
That's how I have mine set up, I have the Ubuntu boot loader install on the MBR of my first drive, which is winxp. I'm triple booting windows xp, slackware-10.2 and ubuntu on three drives.

---

### Post by catlett on 2006-08-23
Here is a how to install ubuntu on a second hard drive without touching the window's mbr [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bodhi.zazen on 2006-08-23
> **wtr_sprts4life said:**
> i did this, but it came up with with a few error msgs, first one i had was error 17 (this was from grub) then i got 21 last night. Any ideas? Thanks fellas.

Two thoughts:

First install GRUB BOTH in the MBR and your Ubuntu partition.

Second, what are the contenets of /boot/grub/menu.lst ?

---

### Post by KGH on 2006-08-23
Are your drives SATA, IDE or one each?

---

### Post by wtr_sprts4life on 2006-08-24
sorry but im a newbie at all this. How do i do grub first? Ive got the ubuntu 6.06 live cd, which boots up automatically, then i just select run or install ubuntu, and has a few other options, then when set up, i click install, adn go through the options. My primary master hdd at this point is a maxtor 40gb, and my slave is a quantum fireball 20gb (i suppose i should upgrade soon). Ive got just the one partition on the 40gb, but on the 20gb i have 3 partitions, 1 which i dont intend to lose because it has all my music on it, one as a ex3 format as a /boot and one as a /linuxswap. Im led to believe that the ubuntu mbr installed on the windows, therefore stopping windows from booting, and giving me a error msg, when i think should be giving me an option to boot one or the other? Should i swap the hdds around? id have to adjust the jumpers then wouldnt i?

thanks. JB

---

### Post by bodhi.zazen on 2006-08-24
I do not believe it will help to swap hard drives.

I believe your problem is in configuration of GRUB.

[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Look at/edit /boot/grub/menu.lst

You should see an Ubuntu and a Windows entry.

Presuming Windows is installed in the first partition of the first HD:

Your Windows entry should look something like:
```

title Windows
root (HD0,0)
makeactive
chainloader +1
boot

```

To edit your menu.lst:

In a terminal:
```
sudo nano /boot/grub/menu.lst
```

Use arrow keys to navigate in nano.

To exit nano, look at the bottom of the terminal for options.

Ctrl-X to exit -> Y to save changes. N to exit without saving.

To paste:

1. Highlight text with mouse
2. Move mouse cursor to desired paste location.
3. Push middle mouse button (sometimes twice).

---

### Post by wtr_sprts4life on 2006-08-24
went into sudo nano /boot/grub/menu.lst and it just came up with a blank screen. What should i do? i tryed swapping the hdd's and it did nothing, but it was worth a shot. any ideas?

---

### Post by KGH on 2006-08-24
Try gksudo gedit /boot/grub/menu.lst

Be sure ti use the letter "l" not the number 1 in your command line. 

As a newbie I was not comfortable using nano.

If the command line does not work cut & paste the command line from this post. 

Good luck
KGH

---

### Post by bodhi.zazen on 2006-08-24
first, make sure you are ysing a small "L" or l and not the number 1. (/boot/grub/menu.lst).

If the file is blank then this is your problem.

Re-install GRUB may be easiest. Otherwise you can edit menu.lst manually (which is not hard).

General format:

Windows as above.

Ububtu:
```
Title Ubuntu
root (HD1,x)
kernel=/boot/vmlinuz-x.y.z root=/dev/hdbx ro
initrd=/boot/initrd-x.y.z
boot[\code]
the x in the root (HD1,x)line is not the same number as the x in root=/dev/hdbx
```

get x.y.z from:
```
ls /boot
```
Use the highest # kernel and initrd (x.y.z kernel=initrd)

---

### Post by wtr_sprts4life on 2006-08-24
I messed around with my bios settings, and my computer was seeing my secondary hdd as a "other device" not as a hdd, so i changed it to a hdd, my master (with windows as IDE0, and ubuntu IDE1). reinstalled ubuntu again, and grub booted up just saying please, wait, then after 5mins it said error 25 (im about to look that up.) i havent as yet messed around with the terminal codes. where can i download grub again, and how do i re-program it to make it work? remembering..im a newbie at all this linux stuff.

---

