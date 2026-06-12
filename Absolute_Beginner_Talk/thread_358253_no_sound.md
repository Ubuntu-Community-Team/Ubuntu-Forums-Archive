---
title: "no sound"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by copliesflip on 2007-02-10
i am very new to ubuntu and i have installed the 6.10 version on a older ibm computer with an on board audio card and i cant get any sound to come out. my question is how do you configure an audio card with unbuntu?

---

### Post by r4ik on 2007-02-10
Double click you're speaker to get into the mixer and see if anything is muted.
Also try Edit - Preferences to see if some boxes are still empty.
If everything seems okay and there is still no sound please try,


[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio)

Good luck !

---

### Post by copliesflip on 2007-02-10
ok so now i am going to sound really stupid, but when is says "Go to a shell and type aplay -l"  where do i go to find the shell? is that under accessories terminal?

---

### Post by fusiachi on 2007-02-10
Yes, that's correct.

---

### Post by copliesflip on 2007-02-10
Ok so i only got as far as the part where it asks you to put in lspci -v but my sound card is onboard and i went into the BIOS and made sure that the sound was enabled but still when i click on the sound icon it says "no volume control GStreamer plugins and/or devices not found

can anyone please tell me what to do now?

---

### Post by nickoli_02 on 2007-02-10
At the terminal, try typing "alsamixer". This will launch the sound mixer, and in here you can check to see if anything is muted. Navigate with the arrows, up and down to increase/decrease volume. "M" mutes/unmutes. Try unmuting everything, that's how I fixed my sound :P

---

### Post by r4ik on 2007-02-10
Are you using Dapper or Edgy ?

---

### Post by r4ik on 2007-02-10
Sorry Edgy.

---

### Post by r4ik on 2007-02-10
Try in a Terminal,

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

    * Save the edited file 

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo aptitude update

Again in a Terminal,

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

When finished,

Press 'Ctrl + Alt + Backspace'

From,
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Good luck !

Copy and paste :)

---

### Post by copliesflip on 2007-02-10
So when i tried the "alsamixer" it told me "function snd_ctl_open failed for default: no such device" Every time it boots up it says "[17179569.184000] APCI unable to locate RSDP" i dont know what this means, could it be the problem?

---

### Post by Skidpad on 2007-02-10
> **nickoli_02 said:**
> At the terminal, try typing "alsamixer". This will launch the sound mixer, and in here you can check to see if anything is muted. Navigate with the arrows, up and down to increase/decrease volume. "M" mutes/unmutes. Try unmuting everything, that's how I fixed my sound :P
Thanks!  I had sound on my laptop, just not enough, even when my volume was all the way up.  After opening *AlsaMixer*, I turned my PCM volume up (it was almost muted).  Problem fixed!

---

### Post by nickoli_02 on 2007-02-10
glad I could help :)

---

### Post by copliesflip on 2007-02-11
I tried doing all those steps several times and after much confusion I still don't have any sound. I have no idea what any of that really did but it doesn't seem to have made any difference. 

Thanks for your help, do you have anything else for me to try?

---

### Post by nickoli_02 on 2007-02-11
Try this howto on troubleshooting sound problems:

[Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449")

From your previous post it looks like it's not seeing your sound card.

---

### Post by copliesflip on 2007-02-12
Yea so I have tried this before and I only make it to the second step and I fail because my sound is onboard and it is enabled in the BIOS so I don't know what to try

---

