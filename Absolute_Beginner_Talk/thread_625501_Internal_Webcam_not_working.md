---
title: "Internal Webcam not working?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by AutoCompliant on 2007-11-28
Heyo my Ubuntu buddies,

I'm semi new to ubuntu, my brother actually introduced it to me, but I've been getting the hang of things pretty easily. But I was wondering.. I have a 'Dell XPS M1210' laptop with a built in webcam and I have been having some trouble getting it to work at all. I've gone to the applications and installed "Camorama Webcam viewer" but when I try to start the application I get the error message "Could not connect to video device (/dev/video0) Please check connection." I was wondering if any of you had solutions to help me out here.

I'm still a novice in terms of the command prompt stuff so if it's not too much trouble the more in depth descriptions the more helpful for me (and maybe others)!

Thanks alot.

---

### Post by linuxwizard on 2007-11-28
Look over, shows notes on getting webcam to work and driver needed

[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210)

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by ubutufan on 2007-11-28
Hi and welcome to ubuntu. I also have the m1210 with gutsy installed. Everything working fine with just 2 glitches. Camera performance and card reader.
For the camera you need to install the uvc driver. For this go to berlios.de and follow the instructions. Camorama will not work. Install Cheese or luvcview. Both work fine but don't expect to have the same quality and tuning options like on windows. Egika will work nicely with the camera.
The card reader is just not recognized at least in my installation. I read in the forums that it works fine with others. I will keep on trying.

---

### Post by cszikszoy on 2007-12-14
Sorry to hear about your card reader.  Mine works flawlessly on the m1210.  Thanks for the links to the video drivers, I'm going to try to get these to work now.

Doesn't ubuntu (7.10) come with uvc already installed?

```

chris@chris-laptop:~$ locate uvcvideo
/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko

```

That being said, webcam still doesnt work on my m1210...

---

