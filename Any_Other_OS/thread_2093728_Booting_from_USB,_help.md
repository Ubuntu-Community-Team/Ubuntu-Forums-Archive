---
title: "Booting from USB, help"
date: 2012-12-11
forum: Any Other OS
---

### Post by BulgarianBoy on 2012-12-11
Okay I programmed my USB to boot windows xp sp3 but I cannot bc when I click F12 and go to USB it send me to the window where I select Windows xp sp3 or Linux 12.04 LTS; I know that is my Grub window but I don't understand why this happens why it wont wipe my whole hard-drive so I can install Win xp sp3. See i am trying to re install windows xp because I am having problems with it and I need help ASAP.

EDIT: I want to wipe the whole Hard-Drive because my windows was messed up to much to explain after trying to get help I got to no where because the guy told me since it isn't genuine I cannot help you so I wanted to wipe everything and re install it first Win xp sp3 then Ubuntu 12.04.

---

### Post by BulgarianBoy on 2012-12-11
bump-

---

### Post by Cheesemill on 2012-12-11
How did you put the XP installation files onto your USB?

Also please be aware it's forum policy to not bump threads for 24 hours.

---

### Post by BulgarianBoy on 2012-12-11
Sorry. I am using win xp sp3 from my friend that is helping me. Like a bootable win xp from USB that will reformat my hard drive. Well I hope that is what it will do at least.

The reason I am using it is because four files have crashed in my .sys but I cannot fix it.

---

### Post by debodas on 2012-12-11
Check your PM inbox. If it is a pirated version of windows I can't help you there either, its probably got some dodgy software on it.

---

### Post by C.S.Cameron on 2012-12-11
There are quite a few guides for placing the XP installer on flash drive, following is one link:

[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)

---

### Post by BulgarianBoy on 2012-12-12
So I formatted my USB to boot my WIN XP SP3. I check my BIOS and it has the LEGACY USB enabled I put it first still nothing. It just goes on to the GNU GRUB and counts down and picks Windows and continues through. So I think I dont have the option to boot from USB is there a way to change that? I really want to reformat my comp because of the corrupt files I have in my windows which I cannot fix.

---

### Post by dannyboy79 on 2012-12-12
how did you make the usb drive bootable?

---

### Post by BulgarianBoy on 2012-12-12
I used wintoflash and it didn't work :/ ... then used POWER ISO and it didn't boot. I used a CD to boot but I thought it will delete everything but it didn't, it just installed it on the old win xp sp3 and everything works now :) but I still want to wipe everything and partition my hard drives so my Windows has more space.

---

### Post by wnelson on 2012-12-12
In you BIO's do you have usb support set to legacy? If not set it to yes.

Walt

---

### Post by Elfy on 2012-12-13
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by BulgarianBoy on 2012-12-13
Yes it is set to legacy. I figured out that I can boot from usb. The way i figured it out I tried Linux live from usb but when ever I try windows from usb it doesn't work. :/   Maybe it is something I am doing wrong.

---

### Post by oldfred on 2012-12-13
Are you sure your XP is a full install and not the upgrade to sp3?

---

### Post by BulgarianBoy on 2012-12-14
oh man :X I dont know.

---

### Post by BulgarianBoy on 2012-12-14
well i think it would make sense if it didn't start bc my usb live starts so that means that my BIOS can launch it. So probably my version is only an upgrade but If it is only and upgrade it wouldn't run correctly? Bc i am running it right now on and everything works.

---

### Post by kiyop on 2012-12-14
> **BulgarianBoy said:**
> Okay I programmed my USB to boot windows xp sp3 but I cannot bc when I click F12 and go to USB it send me to the window where I select Windows xp sp3 or Linux 12.04 LTS; I know that is my Grub window but I don't understand why this happens why it wont wipe my whole hard-drive so I can install Win xp sp3. See i am trying to re install windows xp because I am having problems with it and I need help ASAP.

EDIT: I want to wipe the whole Hard-Drive because my windows was messed up to much to explain after trying to get help I got to no where because the guy told me since it isn't genuine I cannot help you so I wanted to wipe everything and re install it first Win xp sp3 then Ubuntu 12.04.
Are you sure that you can reinstall windows without any information inside the internal HDD you want to wipe?

If you are sure, you can wipe by booting some linux live distribution CD which contains the command "shred" or "gparted" or "fdisk", such as SYSTEM RESCUE CD.:
1) Boot the live CD.
2) Execute one of the following:
A) Execute with root privilege,
```
shred -n 1 -v /dev/DEVICE_FILE_NAME_OF_INTERNAL_HDD_YOU_WANT_TO_CLEAR
```B) Start Gparted and select correct HDD by clicking "/dev/sda" near the and pulling down. Click "Device" -> "Make a new partition table".
C) Execute with root privilege,
```
fdisk /dev/DEVICE_FILE_NAME_OF_INTERNAL_HDD_YOU_WANT_TO_CLEAR
o
```To tell the truth, the above B) and C) does not erase the *REAL* data on the HDD. It only makes a new MS-DOS partition table without any partition.

---

### Post by oldfred on 2012-12-14
Do not create multiple threads on the same topic. We are all volunteers here and need to know what answers you have already gotten, to avoid confusion and wasting our time.

Two threads on exactly same topic merged. May be a bit confusing as both had several answers.

---

### Post by kiyop on 2012-12-14
> **oldfred said:**
> Do not create multiple threads on the same topic. We are all volunteers here and need to know what answers you have already gotten, to avoid confusion and wasting our time.

Two threads on exactly same topic merged. May be a bit confusing as both had several answers.
Thanks oldfred :)

---

