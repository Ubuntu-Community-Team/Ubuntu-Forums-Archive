---
title: "No sound: Acer Aspire 5720Z"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Fred_S on 2007-11-17
Just bought a new laptop, Acer Aspire 5720ZG.

Sysinfo on my Soundcard:
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Acer Incorporated [ALI] Unknown device 011e

I'm currectly using Ubuntu Gutsy Gibbon (7.10).
Everything seems to work like it should except the sound.
There are completely no sound on headphone, or speakers. i've tried to do something in alsamixer. Seems that it still runs some sound drivers, i can turn the volume on the side key of the computer (turning it high and low) and even mute.

---

### Post by firedragonsf on 2007-12-11
> **firedragonsf said:**
> fix for my graphics prob:
At first boot have an internet connection that helps.

1. Go to System ==> Administration ==> Restricted Drivers Managment
2. Check the enabled box and if you have internet it should fix it self.
3. If not reinstall ubuntu :P

fix for my sound prob:
Sound drivers fix for acer aspire 5720z 
		source: [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

1.Copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh 

2.Then "cd" to it in a terminal 
	code: "cd /home/henrik/Desktop"
  if your file is on desktop

3. then type "sudo sh alsa_1.sh"

4.Now reboot

5.Type "sudo sh alsa_2.sh"

6.Open up terminal and write this:
	"sudo gedit /etc/modprobe.d/alsa-base"

7.It will open up a script, scroll to the bottom, make a new line and write this:
	"options snd-hda-intel model=acer"


Text for alsa_1.sh

```
#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1
```





Text for alsa_2.sh

```
#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2
```





This worked om my acer aspire 5720z

.

---

### Post by Fred_S on 2007-12-17
Thank you very much this helped me, been using ubuntu for a couple of months without sound. Although have you fixed any wireless prroblem? seems my connection to networks are weak.

---

### Post by agerg on 2007-12-18
deleted due to reply to wrong thread (embarrased)

---

### Post by r0cks0ul on 2008-05-02
me@laptop:~$sudo sh alsa_2.sh
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory

i have exactly the same laptop 
with Realtek ALC268

---

### Post by r0cks0ul on 2008-05-05
Ok i fixed my problem none of the solutions here worked for me
I updated from gutsy to hardy heron and during the upgrade it asks me if i want to stay with the current settings on my menu.lst or recreate it. So i decided to stay with the current since im on triple boot (VISTA,MACOSX,Hardy) lazy.... :lolflag: 
I heard on some forum that others upgraded their kernel but they were on -12-generic , so i checked my /boot folder and i saw 2.6.24-16-generic so i edited menu.lst and used it instead of the kernel that i was using on Gutsy w/c is 2.6.22-14-generic and VOILA!!!! i got sounds working........

---

### Post by synz on 2008-07-11
i dont under stand this bit:

2.Then "cd" to it in a terminal 
code: "cd /home/henrik/Desktop"
if your file is on desktop

3. then type "sudo sh alsa_1.sh"

4.Now reboot

5.Type "sudo sh alsa_2.sh"

6.Open up terminal and write this:
"sudo gedit /etc/modprobe.d/alsa-base"

7.It will open up a script, scroll to the bottom, make a new line and write this:
"options snd-hda-intel model=acer"


can you explain what i have to do for each step in detail please because im in this situation aswell.

---

