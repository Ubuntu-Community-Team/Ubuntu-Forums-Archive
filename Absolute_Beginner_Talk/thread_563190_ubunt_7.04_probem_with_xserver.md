---
title: "ubunt 7.04 probem with xserver"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by d_mestar on 2007-09-29
i have this little problem with ubuntu ...
the thing is that when i boot ubuntu and i choose "start or install bla bla bla", everything just goes normaly, he is listing everything he has to ( :P ), and at the and (when the "desktop" with "install" should appear) i get this message: "failed to start the X server (your graphical interface). it is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?"
i can choose between "yes" and "no"... :P
so... when i click yes, among everything else, it says "fatal server error: no screens found"... 
wtf does that mean??? "no screens"??? huh??? :)
and... this is first time ever that i'm trying to install linux... so be gentle...

oh... and i found something about this ([http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)) but it didn't help...
and... i'm doing this on acer5520, nvidia geforce 7000m... :)

---

### Post by eapache on 2007-09-29
Try selecting the safe graphics mode.

---

### Post by d_mestar on 2007-09-29
done... but now ubuntu won't boot... :/

---

### Post by d_mestar on 2007-09-29
ok... now... i manage to do everything i need... and linux is on...
but now i have some more problems... :D (total noob... :P )
let's start...
first of all - how to get the resolution up (i have widescreen - it should work on 1280*800 - but all i have is 800*600 and 640*480)
second of all - i have wlan on laptop, but seems like ubuntu is not recogniseing it... or should i say: "i can't go on internet" :P
third of all - it is the same thing with my graphics driver... :(
and... fourth... nah... can't remember anything at the moment... but will later... 

so... pls... some help... :)

---

### Post by scrapnon on 2007-09-29
Hey, I'm having the exact same problem on a Dell Inspiron E1505 laptop, with an ATI Mobility Radeon vid card. Ubuntu 6.10 (Edgy) works fine though.

---

### Post by macogw on 2007-09-29
You have two different graphics cards and therefore will need two different drivers.  I have more experience with Nvidia than ATI (read: no experience with ATI that uses binary drivers and therefore actually requires work), so I'll help the threadstarter.

d_mestar:
According to Nvidia.com there isn't a GeForce 7000m.  There's lots of GeForce 7xxx, but none of them are 7000.  Are you sure that's the right model number?

---

### Post by handydan918 on 2007-09-30
What ever the specific card model is, the first thing to try is to go to System>Administration>Restricted Drivers Manager
and see if you have the nvidia driver installed. 
if not, install it, and reboot.
Let us know if it works.

---

### Post by d_mestar on 2007-09-30
jes... i'm 101% sure that this is the right number... it says so on laptop and in his specifications...

and in restrictes drivers manager it says that there is a driver named: "nvidia accelerated graphics driver (latest cards)" and status is: "not in use"...
i can't enable it or anything... :(

---

### Post by longboarder on 2007-10-02
This sounds sooo similar to my problem, so I have been catching up on this thread. 

I tried the instructions from [http://ubuntuforums.org/showthread.php?t=187177]("http://ubuntuforums.org/showthread.php?t=187177")
and I learned some stuff. 

When I ran "dpkg-reconfigure xserver-xorg" I had to go to the hp page for my dv6604nr Notebook PC. I found that the Video Graphics was an "NVIDIA GeForce Go 7150M" and it accepted that when I entered it. However, I could not find information about the monitor and I was unsure of the bus locations, but I wrote down how to find out. 

When I tried to run "dpkg-reconfigure gdm" it failed. The last line says action "reload" failed.

---

### Post by n1uro on 2007-10-03
I too have the same problem using gutsy. The mac addresses on both nics go crazy under kubuntu. According to what I've read, the video should take the nvidia driver but doesn't. 

The broadcom bcm94311mcg wlan nic and the nvidia nic both load with invalid mac addresses, and kubuntu won't load ndiswrapper properly, it's forcing the bcm43xx driver. I'd be interested in reading a how-to if you have one.

---

### Post by longboarder on 2007-10-03
hp dv6604

Did you look at this document, [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)) . It talks about blacklisting BCM43xx .

How did you figure out what the wireless driver was? All I could figure out is that it was pretty generic.

---

### Post by n1uro on 2007-10-06
Ok, actually I was able to get the nvidia video working great under X but it's a hack. Appearantly loading the NVIDIA driver through modprobe makes it fail for some reason. Blacklisting it and also running "modprobe -r nividia" right after start) in /etc/init.d/kdm made it work like a champ!
Even the nvidia server utility sees the card as a eForce 7150M, the laptop as an hp-dv6604nr, and the display as Seiko DFP at 1280x800!

Now to figure out the ethenet card and I'll be all set :)

---

