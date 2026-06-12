---
title: "[SOLVED] Broke my sound..."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by doorknob60 on 2007-12-30
Well...earlir I tried to download and compile a newer version of ALSA using a script to see if it would fix sound in Zsnes...it didn't. Now my sound wont work at all. [[IMG]http://img247.imageshack.us/img247/6721/screenshotsoundpreferenak3.png[/IMG]](http://imageshack.us)

As you can see now it doesnt detect my sound card at all, and it used to work just fine. Here's what lspci says my sound card is: ```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

Also I tried sudo apt-get remove alsa and then sudo apt-get install alsa there weren't any errors but sound still doesnt work...help please?

---

### Post by doorknob60 on 2007-12-30
Bump! Come on I need sound!

---

### Post by doorknob60 on 2007-12-30
PLease! I know you can help me, you guys are smart!

---

### Post by pissedoffdude on 2007-12-30
Try using synaptic to completely remove the alsa packages and to reinstall them.  Which script did you use to install the alsa driver?

---

### Post by ^rooker on 2007-12-30
There are 2 frequent problems with ALSA:

1) Do you have multiple soundcards in your system (including webcam, headset, etc...)?
Please post the output of
"asoundconf list"

Sometimes the default soundcard is set to the wrong device.
(You can fix it by running "asoundconf set-default-card CARD" (where "CARD" is the name of your soundcard as shown by "asoundconf list"))

2) Another app is blocking the device. If you're using KDE, try killing "artsd" - in gnome, esd is sometimes blocking the device, too.

---

### Post by doorknob60 on 2007-12-30
Incase you are wondering, this is the script that I used: ```
#!/bin/sh

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
# https://help.ubuntu.com/community/HdaIntelSoundHowto
#
# Authored by Bob Nelson  admin@stchman.com
#
# This script updated 9/6/2007


script_name="alsa_setup.sh"

# Script must run as root 
if [ $USER != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

# Install the required tools
sudo apt-get -y install build-essential ncurses-dev

# Install your kernel headers
sudo apt-get -y install linux-headers-`uname -r`

# Change to users home folder
cd ~

# Get the files from www.stchman.com
wget http://www.stchman.com/tools/alsa/alsa-driver-1.0.15.tar.bz2
wget http://www.stchman.com/tools/alsa/alsa-lib-1.0.15.tar.bz2
wget http://www.stchman.com/tools/alsa/alsa-utils-1.0.15.tar.bz2

# make a new folder 
sudo mkdir -p /usr/src/alsa

# Change to that folder
cd /usr/src/alsa

# Copy the downloaded files to the newly made folder
sudo cp ~/alsa* .

# Unpack the tar archive files
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2

#Compile and install alsa-driver
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

# Compile and install alsa-lib
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install

# Compile and install alsa-utils
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

# Remove the archives as they are no longer needed
rm -r -f ~/alsa-driver-1.0.15.tar.bz2
rm -r -f ~/alsa-lib-1.0.15.tar.bz2
rm -r -f ~/alsa-utils-1.0.15.tar.bz2

# Add the following line to the file, replacing '3stack' with your model
sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base

# Reboot the computer
sudo reboot
```

And here is the output of asoundconf list: ```
austin@austin:~$ asoundconf list
austin@austin:~$ 

```lol that probably won't help much.

I'm currently using the complete remove in synaptic for alsa I'll tell you if I get it to work.

---

### Post by doorknob60 on 2007-12-30
Didn't work :'( help please

---

### Post by doorknob60 on 2007-12-30
I really need sound to work!! May I remind you that it doesn't even detect my sound card anymore?

---

### Post by ^rooker on 2007-12-30
puuuuh....

I know that this might sound a bit non-linux-like, but did you try to reboot before re-installing alsa?
(Just to make sure that the "other" sound card driver (kernelmodule) is not loaded anymore? - you could also do that manually if you knew which kernelmodule your card requires)

Furthermore: Which alsa packages did you remove/reinstall?
(I've checked on my system, and these could be related: alsa-base, alsa-utils, libasound2, linux-sound-base)

And: you don't happen to have a backup of your /etc/ folder, do you?

------
PS: Why did you try to compile alsa yourself in the first place?
I think you don't need to run that script at all, unless you have a High-Definition Audio card (HDA).

---

### Post by doorknob60 on 2007-12-30
I'm pretty sure I restarted.... And I compiled ALSA because I was bored and my sound was horrible quality in ZSNES and I thought that this could fix it...and no I didn't back anything up.

---

### Post by ^rooker on 2007-12-30
Which alsa packages did you re-install?
(I've added a list of packages to my previous post)

--EDIT:
1) please paste the output of "lsmod | grep snd".
For your soundcard it should look somewhat like this:
> snd_atiixp_modem 17160 0 
 snd_via82xx_modem 16264 0 
 snd_intel8x0m 18572 6 
 snd_intel8x0 34972 2 
 snd_ac97_codec 100644 4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0 
 ac97_bus 3200 1 snd_ac97_codec 
 snd_pcm_oss 44672 0 
 snd_mixer_oss 17664 1 snd_pcm_oss 
 snd_pcm 80388 8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
 snd_seq_dummy 4740 0 
 snd_seq_oss 33152 0 
 snd_seq_midi 9600 0 
 snd_rawmidi 25728 1 snd_seq_midi 
 snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi 
 snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 snd_timer 24324 2 snd_pcm,snd_seq 
 snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 snd 54660 28 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore 8800 1 snd 
 snd_page_alloc 11400 5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm 

2) What does "cat /proc/asound/cards" say?

---

### Post by doorknob60 on 2007-12-30
I reinstalled all the packages from the last post, and it still doesnt work.

```
austin@austin:~$ lsmod | grep snd
austin@austin:~$ 

```

```
austin@austin:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

```

Yeah....something's definaltly missing.

But I'll just try completely removing, rebooting, and then completely reinstalling again.

---

### Post by doorknob60 on 2007-12-30
Crap! Tried anddd still nothing. What I need is to tell it that I have a sound card cuz it doesnt detect anything.
EDIT: It does show up in lspci just like in my first post though.

---

### Post by ^rooker on 2007-12-30
You could try to manually load the kernel modules:

"sudo modprobe snd_intel8x0"

and then do "lsmod | grep snd" again - and check the output of "dmesg"

---

### Post by doorknob60 on 2007-12-30
```
austin@austin:~$ sudo modprobe snd_intel8x0
[sudo] password for austin:
FATAL: Module snd_intel8x0 not found.
austin@austin:~$ 

``` -.- i should have never got that stupid script lol

---

### Post by ^rooker on 2007-12-30
1) Could also be that ubuntu has this module under a different name. Try:
"modprobe snd-intel8x0"
("-" instead of "_")

2) I'm currently trying to figure out which package contains the soundcard kernel modules.
3) Please check the contents of your audio drivers:
"ls /lib/modules/`uname -r`/kernel/sound/pci/"

---

### Post by doorknob60 on 2007-12-30
```
austin@austin:~$ ls /lib/modules/`uname -r`/kernel/sound/pci/
ac97     ca0106       echoaudio  ice1712   nm256    rme9652  ymfpci
ali5451  cs46xx       emu10k1    korg1212  pcxhr    trident
au88x0   cs5535audio  hda        mixart    riptide  vx222
austin@austin:~$ 
```

hmm i dont see intel in there

also thanks for all your help so far

---

### Post by ^rooker on 2007-12-30
I think I got it!

The sound modules are **not** in one of the alsa packages, since they are kernel modules.

Re-install your kernel package:
In my case that is e.g. "linux-image-2.6.17-12-generic"

You can verify if it's the right one, if you open synaptic and check:
1) it must already be marked as installed.
2) if you right click and select "properties" you can see "installed files" - there you should see a loooooot of /lib/modules/... including the one for your soundcard. 


Good luck!

---

### Post by doorknob60 on 2007-12-30
Currently reinstalling right now :D

-.- the download is going at 45kB/s zzzzzz

IT WORKED!!hanks soooo much! You rock!

---

### Post by ^rooker on 2007-12-30
Whooopee!
Good to hear that.

---

