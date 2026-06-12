---
title: "Is wireless on ubuntu as bad as other linux OSs?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-02-15
I recently bought an HP laptop for school last month, and I am already sick of xp. I have xp at home, on a system that I built. Ive only experienced one blue screen with it, but my laptop constantly crashes. I would understand if I bought a crappy laptop, but I spent 1500 on it and im having problems. Anyway, I have friends who have ubuntu on their desktops and love it. I want to install it on my laptop to dual boot with xp, but I recently read a digg article saying wifi is the main problem concerning linux. Is this true? If anyone has experience with this sort of stuff please post. I have an HP dv6000z, which consists of an amd turion 64 x2 mobile TL-60 cpu, 2gb ram, 120 hd, geforce go 7200, and Broadcom 802.11a/b/g WLAN. If anyother information is needed, let me know. Any response would be greatly appreciated. :guitar: :guitar: :guitar: :guitar:

---

### Post by Bachstelze on 2007-02-15
Broadcom is definitely not the right company to make business with if you value software freedom but most of their stuff work well with ndiswrapper, in *any* Linux distro, not just Ubuntu.

---

### Post by Motoxrdude on 2007-02-15
It is a hit or miss thing. My wireless card worked without a hitch using ndiswrapper, while some people have difficulties with it. There are some tutorials on how to use it. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by em11488 on 2007-02-15
thanks for the help, but do any of you know a website or guide that would help me install ubuntu with xp that would allow me to upgrade to vista eventually.
thanks.
i see people are much more friendly and outgoing when it comes to freeware and linux than anyother subject i try to get help with. I appreciate it greatly.

---

### Post by figgles on 2007-02-15
> **em11488 said:**
> I recently read a digg article saying wifi is the main problem concerning linux. Is this true? If anyone has experience with this sort of stuff please post. I have an HP dv6000z, which consists of an amd turion 64 x2 mobile TL-60 cpu, 2gb ram, 120 hd, geforce go 7200, and Broadcom 802.11a/b/g WLAN. 

Google "ubuntu HP dv6000z" and you'll see various postings by such owners and loading Linux. Yes, loading linux on a laptop isn't as painless as a computer OEM'ed to run Windows. Yet, from SuSE, Fedora, Mandrake and ubuntu, ubuntu is the least painful to load. In my scenario, it was painless -- but that's no guarantee.

Wifi is a common sticking point for laptops. I was unable to get my DLink PCMCIA card to run reliably (including ndiswrapper) until it worked out of the box under ubuntu.

The safe thing to do is get a live CD -- boot of it, see what you think. You don't have to install it to check it out. The trade off is that you'll spend less money on using your computer and waste far less time on internet security issues. The plenty of other reasons to consider running linux, but those are probably more mainstream.

---

### Post by figgles on 2007-02-15
One other option: [http://www.vmware.com/vmtn/appliances/directory/ubuntu.html]("http://www.vmware.com/vmtn/appliances/directory/ubuntu.html") I've heard good things about checking out OS'es this way without reconfiguring your base system.

---

### Post by scrooge_74 on 2007-02-15
Try to set it up using a Live CD, that was the first thing I try on the Toshiba I am using right now, in fact I did the same on another Toshiba (a newer one) and had no troubles.  Also on a Sony using a PCMCIA wireless card from Linksys  the card was detected from the start no problems

---

### Post by kolinab on 2007-02-15
Hello,

I can say from reading these forums that wireless is a problem for some people. For me it was a breeze - maybe I got lucky. One thing you can check is some user pages for laptops similar to yours. You may not find your exact laptop on this list but I'm willing to bet that laptops from the same series of yours likely have the same wireless chipsets etc., and the configuration information might be similar.

Try these pages for extra info:

[http://www.linux-on-laptops.com/hp.html](http://www.linux-on-laptops.com/hp.html)

[https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard)

You can check your system documentation or look in Device Manager I suppose to find out details on your wireless adapter if you want to look up in advance what it is . . . then you could search the forums if you run into trouble. That's one thing that helps a lot of people before they install an OS - make a list of your hardware (esp. video card) information, resolutions, etc. That way you know what hardware you're working with before you get heavy into troubleshooting. But I'm getting ahead of myself - you might not have to do much troubleshooting! Ubuntu works well 'out of the box' for many systems.

The best thing to try to see how things will work for you is the Live CD. Download and burn a Live CD, plug it in, and go for a test run. The Live CD won't make any changes to your hard drive whatsoever. 

There's some good information on dual booting Ubuntu with XP around here. Don't know how much luck people are having with dual booting Vista so far, but one page I recommend is:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

There's great information there that can walk you through downloading and burning, partitioning, etc. Have a look around there and keep posting your questions here when you have them.

Good luck!

K

---

