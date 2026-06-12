---
title: "White screen on Startup"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Roberto80 on 2007-09-09
Hi. Big time noob on Ubuntu. I'm using a Toshiba Satellite 5105-S501 with 512M RAM and an upgraded 120G hard drive. I was attempting to enable the graphic drivers when it needed to reboot. When it did I the login screen was all white and I couldn't see a thing. I knew I was on the login screen because I entered my login name, then password and the start up music played. Yet the white screen was still there. I'm pretty new at this, but I can handle instruction well. Anyone know what I can do? I checked the similar threads, but I don't know what beryl is... Thank you.

---

### Post by Linux_Man on 2007-09-09
What drivers are you using? Ati or NVidia? and then im assuming propriatary drivers. If you don't know if its Ati or NVidia there should be a little sticker on your laptop saying which it is.

---

### Post by Arwen on 2007-09-09
There's still blank screen in recovery mode?Did you enable desktop effects?
which graphics card you use?

---

### Post by Roberto80 on 2007-09-09
Its an NVIDIA GeForce4 440 Go. When I first installed Ubuntu, the screen worked fine. I was assuming the pre-existing drivers were working fine. But there was an indicator that stated that I needed to update my display drivers and it gave me an option to do it automatically. So I did. When it started up again, White screen...

Is there another way to install these manually or should I have not had them install it automatically? What did I do wrong?

Thank you.

---

### Post by gogogadget on 2007-09-10
I had the same problem but my solution was quite simple. I hope this helps you.

Log in to recovery mode and when it is finished you will be at the command prompt and logged in as root.

change directory 

cd /etc/X11

create a backup of the file we are going to alter
cp xorg.conf xorg.conf.backup

use you favorite editor and edit xorg.conf
gedit xorg.conf

looking through the file you might see Load	"glx"
simply comment this line out be putting a hash (#) in 1st column of the line so it reads
#	Load	"glx"

reboot

and all should be ok

---

### Post by Roberto80 on 2007-09-10
> **gogogadget said:**
> I had the same problem but my solution was quite simple. I hope this helps you.

Log in to recovery mode and when it is finished you will be at the command prompt and logged in as root.

change directory 

cd /etc/X11

create a backup of the file we are going to alter
cp xorg.conf xorg.conf.backup

use you favorite editor and edit xorg.conf
gedit xorg.conf

looking through the file you might see Load	"glx"
simply comment this line out be putting a hash (#) in 1st column of the line so it reads
#	Load	"glx"

reboot

and all should be ok

Hi gogogadget,

I got all the way up to gedit xorg.conf
and got this:

cannot open display:
Run 'gedit --help' to see a full list of available  command line options.
root@ubuntu:/etc/X11#

I must have done something wrong maybe...

---

### Post by kirenpillay on 2007-09-12
Commenting out the GLX line works.

Thanks!

---

