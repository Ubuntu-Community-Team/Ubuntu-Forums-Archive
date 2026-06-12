---
title: "webcam and tv tuner switch devices"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by mcsimon on 2008-03-30
hi there,

I have a tv tuner set up and working well. 

However there is one problem; upon rebooting the device identifier sometimes switches with my webcam, making the tuner /dev/video1 instead of /dev/video0. this is an annoyance to me as i have to go and change the settings in my tv program when they switch.

What i would like to know is: Is there a way to make sure that the tuner is always recognised under the same device?

---

### Post by Mud.Knee.Havoc on 2008-03-30
There probably is a way.  I've got two sound cards and had to force one to be loaded first, so it's always the same device (otherwise sometimes sound comes out of your speakers, after a reboot it comes out of your headphones). :)

It's been quite a while since I've done this, though.

Sorry I can't be of any more help, but hopefully somebody else will see this, or you can use this as a starting point and see if you can adopt the "multiple sound card" solution.

---

### Post by Cresho on 2008-04-12
hi!  this is not working either.  the one that worked is the post after this one.  this section works for figuring out your card's modules used by linux.
I am running into the same problem you are but with one high definition video card and also a analog tv tuner card.  So far, I was able to gather just information.

to get your card location, i use this.
```

dmesg | grep video
and this is the result
[   24.225857] Boot video device is 0000:02:00.0
[   35.385207] Linux video capture interface: v2.00
[   36.461640] bttv0: registered device video0
[   36.694678] saa7133[0]: registered device video1 [v4l2]

```

or if you have xawtv installed from add and remove programs (you can also use lsmod but its too long)
```

xawtv -hwscan

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-12-generic)
looking for available devices
port 280-311
    type : Xvideo, image scaler
    name : NV17 Video Texture

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (AVerMedia TVCaptur
    flags: overlay capture tuner

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : Kworld ATSC110/115
    flags: overlay capture tuner

```

I know I have bt878 (avermedia stereo) for my avermedia from other readings and the saa71330 is my high definition card (kworld plustv115) from further reading.  I would search google (you need to know what module works for you because modules load up at boot and automatically assign or install the devices in randomness ) "modules avermedia stereo  linux load modprobe" and it gaved me a location to where I can use a command bttv in modprobe.  now for my high definition, i did the same.  I google "modules kworld 115 linux load modprobe" and I did reading on this particular section [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)  just take a look and the guys here laid it easily for me to find what module to use in modprobe.  I'll help you in your case too...not hard.



so i have bttv to use as my first loader for my avermedia and from doing my reading again I have a saa7134_dvb  and a saa7134-alsa to install in my modules.

so here goes the fix.
```

sudo gedit /etc/modules

```
and change or add or what ever.


fuse
lp
sbp2 



to 

fuse
lp
sbp2
bt878

so it looks like this when i am done
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
bt878

```
save file and reboot and your good to go!


i updated this.  i did not load the high definition modules with modprobe because it still caused randomization.  I am still tweaking.  with bt878 so far alone, i have not expirienced video switching.  still looking if it will switch.

update # 2, I have not expirienced any video switching at all doing this method.  So far, load up the module in modprobe for the card you want to be video0.  Seems to work!
NOw you can reboot and check your hardware with


update 3
this is not working either.  still playing with settings

another up

xawtv -hwscan

and see if anything else is jerking you around.

---

### Post by Cresho on 2008-04-13
ALRIGHT!!!!!  THIS ONE IS THE WINNER.

I decided not to read further and just unload and force the modules to load at a certain order in a specific time filling the video0 an video1 slots.

i created a sh file tv-fix.sh and right clicked on the properties.  I went to permission and allowed it to execute.

I use this code.

```
#!/bin/sh
sleep 2 && modprobe -r bt878;
sleep 2 && modprobe -r saa7134_dvb;
sleep 2 && modprobe bt878;
sleep 2 && modprobe saa7134_dvb;
```

so now it loads up in this specific order and my avermedia stereo is now video0 all the time! and my tv time wont pick up my video1 since I am forcing it through this method.

if you want this script to load automatically at startup, go into
system->preferences->sessions
and call it videofix or something.  navigate to where you are going put the sh file and highlight and open.  now it will automatically load at startup fixing your problem.


[http://ubuntuforums.org/showthread.php?p=4706171#post4706171](http://ubuntuforums.org/showthread.php?p=4706171#post4706171)

I am sure this is just a cheap way of fixing the problem but what I want to know is what is the correct way of fixing modprobe from randomly adding video devices into any dev/video.

---

### Post by Cresho on 2008-04-24
Here is an update to this.  I just noticed that you need super user rights for the modprobe.  I recently had a switch in cards and was unable to view my television.  If I envoked every line with sudo in the terminal, It worked fine in allowing tvtime to detect my analog card instead of digital.  So what I did now was instead of using sudo in the script(for security reasons) I am using init.d to automatically launch the script.

after you created the script from above, you sudo nautilus in the terminal and copy the script you created to the /etc/init.d directory.  and then in the terminal you do a (if you script is called tv-switch-fix.sh)you execute this in the terminal to update it.

sudo update-rc.d tv-switch-fix.sh defaults

and it gives you a few lines verifying the updates.  Now your script will load when you boot up the operating system and correclty fix your video issues.

---

### Post by Cresho on 2008-04-27
still working on it!

---

### Post by Cresho on 2008-05-04
just figured out how to blacklist.  I'm posting this here since nobody helped and I read up through alot of stuff just to get this working.

after doing the above in identifying that my card uses the bttv module and the bt878 for the avermedia stereo, i did the following

sudo nautilus /etc/modprobe.d

add 2 files
blacklist-bttv and type in blacklist bttv in the file
blacklist-bt878 and type in blacklist bt878

in the blacklist, edit with gedit and add

blacklist bttv
blacklist bt878

sudo gedit /etc/modules

add these two at bottom

bttv
bt878

reboot and now video is video1 instead of video1 or video0

---

