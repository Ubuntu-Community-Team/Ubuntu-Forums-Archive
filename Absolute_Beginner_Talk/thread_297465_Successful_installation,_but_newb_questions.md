---
title: "Successful installation, but newb questions"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-11
Thanks to the help here on the forum and searching through the older threads I was able, despite being a total newb, to install Ubuntu 6.10 on my Asus A6K laptop. I now have a dual boot system with Ubuntu and Windows XP.

Here some issues I am having trouble with:

**Wireless:**

My only access to the internet (updates, tutorials, files)is through my wireless home network.

I have an Asus wl-120g wifi card with a broadcom processor. I tried following this tutorial: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

...but failed during step 1) which requires access to **Ubuntu Universe Repository**. Since my wireless access is not set up yet I cannot access the Repository.

This means I was not able to download and install bcm43xx-fwcutter.

**My question is, can i download bcm43xx-fwcutter manually from somewhere and install and then continue with the HOW TO? (If yes, where and how?).**

**Partition:**

During the install of Ubuntu, I was asked how large I would like to make the Ubuntu partition, the default value was 37GB, but I wanted 20GB, it does not seem to have respected my entry, the Ubuntu partition now has about 37GB and my Windows XP partition is left with only 3GB free.

**My question, can I fix the partition sizes somehow without messing up Windows XP or Ubuntu? I want to make the Ubuntu partition a little smaller and use the space to make the Windows XP partition a little larger.**

Thanks in advance.

---

### Post by Perfect Storm on 2006-11-11
To download packages manually: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Architeuthis on 2006-11-11
There are many programs to resize your partitions (like[ gparted]("http://gparted.sourceforge.net/") and [qtparted]("http://qtparted.sourceforge.net/")). They are available in your repostitories.

---

### Post by PartisanEntity on 2006-11-11
Thanks for the info and links. I was able to download bcm43xx-fwcutter and install it, I followed the instructions in the  'how to' I mentioned here earlier but no luck, I don't even know if my wifi card is compatible with ubuntu, whether its set up correctly, whether the system even knows its there, or whether it is active?

---

### Post by Architeuthis on 2006-11-11
Wireless cards are a big issue with linux, not all cards are supported, situations are improving though.

I advise to search for help on this overview page on the wiki:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Check this page out if your card is even supported by the Linux kernel: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) (if it isn't it maybe is in a month, the support grows larger at a fast rate)

---

### Post by PartisanEntity on 2006-11-12
> **Architeuthis said:**
> Wireless cards are a big issue with linux, not all cards are supported, situations are improving though.

I advise to search for help on this overview page on the wiki:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Check this page out if your card is even supported by the Linux kernel: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) (if it isn't it maybe is in a month, the support grows larger at a fast rate)

Thanks for the info.

I did see the BCM4306 mentioned several times on that list, so I am assuming my Asus wifi card with a BCM4306 chip is supported.

Yet I can't get it to work with Ubuntu 6.10. Now I am a total newb to Linux so it could also be the case that I am doing something wrong. But I am sure I have followed 2-3 HOW TO's exactly as mentioned.

:(

---

### Post by webjames on 2006-11-12
Hey,
i had problems with a USB wireless card, many hours wasted. if you can i have found it easier to just run a wire whilst you try and configure your WiFi card.

Good luck,

Regards,
James

---

### Post by Architeuthis on 2006-11-12
Your guide is about ndiswrapper, i have no experience with ndiswrapper myself (my wireless card works perfect out of the box). 
But i can adivise you to check out the ndiswrapper page: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 
or their support page: [http://ndiswrapper.sourceforge.net/support.html](http://ndiswrapper.sourceforge.net/support.html) (forums, irc channel) 
Maybe you can find better help there, if you haven't already tried to do so.

If that cant help you, you'd better start a new thread about your card so you can hopefully reach people who can help you better.

---

