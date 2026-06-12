---
title: "Finally Got Ubuntu Up And Running"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by marcopolo1981 on 2007-12-02
Hi everyone.
I'm very, very new to Linux, so please don't ask me for advice on how to use the terminal thingy!

I have a Dell Inspiron 1520 which now dual boots Ubuntu and Vista with Media Direct working. It took me 5 weeks, with the initial 3 not having any functionality at all! It started and I could look at still pics, and open/edit office apps but couldn't even get online. Don't know why - and I'm not bothered any more.
Well, heres the simplified version of what I did.

[COLOR="Blue"]_Installing Vista:_[/COLOR]
Format Hard Disk with the media direct disc, allocating 40GB to C:
Install Vista onto C:
Install all Vista drivers and Dell Software.
Install Media Direct and update.
Reboot and check no missing Vista drivers for Dell (Don't think its too relevant prior to Ubuntu install?)
Power down and press the Media Direct button. - Allow update of archives, etc...
Reboot into vista and press the Media Direct button from within Vista. 
If all ok continue onto Ubuntu Section. If not, retry Vista install. (This should work first time for anyone with OS installation experience)

Download Current Ubuntu ALTERNATE INSTALL IMAGE. (I tried many live cd's and failed everytime) Burn Image to disc and reboot from said disc.
[COLOR="Blue"][U]
Installing Ubuntu:[/U][/COLOR]
Once splash screen appears, press Enter.
Select Language, Keyboard, etc...
Partition Hard drive - Be sure not to alter the Media Direct or Vista Partitions! 
Complete install and reboot.
Wifi Problems:
Originally, I had the Broadcom chip which I couldn't fix. There are tutorials on how to use ndiswrapper to fix this, but after several attempts, I opted for the Intel chip. £10 from ebay, and well worth it too! Works immediately after entering the network passphrase. 
Sound Problems:
My sound card (Sigmatel HD) wasn't recognised as being present, so I searched the tutorials on how to fix it. I found a solution at [http://ubuntuforums.org/showthread.php?t=577469&highlight=configure+sound](http://ubuntuforums.org/showthread.php?t=577469&highlight=configure+sound)
It was: Alternative 1

    * sudo apt-get install libc6-dev
    * sudo apt-get install patch
    * wget ftp:// ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 (remove the space after the double-slash)
    * tar xvpjf alsa-driver-1.0.15.tar.bz2
    * cd alsa-driver-1.0.15
    * ./configure --with-cards=hda-intel,emu10k1
    * make
    * sudo make install

REBOOT.

A big thanks to ctpaterson for this!
Both the speakers and headphone jack work perfectly.
As far as I can tell, the only things NOT working are the SD, MMC, and Memory Stick Pro readers. But I can live without them anyway.
I hope that this helps others to get Ubuntu working on their Dell's. I don't think I am posting anything new, but hopefully, it will stop the need for thread hopping for solutions.

Best regards to you all,
Mark

---

### Post by dadawan on 2007-12-02
> I hope that this helps others to get Ubuntu working on their Dell's. I don't think I am posting anything new, but hopefully, it will stop the need for thread hopping for solutions.

Congrats, Mark, on getting Ubuntu up and running!  =D>

   For me it took less than an hour to get Ubuntu up and working on my Dell Dimension E510 as a dual-boot system.    However, it became gronked at some later point so I had to reinstall.    Then I reinstalled a third time so I could document every step and take pictures, because I was so enthused about Ubuntu I wanted to make a HowTo.

   Hey if it took a lot of effort to get everything just so, you might want to back up your entire Ubuntu partition.   I did it with the CloneZilla/GParted live CD.

-Kevin

---

### Post by bobyy on 2007-12-02
Hello
for your card reader can you try thys?:
> 
$sudo modprobe tifm_core
$sudo modprobe tifm_sd
$sudo modprobe sd_mod
$sudo modprobe mmc_block

and the SD card shows up

adding:

tifm_core
tifm_sd
sd_mod
mmc_block

to /etc/modules will have them load at boot

---

### Post by marcopolo1981 on 2007-12-02
dadawan, Less than an hour?! WOW! I'm impressed! Did you have any installation/hardware problems? I've read a lot that the 1520 is a pain in the wotsit, so was feeling rather good about getting it up and running. The only reason I've kept vista is for the Media Direct utility. It stopped the self destruct function if I accidentally pressed that button from within Ubuntu. My biggest hurdle was everyone saying to use live cd's, but I just couldn't get them to work. Once I choose the alternate version, it seemed very straight forward. The lack of sound was the only real problem, which was easily fixed. After a few practice runs with this disc, it did only take a few hours which includes searching for the sound fix. Backing up makes sense. I will do that, thanks.

bobyy, Thanks for the codes. I've entered the sudo commands, but where do I enter /etc/modules? It says permission denied without the sudo at the beginning and command not fond if I start with sudo. I'm not familiar with the terminal at all. 
Mark

---

### Post by bobyy on 2007-12-02
sorry my mistake 
> $sudo gedit /etc/modules

and you must add the stuf like in this example
> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored

tifm_core
tifm_sd
sd_mod
mmc_block

---

### Post by marcopolo1981 on 2007-12-02
It's ok bobyy. I did what you said, but it didn't make any difference. Thanks anyway.
Mark

---

