---
title: "general apple usage"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by vegetali on 2008-05-11
Hi
 I am not an apple enthusiast at all. But I have the possibility of getting a new macbook for a very low price (basically free). I plan to buy it and use ubuntu. BTW, it seems that linux has a lot of problems to run on mac, basically because of its silly BIOS. My question is: is it really the case? In the macbook wiki, it seems that nothing works out of the box: you have to update firmware for installation; you cannot make more than 2 partitions; sound, microphone, webcam, wifi, bluetooth do not work out of the box. Also, lots of issues on screen, fonts, mouse (do 2 or 3 buttons mouses work on apple?).

My question is: is it really the case, or ubuntu on new macbook work out of the box by the end? I mean, also linux on PC suffers several bugs due to poor driver support, but the average user experience is pretty smooth (none is so unlucky/stupid to get completely unsupported hardware).

I would appreciate any answer, expecially any fast one, since my deal with the macbook expires tomorrow.

Thanks a lot

---

### Post by Aranel on 2008-05-11
> **vegetali said:**
> Hi
 I am not an apple enthusiast at all. But I have the possibility of getting a new macbook for a very low price (basically free). I plan to buy it and use ubuntu. BTW, it seems that linux has a lot of problems to run on mac, basically because of its silly BIOS. My question is: is it really the case? In the macbook wiki, it seems that nothing works out of the box: you have to update firmware for installation; you cannot make more than 2 partitions; sound, microphone, webcam, wifi, bluetooth do not work out of the box. Also, lots of issues on screen, fonts, mouse (do 2 or 3 buttons mouses work on apple?).

My question is: is it really the case, or ubuntu on new macbook work out of the box by the end? I mean, also linux on PC suffers several bugs due to poor driver support, but the average user experience is pretty smooth (none is so unlucky/stupid to get completely unsupported hardware).

I would appreciate any answer, expecially any fast one, since my deal with the macbook expires tomorrow.

Thanks a lot

With Hardy, MacBooks' hardware is fairly well-supported. If you're planning on single-booting with Ubuntu, it shouldn't be too much of a problem to get the disk partitioned; you have the option of formatting the disk as either GPT (can have as many real partitions as you want, with the first three bootable; extended partitions are not allowed) or MBR (operates the same as a normal PC). You'd need to do that from the OS X installer DVD, though, so GParted doesn't accidentally mess something up. As far as hardware support goes, the newest two MacBook models have a wi-fi card with the BCM4328 chip (used in many other laptops too), which has no *native* support in Linux but works fine with NdisWrapper. To get sound working, you need to add one line to a file and reboot--nothing too difficult. To make the iSight webcam work, you also need to install firmware from OS X, but there's a software package to basically automate the process. Other than that, I haven't run into any major problems.

Support for Macs is continually getting better, and getting Linux to run on a MacBook is [well-documented](https://help.ubuntu.com/community/MacBook_Santa_Rosa). You may find that you like OS X too, though; I was pleasantly surprised by it myself when I bought my first Mac in November.

Edit: Er, wait. Is my assumption correct that the model you're being offered is the newest one? Hardware on older MacBooks is supported about the same, but the hardware itself is different (e.g. you wouldn't have to use NdisWrapper for the wi-fi card).

---

### Post by vegetali on 2008-05-11
Thanks for your answer. The macbook is the one currently advertised on the apple website. I plan to single boot with ubuntu, provided I get most of the hardware up and running (in particular, I need webcam, sound and microphone as I live abroad now and use VoIP a lot). I have used MacOS a few times... I doubt I can fall in love with it.

I am a reasonably experienced linux user (although not very technical), so it should not be much of a problem to add lines in configuration files. Still, in the last years I have understood that linux is mature enough, and you need not to spend hours to fix drivers, recompile kernels etc as in the old days... provided you carefully choose your hardware. My only concern is that -if I get the macbook- I could be back at spending days reading doc online. Unfortunately, in these days I can dedicate little time to linux.

Thanks again.

[The bargain with the macbook, is that my university will buy me a laptop: I can choose between the macbook and a cheaper laptop. I still have not made my mind. Apple would probably by lighter and resistant; on the other hand I can choose my hardware for the PC. PC is also closer to my idea of freedom than apple, and at worst I can install and dual boot windows if I ever need some software which is not in linux.]

---

### Post by Uinluan on 2008-05-11
I just installed Ubuntu 8.04 on a Macbook yesterday.  It is about a year and a half old but everything was detected by Hardy Heron out of the box except the wifi.  That was easily remedied by going to terminal and doing and lspci to find out that I had a atheros chipset for a wifi card.  I then googled my exact model and revision and quickly found a howto that allowed me to get my wifi card working in about five minutes.  I downloaded a package which I extracted in my home directory that had the windows driver in it and then did a sudo apt-get install ndisgtk.  I then when to System>Administration>Window Wireless Driver.  Click on it and when it opened clicked on the install driver button and then browsed my way to the .inf filed clicked on it and I was done.

---

### Post by vegetali on 2008-05-11
Thanks for your answer. I made my mind about getting the mac. I will accept the freedom restrictions related to using a mac. By the end, getting window* implies similar (although slightly weaker) restrictions, and you are forced to buy windows when you get a laptop (ok; you are not really forced to, but you have to wait like 60 days to get your laptop windows free).

Linux rocks.

---

### Post by ThatGuyThere on 2008-05-11
I installed hardy on my second-gen Macbook Pro, and it installed with no problems. However, WiFi needed configuration. If you need Windows software, you can use VirtualBox for that. I would personally keep OSX and give it a 10gb leash, if you ever do need that, but hey, that's my 0.02.

---

