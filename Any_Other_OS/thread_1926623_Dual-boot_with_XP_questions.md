---
title: "Dual-boot with XP questions"
date: 2012-02-16
forum: Any Other OS
---

### Post by Moofu on 2012-02-16
I hope I'm posting this on the proper forum, if not please redirect me to the correct location.

Before I leave for college I want to build a small media PC to hold all of my music and movies. Since I have a netbook I also want it to have a DVD drive to rip my CDs and movies. All of my CD's are backed up into FLAC and MP3 (so if MP3 ceases to be standard I won't lose my audio quality and tags).
I've been brainstorming ideas with a friend of mine who has been building computers for years on the best way to do this and here is what we came up with:

-A bare-bones mini atx case/mobo
-A small SSD for running the OS
-A large slow HDD for storing the files (I already have a 750GB HDD, so this is taken care of)
-A wireless card to hook up to Wi-fi

I've built a media server using Mint in my house already and it works great, but it's only running Mint. I would like to dual-boot with a windows system so I can use Handbrake for DVDs (I haven't been able to find a linux app that can match it's quality, so I'm open to suggestions).

This is where my knowledge runs out though. So here are my questions:

-Would there be any problems with dual-booting Linux and XP on the SSD and have the HDD set as the Linux Home partition? I would just access it from both OS's.

-Is there a specific Linux distro that would be best for this purpose?

-Would it matter if I used a USB wi-fi adapter vs an internal card? I'm considering it just to save the space. 

-Is there a better way to complete this setup or anything else that I'm just not thinking of? 

Thank you for taking the time to read all of this.

---

### Post by BeRoot ReBoot on 2012-02-16
> **Moofu said:**
> 
-Would there be any problems with dual-booting Linux and XP on the SSD and have the HDD set as the Linux Home partition? I would just access it from both OS's.

The dual-booting should work, accessing Linux partitions (the ext2/3 file system) from windows requires a driver but can be done.

> -Is there a specific Linux distro that would be best for this purpose?

Ubuntu, Mint, Debian or just about any desktop-targeted distro should work fine.

> -Would it matter if I used a USB wi-fi adapter vs an internal card? I'm considering it just to save the space. 

Check if it's supported by the distro you end up deciding on.

> -Is there a better way to complete this setup or anything else that I'm just not thinking of? 

Just make sure all the hardware you're buying is supported under Linux before you spend any money.

---

### Post by JohnAStebbins on 2012-02-17
> **Moofu said:**
> I've built a media server using Mint in my house already and it works great, but it's only running Mint. I would like to dual-boot with a windows system so I can use Handbrake for DVDs (I haven't been able to find a linux app that can match it's quality, so I'm open to suggestions).

Umm, HandBrake runs on Mint
Assuming you are using the latest version of Mint (12), this link should get you going.
[http://lincgeek.org/blog/?p=1466](http://lincgeek.org/blog/?p=1466)

---

