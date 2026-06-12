---
title: "Need help with drivers installation"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by digimas on 2008-04-10
Hi, I just installed Ubuntu 7.10 and inserted my motherboard drivers cd. This has drivers for my nvidia graphics card, lan, audio and some other stuff. When I enter the cd to view the files I click on the setup files, which are .exe files, and it says that it can't run those types of files. Any way around this? What should I do?

---

### Post by Crafty Kisses on 2008-04-10
> **digimas said:**
> Hi, I just installed Ubuntu 7.10 and inserted my motherboard drivers cd. This has drivers for my nvidia graphics card, lan, audio and some other stuff. When I enter the cd to view the files I click on the setup files, which are .exe files, and it says that it can't run those types of files. Any way around this? What should I do?

Depends, who makes your Motherboard? I'd see if they offer Linux drivers.

---

### Post by digimas on 2008-04-10
.exe stands for Windows executable right? does that mean that there is no way to run .exe files on anything other than windows? I'll go look for my motherboard manufacturer now to tell ya

---

### Post by Sef on 2008-04-10
> .exe stands for Windows executable right? does that mean that there is no way to run .exe files on anything other than windows? I'll go look for my motherboard manufacturer now to tell ya

That is correct.   Look under System > Administration > Restricted Drivers Manager.

---

### Post by Crafty Kisses on 2008-04-10
> **digimas said:**
> .exe stands for Windows executable right? does that mean that there is no way to run .exe files on anything other than windows? I'll go look for my motherboard manufacturer now to tell ya

Technically you can run .exe's in Linux in WINE, but I'm not sure about this one. I'd check to see if the manufacturer offers the Linux drivers, but if they don't, I guess you might want to look into Wine.

---

### Post by Tatty on 2008-04-10
You can "attempt" to run .exe files via wine, although it is not guarenteed they will work.

However this will not work for your drivers.  Windows drivers will not work in linux.

Mostly you do not need to install drivers in linux as you do in windows as the system takes care of most things itself.  Is there anything you feel is not working?

The only thing you might want to install external drivers for is for your graphics card (as the proprietry drivers are generally accepted to work much better than the open source ones).  Go to System->Administration->Restricted Drivers, and see if there are any drivers available that you can enable.

If not, if you could give us details of your graphics card then we could try to figure out if there are any drivers for your to install for it.

---

### Post by digimas on 2008-04-10
Ok, so I went to restricted drivers and this is what is listed: "NVIDIA accelerated graphics driver (latest cards)" On the right there is a box that I can check. I checked the box and clicked "Enable Driver" when a seperate box opened up giving me the two options "Enable Driver" or "Cancel". Then it goes to "Downloading package files" but then says "An error occured: W: Failed to fetch http"//archive.ubuntu.com/ubuntu/pool/restriced/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19 + 2.6.22.4-14.10_amd64.deb Connection failed [IP: 91.189.88.46 80]. Manufacturer of my motherboard is Biostar. Specific name of motherboard: nvidia Geforce 6100 NF61S Micro AM2 SE

---

### Post by digimas on 2008-04-10
The only problem I seem to be experiencing is that my internet connection is very slow and when I try to load a page it takes a long time and after awhile it says done at the bottom left hand corner of the Firefox browser but there is just a white screen. I was suspecting that this was a driver problem related to the LAN driver but I'm not quite sure if that's the problem.

---

