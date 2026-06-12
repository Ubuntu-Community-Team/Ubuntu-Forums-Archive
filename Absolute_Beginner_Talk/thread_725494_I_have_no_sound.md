---
title: "I have no sound"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by awashington on 2008-03-15
Hello all,

Having some problems with sound on my laptop...every time I go to switch on my sound this error message happens:
Code: No volume control GStreamer plugins and/or devices found

I am using clean install of Gutsy 7.10 completely updated.

Help will accepted gratefully.
:(

---

### Post by natman on 2008-03-15
You said turn sound on, have you tried leaving the sound on and restarting, not sure if you can do that, also does the sound work on a Live CD?

---

### Post by Mogurijin on 2008-03-15
Could you please  post the output of:

```
$sudo lshw -C sound
```

That will help get things started.

EDIT: Also a few system specs could be helpful. Mainly system manufacturer and audio device.

---

### Post by awashington on 2008-03-15
sorry i'm new to this. don't mean to be a pain to anyone. not sure what that does but this is what i got back on my screen 


*-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

---

### Post by Tyke91 on 2008-03-15
you will probably need to download/compile your alsa drivers from source. Don't worry, it's intimidating at first, but there is a very well documented page on how to do this.

you have an intel ICH7 family HD audio controller, which at least is supported. so that's good :)

here's a link:
[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29%7C%28troubleshooting%29]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29%7C%28troubleshooting%29")

---

### Post by Mogurijin on 2008-03-15
Well I don't know if this will help:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

It is for the ICH8 family as your's is ICH7. Might still be helpful though.

EDIT:

This might actually be better for you:

[https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847]("https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847")

---

### Post by awashington on 2008-03-15
that was alittle advanced for me I did follow the steps but I still have no sound thanks for your help greatly appreciated

---

### Post by Mogurijin on 2008-03-15
Have you tried the second link I posted?

---

### Post by fenian on 2008-03-15
Download[ this file ]("http://www.stchman.com/tools/alsa/alsa_setup.sh")to your home folder.

make  it executable ,open a terminal and type...

> chmod 755 ~/alsa_setup.sh

run the script,in the terminal type...

> sudo ./alsa_setup.sh

the script shoul install the alsa driver and restart your computer.

---

### Post by awashington on 2008-03-15
yes i just tried the second link still working on it

---

### Post by awashington on 2008-03-15
hey i did that it restarted my laptop and now i'm at the command line and it's asking for my login when i log in how do i get back to the desktop

---

### Post by fenian on 2008-03-16
My apologies it seems the script has messed up your xorg configuration,to fix this first try this...
Login at the prompt then run...
> 
sudo dpkg-reconfigure -phigh xserver-xorg

Then enter....

> sudo reboot

If that doesn't work try this....
> 
sudo apt-get install ubuntu-desktop gdm

then 
> 
sudo reboot

---

