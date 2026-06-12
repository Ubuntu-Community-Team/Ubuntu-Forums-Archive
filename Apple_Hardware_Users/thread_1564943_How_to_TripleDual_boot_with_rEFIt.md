---
title: "How to Triple/Dual boot with rEFIt"
date: 2010-08-31
forum: Apple Hardware Users
---

### Post by dngfng on 2010-08-31
As a lot of people seem to have issues with the existing guides and we  keep having questions about Dual/Triple booting. I have decided to type  up this short guide linking to useful external sources.
[B]
Getting Started[/B]
LifeHackers rEFIt Triple Boot Guide (OS X, Win, Lin)
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)
Yes its Triple boot guide all you have to do is skip the Windows part of the guide 
and you are down to dual booting easy enough. This will walk you through partitioning and installation of the OS(s).

**Getting Ubuntu to play nice with your Apple**
There are several ready made packages witch will depending on your Mac get most things working out of the box
with out to much hassle. 

To install these packages you will have to find the proper entry in Ubuntu's community documentation. Make sure
that you look at the right guide for your Mac's Version.

Running this command will identify your Mac's Version.
```
sudo dmidecode -s system-product-name
```Find the entry in Ubuntu's community documentation (link list is by no means complete, if yours is not listed just use
the search function).
> MacBook [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
MacBook Pro  [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Intel iMac [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)
Mac Mini [https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini)
Mac Pro [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)...and fall the instructions listed, also known issues will be listed here. 


Normally after completing all these steps you should be good to go.

**Known Issues**

However there are some known issues, witch keep popping up (you may not experience any of these).

*-heat/Fan *
On some Mac's the fan control does not work properly leading to overheating. 
Swedish wings has coded a daemon witch takes care of that and seems to be working pretty well.
[http://ubuntuforums.org/showpost.php?p=9778072&postcount=34](http://ubuntuforums.org/showpost.php?p=9778072&postcount=34)

*-no Sound*
for some reason also all channels are displayed as unmuted in the GUI they are not.
You will have to install alsamixer and run it from the terminal - there you will be able to unmute (by pressing "m")
all channels. 99% of the time this will solve your sound issues.

**Visual Guide**
For those of you preferring a Visual guide Michel66 pointed out the following you-tube video:
[http://www.youtube.com/watch?v=6SRKnWC3BDo](http://www.youtube.com/watch?v=6SRKnWC3BDo)

Please note that this guide is work in Progress. I will keep adding and amending it as time progresses.

---

### Post by Michel66 on 2010-09-02
Hi,

Did what is presented here without a glitch

[http://www.youtube.com/watch?v=6SRKnWC3BDo]("http://www.youtube.com/watch?v=6SRKnWC3BDo")

There is 3 more pts

---

### Post by vibe3 on 2010-09-16
When 10.04 came out, there were a lot of threads saying that the installer program put the grub2 in the wrong place and hosed the efi loader, making macbooks unbootable etc. I'm still running 9.10 because I'm scared to upgrade. Has that issue been fixed yet?

---

### Post by dngfng on 2010-09-17
Haven't notices anything to that effect - the guide that I followed even stated to put GRUB on the same Partition as Linux as rEFIt finds all Bootloaders on the device.

Had the stupid case that I installed Ubuntu twice and put the Bootloader once in the default Partition and the second time in Linux Partition - all that happend was that it showed 2 linux bootloaders for both enteries in rEFIt.

Under the line - I haven't had any problems other than self inflicted once.

---

