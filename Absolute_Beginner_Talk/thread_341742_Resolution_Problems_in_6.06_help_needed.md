---
title: "Resolution Problems in 6.06 help needed"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by gingerj on 2007-01-19
Hi all,

I installed 6.06 just over a month ago, and ever since I've installed my resolution has been really poor with no ability to up it like my windows partition.

Currently the maximum resolution that I can select is 1024x768 which looks hideous especially for web design work. 

On my windows partition I've currently go it set to 1280x720.

Is the solution to my problem that I haven't installed the ATI Drivers, to get my ATI Radeon Mobility card working on Ubuntu to up the resolution? If so could anyone point me to any terminal cmds to help with the degubbing/problem solving stage.

Also could anyone point me to a fail safe method of installing the ATI Drivers as I've read a couple of threads where people have tried and reboot to find no gui. Which has put me off doing this until now, I only really do stuff until I know all the answers. So perhaps someone could also point me in the correct direction of what if it fails and I've go now gui how do I restore stuff again? Is this  via Ubuntu "Recovery" mode which is on my GRUB configuation?

Cheers!!

---

### Post by Quillz on 2007-01-19
Since you have an ATI Radeon card, you need to use the fglrx driver in order to properly configure your resolution. It should be available via Synaptic.

---

### Post by gingerj on 2007-01-19
> **Quillz said:**
> Since you have an ATI Radeon card, you need to use the fglrx driver in order to properly configure your resolution. It should be available via Synaptic.

Is that an ATI Binary Driver?

---

### Post by gingerj on 2007-01-19
Hi all I've tried to get this to work and it seems to have not installed correctly via Synaptic.

What I did was once Synaptic loaded, I did a search for "fglrx" and installed this package:
"xorg-driver-fglrx" and rebooted my laptop.

I then went to System > Preferences > Screen Resolution and I still can only select 1024x768 as the highest resolution. So I googled to check the terminal command to check fglrx installed correctly and it's given me this error.

> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


Can anyone pointed me in the right direction as to how I can fix this problem with my ATI Radeon Mobility card so I can up the resolution to something half decent. I wouldn't mind getting all the 3D Desktop stuff going one day but just getting the resolution up isa must.

Cheers in advance :D

---

### Post by bodhi.zazen on 2007-01-19
I am not so familiar with ATI

See if this helps:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by jr3us on 2007-01-19
Right now, from all that i have seen on the forums and experienced, the nvidia and ati video cards are the dogs breakfast.. partly due to nvidia and ati, partly due to Xorg and partly due to ubuntu.

Some distributions handle video from these cards better than others. I have nvidia, ati, and intel video, and nvidia and ati have been he11 to make work properly, 3d or not.

intel works good but only in 2d mode.

As mentioned in this thread and others, there are workarounds that sometimes work, sometimes don't. If you visit the ubuntu development section, one of their primary goals for the 'feisty fawn' version of ubuntu is to get the video configuration right!

---

### Post by gingerj on 2007-01-19
I've printed off a document from one of the wiki's, that says to do this:

After the apt-get command (I presume this is the same step as when I went straight to Synaptic and grab from there)

Do I need to do these steps and then shutdown -r now.

$ sudo aticonfig --initial
$ sudo aticonfig --overlay-type=Xv

I've read a couple of docs but there's numerous ways I'm a bit confused. Does anyone have any concrete methods? Or advice I've seen ton's of compiz screens so surely some of you guys have got 3d working on your Ubuntu systems.

Any help would be appreciated.

---

### Post by bodhi.zazen on 2007-01-19
> **jr3us said:**
> Right now, from all that i have seen on the forums and experienced, the nvidia and ati video cards are the dogs breakfast.. partly due to nvidia and ati, partly due to Xorg and partly due to ubuntu.

Some distributions handle video from these cards better than others. I have nvidia, ati, and intel video, and nvidia and ati have been he11 to make work properly, 3d or not.

intel works good but only in 2d mode.

As mentioned in this thread and others, there are workarounds that sometimes work, sometimes don't. If you visit the ubuntu development section, one of their primary goals for the 'feisty fawn' version of ubuntu is to get the video configuration right!

I have had good experience with the nvidia driver on my nvidia card across multiple distro's, including Ubuntu, LTS up to Feisty.

Now it is even easier:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

install the generic linux kernel package, use envy, no porblem ..

The nvidia driver will configure your monitor from the nvidia-settings gui,

Including twinview :guitar:

Last, this is not the "fault" of linux, you need to bring this up with ATI and Nvidia whose drivers are not open source. Take you beef up with ATI/Nvidia and ask them to support Linux a little better.

I am sure the open source community would build better faster drivers then ATI and Nvidia...

---

### Post by gingerj on 2007-01-19
Just a small update I just did this command in the terminal as the wiki told me to do it but nothing happen after the restart. Although I'm not sure what was meant to happen after this commend:

sudo depmod - a

I also took a look at the blacklist file: /etc/default/linux-restricted-modules-common and there was no sign of fglrx so I know it's not blacklisted. So it's kinda left me slightly more confused regarding why these drivers don't work.

---

### Post by gingerj on 2007-01-20
Sorry to bump this but I do need some help :D

---

### Post by bodhi.zazen on 2007-01-20
Which version of Ubuntu are you running ?

It looks to me as if you just keep going, did you get an error message ? If not ...

> sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a  **<- You are here** ;p
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Now Reboot your system:

sudo shutdown -r now

Then:

 Confirm that it works

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

Just keep going with **sudo aticonfig --initial** ....

Otherwise, did you get some kind of error message ???

In Linux if a command works you will get no output to the terminal to confirm it worked :p

Only an error message if there were a problem ;)

---

### Post by gingerj on 2007-01-20
When doing the sudo aticongfig --initial command I get the following error message.

> 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0


---

### Post by je1117 on 2007-01-20
Ginger, I believe that is what it is supposed to output. It's just saying that its reconfiguring your xorg and backing up your old one.

What kind of mobility card are you running?

---

### Post by gingerj on 2007-01-20
The model is the X1300

---

### Post by je1117 on 2007-01-20
First go to your Synaptic Package Manager and find/uninstall fglrx-control fglrx-kernel and fglrx-source and also xorg-driver-fglrx (if you don't have one or many of these, it's fine.) REBOOT.

I have a Radeon 9200, and I know our cards are quite on opposite ends of the spectrum here, but I think that this guide works really well. [FOLLOW THIS]("http://www.ubuntuforums.org/showthread.php?t=204910")

The drivers you need if you are running 32bit arch. is [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run")

The drivers for 64bit arch is [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.32.5-x86.x86_64.run")

Just follow those directions VERY carefully, If your computer boots to a black screen startup in recovery mode and type:
sudo nano /etc/X11/xorg.conf.original-0     and then save it as xorg.conf to overwrite.

---

### Post by gingerj on 2007-01-20
I think I've got it completely working now?

when I run fglrxinfo I get this:

> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300 Generic
OpenGL version string: 2.0.5814 (8.25.18)


Btw thanks everyone for replying to this thread and helping me out (that is if this is what I should be seeing).

I'm currently running in 1200x800 now :D

---

### Post by je1117 on 2007-01-20
fantastic, why don't you head [here]("http://www.ubuntuforums.org/showthread.php?t=221320"), and let everyone else know how you did it! :D

---

