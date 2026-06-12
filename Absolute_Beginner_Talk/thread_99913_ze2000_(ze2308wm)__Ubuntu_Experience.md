---
title: "ze2000 (ze2308wm)  Ubuntu Experience"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by JackDog on 2005-12-06
Over the Thanksgiving break, I splurged $368 for one of those HP notebooks from Walmart, yeah I was there at 4am.  I thought I would post here what my experiences were with Ubuntu so that others may benefit. I have used linux for over 10 years but rarely have used a debian based distro (usually source based distros). I put suse10 on it since it Just Worked (tm) but decided to give ubuntu a shot.

[B][SIZE=4]
[COLOR=Blue]ze2000 (ze2308wm) [/COLOR][/SIZE][/B][SIZE=4][SIZE=1]
This laptop series of HP comes with a variety of hardware from Intel Chips to AMDs, from nvidia to ati.  This is a very hacked down laptop which is exactly what I wanted. Just a laptop to take on the road for photos, videos and music. Now that I have the RAM upgraded, I can use it for development (Java). Battery lasts about 90 minutes with continuous web use.  Not sure about the durability, only time will tell ;)[/SIZE][/SIZE]
[B]

Sempron 2800[/B] - not sure if this is 64b enabled, need to find out though. The powernow module seems to think it is - "Found 1 AMD Athlon 64 / Opteron processors"
**40G Drive** - worka but not very fast.  $138 would get me a 7200rpm drive with 8mb of cache. Ill put that on my xmas list. 
**802.11g/b** - bcm4318 works perfectly via ndis wrapper. I have seen it confused on a couple occasions where a Router supposedly had WEP enabled when it didnt. But that may have just been the network applet in gnome. The iw tools saw it correctly.
**256MB **- Has two slots (piggy back). I spent $108 and upgraded to 1.25GB. Huge improvement in terms of performance.
**15" XGA display** - 4:3. Display is lower grade, but gets the job done at 1024x768. I actually prefer 1024x768 to 1400x1050 which is what my old laptop had. 
**USB/Bluetooth** - One of the ports detected claims its "version 2.00" and speed "480". I guess that means its USB2. I saw nothing in the package or ad that said it came with bluetooth, but it appears to have it that as well. 
**CDRW/DVD** - Works great. Burns CDs at 24x. No coasters yet. Also plays DVDs just fine.
**Power Management** - AC detection, battery usage work  perfectly. Doesnt seem switch management schemes though like SUSE10 did. I need to figure out how to do that with Ubuntu.  This is the first time I have ever seen power management actually work with a laptop. 
**ATI 200M (RS480)** - Unfortunately this is the only piece of hardware that does not work. Granted I have not tried very hard. Not even vesa will work since I believe the kernel is trying to use the radeon fbdev. I am still working on fglrx.


The install was a major pita. 

First off,  the fb would not start because it was using a mode that the video card does not like. No install screen, no consoles. The display was completely locked up. I had to try a couple modes before I got one to work. I ended up having to use 1024x768-60 at 16b to get the install going. Everything went fine until Ubuntu autodected my ati card and once again I was cast into darkness with no screen and no virtual consoles. Using the Recovery Mode, I was able to boot to a command line and alter the xconfig to get the fb driver working for X. Vesa or ati refused to work in any mode. I always got the same error "No valid screens found". Still need to figure out the video issues but fbdev is running fine in the meantime. 

Secondly, getting the wirless driver onto the laptop was a pain. But that is mainly because the network I was using during the install is wireless only. Not Ubuntu's fault, but it was a pain to find a wireline connection so I could get the inf and sys files onto the system. Once there were in place, ndiswrapper picked them up and enabled the wlam0 interface.

Once those two issues were taken care of, I just had to do the usual tedious tasks of installing mp3, dvd and divx support and configuring the system to my liking.



Buying this laptop has completely changed my opinions on laptop purchasing.  From now on I will buy the cheapest (name brand), most expandable laptop available and upgrade it with my own parts. As long as the proc speed is good, you are happy with the display quality and it has two RAM slots, you can build a kickass laptop system for less than $700. When its all said and done, I will have laptop containing a 7200rpm, 60G drive and 2GB of RAM for ~$720. Of course different people have different needs, but I think for the average user, this is the way to go. The only thing I wish this laptop has was an nvidia card. But its hard to complain for when you get a laptop for $368. I almost wonder if Ubuntu should blacklist ATIs and force the user to choose an fb mode. My Old 9500Pro had similar problems. 

Hope this helps someone.  Is there a better place to post the linux-laptop-device information? If anyone needs more detailed device info or help, dont hesitate to ask.

---

### Post by Buelldozer on 2005-12-06
Hi,

Could you tell me what version of NDISWRAPPER and more important WHAT DRIVER you are loading?

I have basically the same laptop, with the same BC card in it and I'm having a helluva time getting it to work.

I've tried every version of ndiswrapper from 1.1 through 1.7rc1 along with every driver I can find and nothing works. I've even tried the linuxant stuff and no joy.

I can't even seem to make the little wireless button stay on reliably.

The main difference between your rig and mine is that mine has a Turion64.

Heeeeelllllppppp!

---

### Post by JackDog on 2005-12-08
[quote=Buelldozer]
Could you tell me what version of NDISWRAPPER and more important WHAT DRIVER you are loading?
[/quote]

I am using the ndiswrapper that ships with breezy. 1.1-4 I believe. 

The driver files are bcmwl5.inf and bcmwl5.sys

---

