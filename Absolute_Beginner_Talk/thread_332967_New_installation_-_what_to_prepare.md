---
title: "New installation - what to prepare?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by paker on 2007-01-06
Even this Beginner Talk forum is too much for me. Please tell me what to prepare before a new install.

1) I have amd64 x2 3200 cpu. I learned amd64 is the best. I will download Ubuntu 6.10 64bit.
2) I have Foxconn 6150K8MA mobo with built-in nVidia 6150 video and built-in AC 97 audio. Where do I get drivers for these?
3) What would be Ubuntu equivalent of nero (cd/dvd burner)?

PS: My application: some surfing, word processing. In brief, light and casual user.

Thanks.

---

### Post by finer recliner on 2007-01-06
burn the installation disc and boot from it (it will run a live version of linux) and see what works and what doesnt. go from there.

---

### Post by riven0 on 2007-01-06
Yeah, the first thing to do is check if all your hardware is compatible. That's what the liveCD is for. So that's the first step.

Good luck!

---

### Post by maniacmusician on 2007-01-06
I would not recommend using the 64-bit edition. Not as much software is packaged for it, and it's not as well maintained or optimzed as one would like. It's a good thing to test it (if you report bugs and stuff, it will help the development), but you should really use 32-bit if you want to have better access to software and things like that. 

Also, consider how much RAM you have. if you have less than 512 (unlikely as you're runnign a dual-core) then you should download and burn the Alternative Install CD instead of the Live CD. The Live CD is always slower to install from than the text installer (alternate cd), but it's better if you want to test the system before installing it.

There are many ubuntu equivalents of burning CDs though most are not like Nero. There is Gnomebaker, Brasero, K3b, and many others. In my opinions, and others will probably say the same, K3b is the best one out there.

Drivers for your setup are most likely built in to the kernel; Linux is better like that :)

Now, before you do ANYTHING, like installing, messing about, etc, I would compell you to visit this website: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)  . It will help you every step of the way and walk you through the installation. I'd recommend even printing it out so you can look at it during installing.

To start using the site, choose the Introduction link from the left hand side of the screen (under "Just beginning") and that will lead you through it. 

Good luck! if you need anything else, just ask!

---

### Post by IYY on 2007-01-07
> 1) I have amd64 x2 3200 cpu. I learned amd64 is the best. I will download Ubuntu 6.10 64bit.

Good idea. If you are having problems, however, try downloading the regular edition. It will still install, and people sometimes find it to be less problematic.

> 2) I have Foxconn 6150K8MA mobo with built-in nVidia 6150 video and built-in AC 97 audio. Where do I get drivers for these?

The sound card will most likely work out of the box. The video card will probably work out of the box with the community-developed nv driver. However, for better functionality you can download the official nvidia driver using the following instructions (after Ubuntu is installed):

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

> 3) What would be Ubuntu equivalent of nero (cd/dvd burner)?

There are many CD burning applications for Ubuntu. A basic one is already installed for you with the operating system. A burning application with slightly more features is Gnomebaker, available from the repositories (sudo apt-get install gnomebaker). There are others, too.

---

### Post by paker on 2007-01-08
Thanks for your helpful suggestions. Everything is working right, integrated video, integrated sound, printer, CD/DVD writer. I was concerned because the motherboard was not in the "approved motherboard list." 

The main reason I switched from Windows 2000 was incompatibility of the antivirus/spyware/adware suite that I paid my hard-earned money for. I installed ubuntu from the frustration. What a relief!

Now I am having my first ubuntu headache. I cannot get the Korean input right. If anyone is a SCIM expert, please help. SCIM appears to be built in ubuntu, but I cannot get it work right.

Thanks.

---

