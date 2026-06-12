---
title: "Cannot install ubuntu 12.10 on Eeepc 1025 Flare series"
date: 2012-11-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ncholson on 2012-11-26
I just buy an eeepc 1025 Flare series and wanna install ubuntu 12.10 on it, but after installation all i have just a black screen with text and can't log in to my desktop, is there something wrong with ceddar trail ??? need ur help :confused:

---

### Post by ncholson on 2012-11-29
Need help :confused:

---

### Post by fantab on 2012-11-30
> **ncholson said:**
> I just buy an eeepc 1025 Flare series and wanna install ubuntu 12.10 on it, but after installation all i have just a black screen with text and can't log in to my desktop, is there something wrong with ceddar trail ??? need ur help :confused:

As of today, there is no good, workable open source (Linux) driver for the Cedar Trail PowerVR and Intel Graphics GMA3600.

**Read** the following links:
[**ubuntuforums=gma3600**]("http://ubuntuforums.org/showthread.php?t=2060510&highlight=gma3600")
[**Intel Cedar View/Archlinux**]("https://bbs.archlinux.org/viewtopic.php?id=141858")
[**Intel Community**]("http://communities.intel.com/message/158477")
Please google for more.

I have a Asus 1015CX and had loads of issues installing and getting the Linux to work on this machine... the good news however is that Intel has provided some sort of open source support to Red Hat Linux (Fedora) for the PowerVR chipset and Gma 3600 so we can expect some progress in the near future, hopefully.

Of all the Linux distros I have personally tried (and I have tried a few) on my machine only **Fedora 17** (xfce and lxde) worked out of the box, meaning it installs and boots without any issues. It is the only Linux distro that, I have tried, detects the screen resolution correctly (1024x600) and that&#8217;s it. HD video is very poor though. You can play youtube videos upto 480 pixels without any issue depending on your internet connection quality. If you read the above link to intel community you will learn more on how to build your own kernel with working drivers. (I haven't tried it though). Fedora 18 will be released sometime in January 2013 lets hope it comes with better support for our machines.

Another distro that works on the said machine is **Bodhi Linux** but you have to use it with "nomodeset" option during boot. It too has the same issues with playing quality videos/graphics.

I have also tried **Xubuntu 12.04** and it works too but again you should not try to install the 'additional drivers' it prompts you to install otherwise the system breaks and I was forced to reinstall. (If some elders can help us install these additional drivers correctly then perhaps we can get more out of our machines)

So, Until there is better support for the said drivers in Linux our options are very limited. I have Bodhi (which is based on Ubuntu LTS) presently running on my Asus and it is very satisfactory as long as you can avoid high quality videos.

Good Luck...

EDIT: Only 32 bit OS works on my machine.

---

