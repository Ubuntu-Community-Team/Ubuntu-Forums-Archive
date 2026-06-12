---
title: "Core 2 Duo &amp; Gutsy - 32 or 64 bit install?"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by rickwood on 2007-10-18
About a year ago I bought a core 2 duo Macbook to replace my old windows box.  I enjoy OS X, but still prefer Ubuntu & gnome.  However, it's been kind of a pain to make all of the hardware work with Ubuntu.  A week or so ago I downloaded the RC version of Gutsy and gave it a try as a live disc on my Macbook.  Looks like out-of-the-box support for the Macbook has improved greatly, so I want to install Gutsy now that it's out.

My question is which version -- 32 or 64 bit?  I'd love to try the 64-bit version, but don't know what software will still have incompatibilities.  Does Flash now work for 64-bit?  Also, will I have any problems running Parallels or VMWare on a 64-bit install?  Any other things that won't work with 64-bit (software or hardware)?  Or have most of the wrinkles been worked out with 64-bit?  And last but not least, will I even notice a difference in performance between 32 and 64-bit?

---

### Post by cyberdork33 on 2007-10-18
> **rickwood said:**
> About a year ago I bought a core 2 duo Macbook to replace my old windows box.  I enjoy OS X, but still prefer Ubuntu & gnome.  However, it's been kind of a pain to make all of the hardware work with Ubuntu.  A week or so ago I downloaded the RC version of Gutsy and gave it a try as a live disc on my Macbook.  Looks like out-of-the-box support for the Macbook has improved greatly, so I want to install Gutsy now that it's out.

My question is which version -- 32 or 64 bit?  I'd love to try the 64-bit version, but don't know what software will still have incompatibilities.  Does Flash now work for 64-bit?  Also, will I have any problems running Parallels or VMWare on a 64-bit install?  Any other things that won't work with 64-bit (software or hardware)?  Or have most of the wrinkles been worked out with 64-bit?  And last but not least, will I even notice a difference in performance between 32 and 64-bit?

No 64-bit Adobe Flash Player yet. 
There are a couple solutions:
Gnash is still buggy, but has a 64-bit version (is available in ubuntu):
[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

and you can run 32-bit firefox in the 64-bit OS. This is a messy process, but many do something that runs 32-bit apps in a chroot sorta thing. I don't have any information on that though.

---

### Post by rsambuca on 2007-10-18
Actually, Flash works just as well with Gutsy now.  There really is no reason not to use the 64bit system.

---

### Post by rickwood on 2007-10-18
Thanks for the information.  I torrented both versions this morning, so I'll give the 64-bit install a try when I get home from work.

---

### Post by kzimir on 2007-10-19
> rsambuca

how do you mean? no npwrapping (or similar) needed any more? does the 32bit player just runs out of the box in the 64bit firefox? how does that work? curious.. because i have some 32bit binary i would love to give a try but i couldnt get em run yet on 64bit.

thanx..

---

### Post by rsambuca on 2007-10-19
> **kzimir said:**
> > rsambuca

how do you mean? no npwrapping (or similar) needed any more? does the 32bit player just runs out of the box in the 64bit firefox? how does that work? curious.. because i have some 32bit binary i would love to give a try but i couldnt get em run yet on 64bit.

thanx..
To be honest, I have no idea how the develpers got it working, but Flash definitely works  out of the box now with 64bit Ubuntu.  For a Java plugin, you still have to use the blackdown Java, which has some security issues, but it does work.

---

### Post by rickwood on 2007-10-20
Yup, I can verify.  I installed 64bit yesterday.  First time I hit a flash page in Firefox, it couldn't find a plug-in, making me think that it wouldn't work.  But for some reason, the next time I hit a page it prompted me to install Flash.  I chose adobe's version, and it works fine so far.

Now if I could just get this wireless networking thing to work! :mad: It's no fun to have a laptop that has to be connected to a wall for the network to function!

---

### Post by onekopaka on 2007-10-21
Try installing madwifi. That should give you wireless. I'm trying to do that with my Acer Aspire 3680.
-Onekopaka

---

### Post by rickwood on 2007-10-21
> **onekopaka said:**
> Try installing madwifi. That should give you wireless. I'm trying to do that with my Acer Aspire 3680.

Tried several versions of madwifi -- could see the networks, but couldn't connect.  Finally gave up and installed 32 bit ubuntu.  Madwifi acts the same as in 64 bit.  Tried ndiswrapper, and it works like a charm.  Now just need to find a driver that supports wireless N and all will be perfect (except I'm stuck with 32-bit instead of 64-bit).

---

### Post by stuartbh on 2007-10-22
Ubuntu Users:

My understanding is that the "amd64" bit version is not to be used on the Mac Intel products that are anything other than XEON based (and as far as I know, there are no XEON based Intel based Macs). Apparently the "amd64" bit version is really only tuned (or perhaps tested) on AMD 64-bit hardware and the Intel XEON.

Thus, in light of the forgoing instantiates, one is compelled to educe that indeed it is best to maximize risk mitigation regarding the leveraging of the "amd64 bit" version on Core 2 DUO hardware; now therefore, I am downloading the 32-bit version in precedence to my forthcoming purchase of a new MacBook Pro in the next some several months.


read the page that pops up predicated upon assertion of this URL:

[http://cdimages.ubuntu.com/dvd/20071017/](http://cdimages.ubuntu.com/dvd/20071017/)


V/R,

Stuart

---

### Post by rsambuca on 2007-10-22
> **stuartbh said:**
> Ubuntu Users:

My understanding is that the "amd64" bit version is not to be used on the Mac Intel products that are anything other than XEON based (and as far as I know, there are no XEON based Intel based Macs). Apparently the "amd64" bit version is really only tuned (or perhaps tested) on AMD 64-bit hardware and the Intel XEON.

Thus, in light of the forgoing instantiates, one is compelled to educe that indeed it is best to maximize risk mitigation regarding the leveraging of the "amd64 bit" version on Core 2 DUO hardware; now therefore, I am downloading the 32-bit version in precedence to my forthcoming purchase of a new MacBook Pro in the next some several months.


read the page that pops up predicated upon assertion of this URL:

[http://cdimages.ubuntu.com/dvd/20071017/](http://cdimages.ubuntu.com/dvd/20071017/)


V/R,

Stuart

I haven't heard of this before.  Do you have any links where I might find some info?

---

### Post by rsambuca on 2007-10-22
Upon further checking, it appears that the AMD64 version works on much more than just the Xeon line.  Basically you should be fine with any Core 2 Duo.

---

### Post by aidanr on 2007-10-22
> **stuartbh said:**
> Ubuntu Users:

My understanding is that the "amd64" bit version is not to be used on the Mac Intel products that are anything other than XEON based (and as far as I know, there are no XEON based Intel based Macs). Apparently the "amd64" bit version is really only tuned (or perhaps tested) on AMD 64-bit hardware and the Intel XEON.

Thus, in light of the forgoing instantiates, one is compelled to educe that indeed it is best to maximize risk mitigation regarding the leveraging of the "amd64 bit" version on Core 2 DUO hardware; now therefore, I am downloading the 32-bit version in precedence to my forthcoming purchase of a new MacBook Pro in the next some several months.


read the page that pops up predicated upon assertion of this URL:

[http://cdimages.ubuntu.com/dvd/20071017/](http://cdimages.ubuntu.com/dvd/20071017/)


V/R,

Stuart

Matrix fan? Vis a vis ergo :-s

---

### Post by cyberdork33 on 2007-10-22
Two corrections

1. The 64-bit software is based on x86_64 instructions that were developed by AMD. The Intel64 instruction set is almost the exactly the same. I *think* all Core Duo processors have x86_64 capability.


2. Mac Pros have Xeon Processors.
[http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?nnmm=browse&mco=7B72365D&node=home/shop_mac/family/mac_pro](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?nnmm=browse&mco=7B72365D&node=home/shop_mac/family/mac_pro)
> **Quad-core or 8-core, all Xeon**

                                                  Every Mac Pro packs the power of two multicore Intel Xeon processors. Choose two 3.0GHz quad-core “Clovertown” processors — the fastest Quad-Core Intel Xeon available — for groundbreaking, 8-core power.
                                                  Or configure a quad-core Mac Pro with a pair of dual-core “Woodcrest” processors at 2.0GHz, 2.66GHz, or 3.0GHz.

---

### Post by S.G. on 2007-11-05
I have just acquired a Core 2 Duo Macbook Pro. I've searched the Internet and it seems quite difficult to install Ubuntu. Does this Gutsy version improve installation, or it is necessary to follow all the complicated steps listed everywhere? [If so, does anyone know a web page with a clear list for beginners?]

I don't really mind not using the wifi, can I thus install the AMD64 version without further inconvenience?

Thanks in advance,

Soledad

---

### Post by cyberdork33 on 2007-11-05
> **S.G. said:**
> I have just acquired a Core 2 Duo Macbook Pro. I've searched the Internet and it seems quite difficult to install Ubuntu. Does this Gutsy version improve installation, or it is necessary to follow all the complicated steps listed everywhere? [If so, does anyone know a web page with a clear list for beginners?]

I don't really mind not using the wifi, can I thus install the AMD64 version without further inconvenience?

Thanks in advance,
Soledad


The toughest part is partitioning your hard drive for Ubuntu. Most of the 'guides' are outdated, and really aren't needed anymore.

To partition you can use Boot Camp beta by turning back the clock on your mac, or you can use the [commandline]("http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes"). Otherwise you can use a live cd like [parted magic ]("http://partedmagic.com/")to shrink your mac partition down to make room for Ubuntu.

---

### Post by Jackster on 2007-11-05
> **cyberdork33 said:**
>  I *think* all Core Duo processors have x86_64 capability.

All Core 2 Duos have x86_64, but the original Core Duos _didn't_ have x86_64 as far as I know.

---

### Post by michwill on 2007-11-05
The questions regarding parallels seem to have been left unanswered.  It would appear that Parallels is a no-go with the 64 bit OS.  I'm currently installing [VirtualBox]("http://www.virtualbox.org/").

---

### Post by cyberdork33 on 2007-11-05
> **michwill said:**
> The questions regarding parallels seem to have been left unanswered.  It would appear that Parallels is a no-go with the 64 bit OS.  I'm currently installing [VirtualBox]("http://www.virtualbox.org/").

Worked ok for me with VMWare. Doesn't make a difference. If the VM supports it, then yes, if not, no. I don't know that there is any advantage to using a 64-bit OS in a VM though.

---

### Post by natros on 2007-11-05
> **rsambuca said:**
> I haven't heard of this before.  Do you have any links where I might find some info?

Does that mean that we shouldn't be using the AMD64 iso for core 2? I'm starting a migration from gentoo to Ubuntu 64 and I have a core2quad with 4GB ram (for now, next week 8GB :). What should I install? 32bit Ubuntu or is there a special version for core 2?

---

### Post by roaldz on 2007-11-05
I don´t know what the fuzz is about nowadays, because 64bit gutsy is just as good (if not even better) as 32bit gutsy. I have an Core 2 Duo T7200 laptop, and I´m running 64bit gutsy for a while now, and its just smooth:)

Enjoy!

Roald

---

### Post by rsambuca on 2007-11-05
> **natros said:**
> Does that mean that we shouldn't be using the AMD64 iso for core 2? I'm starting a migration from gentoo to Ubuntu 64 and I have a core2quad with 4GB ram (for now, next week 8GB :). What should I install? 32bit Ubuntu or is there a special version for core 2?

For the Core 2 Duo, use the amd64 version.

---

### Post by Rog-Mahal on 2007-11-05
I installed the 64bit version of 7.10 and it works well. I am curious if there are any benefits to choosing the 64 to the 32bit system. I apologize if this is too simplistic of a question.

---

### Post by volanin on 2007-11-06
Just one important point:

As far as I know, the 64-bit version of Gutsy does *NOT* have a tickless kernel.
Just install powertop and check it for yourselves.
The kernel wakes up MANY times per second.

This will make your battery last much less than the 32-bit version.
So, if you are using a notebook, and care about battery life, I suggest installing the 32-bit version.

Can anyone re-confirm this for me?

---

### Post by karl_kashofer on 2007-11-06
Hi all !

I am asking myself the same question, as I plan to soon upgrade my macbook c2d to gutsy.

Here is my knowledge so far:

32 and 64 bit are equal in speed, which makes sense, having longer addressing registers will not have a huge impact on calculation speed.

With a 32 bit system you can address a maximum of 2^32 bit of ram, ie if you want more than 4GB you need 64 bit registers.

The first generation of Core duo computers has no 64 bit support, 64 bit started with Core2 duo.

So if you have any trouble with 64bit (flash, wlan, etc) and less than 4GB of RAM you can just go for 32 bit. 
If you use more than 4GB of RAM or are not bothered with the few limitations you still face with 64 bit go for that as it is the technology of the future.

Hope this helps,
Cheers,
Karl
P.S. I have 3GB of RAM in mine and will nevetheless go for 64 bit.

---

### Post by cyberdork33 on 2007-11-06
> **Rog-Mahal said:**
> I installed the 64bit version of 7.10 and it works well. I am curious if there are any benefits to choosing the 64 to the 32bit system. I apologize if this is too simplistic of a question.
[http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit](http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit)

Especially read the Pros and Cons section.

---

### Post by cyberdork33 on 2007-11-06
> **volanin said:**
> Can anyone re-confirm this for me?

Looks right to me.

[http://kerneltrap.org/node/11751](http://kerneltrap.org/node/11751)

---

### Post by michwill on 2007-11-08
> **cyberdork33 said:**
> Worked ok for me with VMWare. Doesn't make a difference. If the VM supports it, then yes, if not, no. I don't know that there is any advantage to using a 64-bit OS in a VM though.

The original question was with regard to a 64-bit host.  Not the guest OS.  Parallels doesn't currently run on 64-bit hosts.

Regards.

---

### Post by Rog-Mahal on 2007-11-10
is there any way I can modify my 64bit kernel to become tickless? I just finished installing it and I'd like to keep things as they are, but more battery life is always a plus. I only have 2 GB of RAM, so that shouldn't matter. Powertop recommends that I "Enable the CONFIG_NO_HZ kernel configuration option". How much battery life are we talking about anyway?

---

### Post by cyberdork33 on 2007-11-10
unless you are a kernel hacker, no. This will require a great bit of programming. They had to completely start over with certain parts of the kernel to get tickless kernel working, and they really don't want to do that again for x64.

Someone has submitted patches, but I would guess this is very experimental:
[http://kerneltrap.org/node/11751](http://kerneltrap.org/node/11751)

---

