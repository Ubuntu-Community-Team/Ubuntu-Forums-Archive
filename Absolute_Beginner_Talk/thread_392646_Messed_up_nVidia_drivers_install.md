---
title: "Messed up nVidia drivers install"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by KillerHamster on 2007-03-24
I managed to totally kludge up my first install of Ubuntu (really nice so far until my newness to it killed X server forever). Reinstalled it basic stuff only (just basic drivers etc...). Now my problem didn't come with getting the drivers installed (or so I think?), but when it came time to configure them...

What I did I found through google (I am new, please do not laugh).

1. sudo apt-get update

2. sudo apt-get install nvidia-glx

3. sudo dpkg-reconfigure xserver-xorg

4. Restarted X-server (got the nVidia backsplash to appear and everything upon restart of X).

5. Logged in and wondered why I was jammed in 640x480 60Hz on a monitor that can run 1600x1200 @ 85Hz (screen resolutions was locked to that being my only setting).

6. Through another google search I apt-get'd nvidia-settings and set that up...rebooted...

7. ?? X server died ?? 

Whatever I did I really owned X server hardcore - I can get command line but thats it, GDM is dead.

What is the easiest way to do this so I don't own my next install?

---

### Post by r4ik on 2007-03-24
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

### Post by KillerHamster on 2007-03-24
I don't know what I did...but it has graphics again (magic?).

Now how do I enable higher than 640 resoluitons and 85Hz? :/

---

### Post by r4ik on 2007-03-24
Try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck!

---

### Post by KillerHamster on 2007-03-25
That link is a dud :/

---

### Post by Dark Lord Peaches on 2007-03-25
open up a terminal window and type "sudo nano /etc/X11/xorg.conf"(capitalize the X its picky that way) and change the driver for your graphics card from "nv" to "nvidia" and see if that helps any, it did for me

---

### Post by KillerHamster on 2007-03-25
Nevermind, have you guys ever heard of a router not playing nice with a mixed Linux/Winblows setup? I am having to constantly reset my router ever since I got the linux box working; some sites will work others will be duds. Half the time I cannot even ping newegg or google but I can load amdzone...

---

### Post by Dark Lord Peaches on 2007-03-25
do you have a Linksys WRT54G by any chance

---

### Post by KillerHamster on 2007-03-25
No it is an SMC hard router (10/100 x8 ports w/swtich)...pretty old and I am fairly sure it is a Linux based router (though I may be mistaken).

In other news Envy killed my GDM (again). Seems I am stuck at the command line...some lib file is missing (though I cannot install it with the apt-get install linux-headers command as it is giving me some odd error about being >=2.0.0).

---

### Post by KillerHamster on 2007-03-25
Ok, I have narrowed the X server error down to just the missing header (the only FATAL: error I get now). However I cannot get it to install...

I ran sudo apt-get install linux-headers 2.6.7-10-386 --->leading to a statement about that not being the explicit package required.

The nVidia library missing is the /lib/linux-headers-2.6.7-10-386/volitile/nvidia.ko

What the hell do I do? I hate being new...but I am trying not to stay new :(

---

### Post by lamalex on 2007-03-25
try apt-get install linux-headers-`uname -r` that should do it

---

### Post by KillerHamster on 2007-03-25
I got the linux headers to finally install...but I am still getting the missing /volitle/nvidia.ko error that is killing X server. I do not know what to do to get it to reinstall...

---

### Post by KillerHamster on 2007-03-25
Anyone have any ideas? Or should I just reinstall the whole Ubuntu (I hadnt done anything else to the install except attempt drivers).

---

### Post by Dark Lord Peaches on 2007-03-25
what nvidia graphics card do you have, i updated my nvidia drivers last night and was having trouble with x server but i fixed it by ```
sudo dpkg-reconfigure -phigh xserver-xorg

```
and reinstalling the nvidia drivers off of the nvidia website

---

### Post by KillerHamster on 2007-03-25
I reinstalled Ubuntu...but Envy will not work now. Getting the following error:

"Dependency is not satisfiable: module-assisant"

---

### Post by al1b1 on 2007-03-26
google the module assistant file it is available as a .deb in the debian repostries
Sounds like youre having a tough time for a starter

---

### Post by KillerHamster on 2007-03-27
Through creativity I worked around the problem and have both nvidia-settings configured and working as well as the monitor working at 1280x1024 @ 75Hz (so I can still use my LCD).

Now have any of you guys ever had problems with a mixed Windows/Linux network? I do not think this should be an issue AT ALL, but my SMC 8-port router (switched) is giving me more trouble than I have ever had with any peice of network equipment. Every time I access the web on the Linux machine all the windows machines in the house (3 others) stop having access to the internet...

In 4 years of building my own networks/computers I have never come accross such a situation, what the hell is going on here? It all started when I turned on the Linux machine and got it working with the Web.

---

