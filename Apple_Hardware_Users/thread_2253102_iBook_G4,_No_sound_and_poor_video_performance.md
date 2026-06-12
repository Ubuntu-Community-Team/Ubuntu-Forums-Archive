---
title: "iBook G4, No sound and poor video performance"
date: 2014-11-17
forum: Apple Hardware Users
---

### Post by Alpay_Aygn on 2014-11-17
Hi this is my first post,

Specs:
iBook G4 mid 2005
PowerPC G4 1.42 Ghz
1.5 GB DDRI SDRam
ATI Mobility Radeon 9550 

First of all, I have no sound. I updated everything but nothing, also i searched on google but my problems werent fixed
I also have bad performance with my Radeon 9550, Do I have to install drivers?

greets

---

### Post by rican-linux on 2014-11-17
What version of Ubuntu are you running? Have you look at the at the Ubuntu PowerPC FAQ wiki?

[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

### Post by Alpay_Aygn on 2014-11-17
Ehm sorry for not telling which version of ubuntu i use, its 12.04 LTS. I looked up there but i cant fix it with that thing there. and for people who ask themselves why someone uses a PC with PowerPC in it, I love using older tech stuff, 10.4 was boring for me. I recently discovered how ****ing awesome ubuntu is.

---

### Post by rican-linux on 2014-11-17
what do you mean bad performance? I was running Ubuntu 12.04 and I am running Xubuntu 12.04 pretty well with the expection of a few bugs.

can you run thus command cat /proc/cpuinfo

---

### Post by Alpay_Aygn on 2014-11-18
somehow now the performance isnt that bad, but i still cant get sound to work :(

---

### Post by rican-linux on 2014-11-18
Did you go through the instructions in the first part of the wiki link I sent you?

---

### Post by Alpay_Aygn on 2014-11-19
Yes I did nothing changes, its so frustrating. I did that and saved, rebooted and noticed that my volume is muted but still no sound when i turn them on

---

### Post by rican-linux on 2014-11-19
can you ls these two files and send the results?

 /etc/modprobe.d/blacklist.local.conf
/etc/modules

Also when you do a reboot enter this in yaboot prompt with this if you have not tried it already:  "Linux video=radeonfb:1024x768-32@60"

---

### Post by Alpay_Aygn on 2014-11-19
lsalpay@iBookG4:~$ ls -R /etc/modprobe.d/blacklist.locan.conf
ls: Zugriff auf /etc/modprobe.d/blacklist.locan.conf nicht möglich: Datei oder Verzeichnis nicht gefunden
alpay@iBookG4:~$ ls -R /etc/modules
/etc/modules
alpay@iBookG4:~$ 

folder not found

---

### Post by rican-linux on 2014-11-19
I am sorry I meant cat those files. Apologies

---

### Post by Alpay_Aygn on 2014-11-20
sorry but how do i cat those files? google didnt help

---

### Post by rican-linux on 2014-11-20
cat /etc/modprobe.d/blacklist.locan.conf
cat /etc/modules

---

### Post by Alpay_Aygn on 2014-11-21
alpay@iBookG4:~$ cat /etc/modprobe.d/blacklist.local.conf
blacklist snd-aoa
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-soundbus
blacklist snd-aoa-i2sbus
blacklist snd-aoa-codec-tas

alpay@iBookG4:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd_powermac
apm_emu
snd-powermac
therm_adt746x
alpay@iBookG4:~$

---

### Post by rican-linux on 2014-11-21
> **Alpay_Aygn said:**
> alpay@iBookG4:~$ cat /etc/modprobe.d/blacklist.local.conf
blacklist snd-aoa
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-soundbus
blacklist snd-aoa-i2sbus
blacklist snd-aoa-codec-tas

alpay@iBookG4:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd_powermac
apm_emu
snd-powermac
therm_adt746x
alpay@iBookG4:~$

You need to delete the first file by running this command:
sudo rm /etc/modprobe.d/blacklist.local.conf

Then you need to edit the modules files by running this command:
sudo nano /etc/modules 

Add these lines at the end:
snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas

Then reboot and test.

---

### Post by Alpay_Aygn on 2014-11-21
didnt work, but at the thing you test the sound it says

Analog Headphones
Keylardo/intrepid Mac I/O

before that it was dummy

---

### Post by rican-linux on 2014-11-21
ok now run this command:
alsamixer

and verify the PCM channel is set to 80

---

### Post by Alpay_Aygn on 2014-11-21
Hahha thank you it works now!

---

### Post by rican-linux on 2014-11-21
Everything I walked you through was detailed the Ubuntu PowerPC FAQ wiki. The wiki has a wealth of information that will help you as you work through Linux on the PowerPC. I also recommend this blog to you as well [http://ppcluddite.blogspot.com](http://ppcluddite.blogspot.com). There wealth of information specifically on alternatives to flash video play back. 

[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

