---
title: "[SOLVED] Problems with sound, wireless and graphics"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by firedragonsf on 2007-12-08
I got Ubuntu today. i have read other posts and i dont understand anything. please could you tell me how to fix it in lame mans terms? i have an acer aspire 57202 laptop if that helps.
heres the problem:

1. "The software source for the package nvidia-glx-new is not enabled" i get this when i try to unrestrict my drivers for a NVIDIA GEforce 8400M GS graphics card.

2. The sound doesnt work. any idea on where i can get sound drivers for "Realtek high definition audio" that work?

3. Same for networks card. no wireless. "802.11 b/g WLAN"

4. "The software source for the package bcm43xx-fwcutter is not enabled" i get this when i try to enable my drivers for ... firmware for broadcom 43xx chipset family.

thanks for the help

P.s what is firmware for broadcom 43xx chipset family??

---

### Post by nikoPSK on 2007-12-08
> **firedragonsf said:**
> I got Ubuntu today. i have read other posts and i dont understand anything. please could you tell me how to fix it in lame mans terms? i have an acer aspire 57202 laptop if that helps.
heres the problem:

1. "The software source for the package nvidia-glx-new is not enabled" i get this when i try to unrestrict my drivers for a NVIDIA GEforce 8400M GS graphics card.

2. The sound doesnt work. any idea on where i can get sound drivers for "Realtek high definition audio" that work?

3. Same for networks card. no wireless. "802.11 b/g WLAN"

4. "The software source for the package bcm43xx-fwcutter is not enabled" i get this when i try to enable my drivers for ... firmware for broadcom 43xx chipset family.

thanks for the help

P.s what is firmware for broadcom 43xx chipset family??

for audio you can do this:
```

asoundconf list
```

that'll list the cards/ audio output devices.

```
asounconf set-default-card XXX
```

where xxx is your card. In my case it was "Audigy"

---

### Post by firedragonsf on 2007-12-08
asounconf set-default-card didnt work, 
error message:
"bash: asounconf: command not found"

what is wrote in : asounconf set-default-card intel
where "intel" is my sound card

---

### Post by nikoPSK on 2007-12-08
whoops, typ

it's:

```
asoundconf list
```

---

### Post by firedragonsf on 2007-12-09
i have gotten everything but my wireless fixed. 
solution:
graphics and #4 = reinstall ubuntu
sound = [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by nikoPSK on 2007-12-09
heres the wireless documentation:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by firedragonsf on 2007-12-09
how/where do i see which networks card i have?

---

### Post by nikoPSK on 2007-12-09
you can list all pci devices attached:

```
lspci
```

---

### Post by firedragonsf on 2007-12-09
> **nikoPSK said:**
> you can list all pci devices attached:

```
lspci
```

what is a pci?

---

### Post by firedragonsf on 2007-12-09
fix for my graphics prob:
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

---

### Post by nikoPSK on 2007-12-09
pci is a "[SIZE=2]Peripheral Component Interconnect" which could be an older graphics card, a pvr card, a wireless card or a sound card. Give me the output of that command.
[/SIZE]

---

### Post by roball80 on 2007-12-09
> **firedragonsf said:**
> asounconf set-default-card didnt work, 
error message:
"bash: asounconf: command not found"

what is wrote in : asounconf set-default-card intel
where "intel" is my sound card

I have the same laptop and it worked for me, I see you wrote intel. It's case sensitive,

---

### Post by nikoPSK on 2007-12-09
maybe Intel with a cap? Do the list thing and give me the output, both of you:D

asoundconf list

---

### Post by nikoPSK on 2007-12-09
heres an example of what I'd do:

```
niko@home:~$ asoundconf list
Names of available sound cards:
Audigy
Bt878
niko@home:~$ asoundconf set-default-card Audigy
niko@home:~$ 

```

---

### Post by roball80 on 2007-12-09
> **nikoPSK said:**
> maybe Intel with a cap? Do the list thing and give me the output, both of you:D

asoundconf list

me@me-laptop:~$ asoundconf list
Names of available sound cards:
Intel
me@me-laptop:~$ asoundconf set-default-card Intel
me@me-laptop:~$

I rebooted but no sound.

---

### Post by nikoPSK on 2007-12-09
It doesn't work like that... Sorry, you have to fool around with the channels in alsamixer

```
alsamixer
```

I find unmuting the card helps. I sent you screenshots of my configuration, might help:D.

---

### Post by roball80 on 2007-12-09
All I get is Master & PCM sliders.

---

### Post by maig on 2007-12-09
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

This worked om my acer aspire 5720z

I'd just like to thank you for posting that, i've been racking my brain trying to get my sound drivers working.

---

### Post by nikoPSK on 2007-12-09
> **roball80 said:**
> All I get is Master & PCM sliders.

maybe my card has more options than yours. Mine is a high quality one.... Well, unfortunately the rest is now up to other members/ yourself as this is now beyond me.

---

### Post by roball80 on 2007-12-09
> **nikoPSK said:**
> maybe my card has more options than yours. Mine is a high quality one.... Well, unfortunately the rest is now up to other members/ yourself as this is now beyond me.

Thanks for your help, I'll figure it out sooner or later](*,)

---

### Post by nikoPSK on 2007-12-09
np, hope you resolve it soon. I resolved my pvr issue 2 months ago and had posted the thread since I joined... the thread had layed dormant for a month:(. I still need to get the infared remote working though.

---

### Post by Nexusx6 on 2007-12-09
> **nikoPSK said:**
> heres an example of what I'd do:

```
niko@home:~$ asoundconf list
Names of available sound cards:
Audigy
Bt878
niko@home:~$ asoundconf set-default-card Audigy
niko@home:~$ 

```

Wait... what??
How did you get a creative card to work in Linux? As far as I knew, the only drivers they had were for the X-Fi, and those only for 64-bit and been beta forever

---

### Post by nikoPSK on 2007-12-09
no, it's built in.

---

### Post by Nexusx6 on 2007-12-09
> **nikoPSK said:**
> no, it's built in.

Oooohh....

cheater! :p

---

### Post by nikoPSK on 2007-12-09
LOL, I'm just cooler than you;). Well I hope you resolve this. In the meantime go with onboard?

---

### Post by Nexusx6 on 2007-12-10
> **nikoPSK said:**
> LOL, I'm just cooler than you;). Well I hope you resolve this. In the meantime go with onboard?

Onboard is exactly what I'm doing for the time being. Knowing Creative and their drivers, it'll be what I'm doing for a loong time, but really and truly - not much of a loss.

---

### Post by nikoPSK on 2007-12-10
good to hear you manning up to it. :lolflag:

---

### Post by roball80 on 2007-12-10
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

:biggrin:I just got my sound going. Thanks for the help, greatly appreciated!!

---

### Post by firedragonsf on 2007-12-11
.

---

### Post by firedragonsf on 2007-12-11
.

---

### Post by nikoPSK on 2007-12-11
> **roball80 said:**
> :biggrin:I just got my sound going. Thanks for the help, greatly appreciated!!

glad to hear!!! :D please mar the thread as "SOLVED"

---

### Post by foppeh on 2007-12-15
Thanks,

I've now got my sound. Three to go. Do you have advise on:
Boot -> often freezes at boot
Display -> Can't find / load driver, low resolutions only
Wifi: not working

---

