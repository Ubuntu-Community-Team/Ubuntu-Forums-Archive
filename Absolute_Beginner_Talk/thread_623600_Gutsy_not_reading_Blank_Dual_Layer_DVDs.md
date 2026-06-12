---
title: "Gutsy not reading Blank Dual Layer DVDs"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by MystaMax on 2007-11-26
I haven't had the need to burn a Dual Layer DVD in ubuntu, until now. I have a [Pioneer DVR-107BK]("http://www.pioneerelectronics.com/pna/v3/pg/support/details/0,,2076_310070215_83265402,00.html"), and can successfully write to DVD+R & CD-R. Ubuntu will not even recognize the blank Dual Layer DVD+R media .

Memorex CD-R's = WORK
Single Layer Memorex DVD+R = WORK
Verbatim Dual Layer DVD+R = DOES NOT WORK

I also ran this test on my laptop, running Ubuntu Gutsy. My laptop was unable to read the Blank Dual Layer DVD media as well. What gives? After searching the forums, I see that others were having a problem, but not many resolutions.

CD-R's and DVD+R's automatically get recognized as Blank media, but nothing for Dual Layers. I'm trying to use Nero Linux to burn a 7.2 GB ISO

IMO, this is a really weird problem for Ubuntu to have. I'm not even sure how to begin troubleshooting this. Any insight or ideas?

---

### Post by tesserhex on 2007-11-26
Hi,

May be a little obtuse here, but according to the specifications on the link, the device (DVR-107D) doesn't write dual layer discs? Only reads them. Just curious if this is the right link?

Specifications:
Write Support DVD-R (4.7 GB for General disc only), DVD-RW, +R, +RW 
CD-R, CD-RW
 
No mention of Dual Layer Support for writing purposes.
....

---

### Post by MystaMax on 2007-11-26
Thanks for the reply.

The specs on that link are incorrect, I have no problems burning Dual Layer DVDs with Nero in Windows XP. Its worked for me the last 3 years. I just haven't tried it in Ubuntu. 

Also, I'm having the same **exact **problem on a Dell Latitude D620. It won't recognize Blank Dual Layer DVDs either, and I know that can burn DL DVDs, as I do it in Windows.

---

### Post by tesserhex on 2007-11-26
OK. 

What application will you use for burning the dual layer DVDs in Ubuntu? If you are using K3b you can go to Settings>ConfigureK3B and look in the Devices section. Your drive should say something like:-

Writes DVD-R Dual Layer and have either Yes or No.

Failing this, have a look in the Advanced tab of Device Manager (in System Preferences>Hardware Information) for your device and see if it's reporting the capabilities correctly.

You could also check to see if there's an updated firmware for you DVD drive that might tighten up any loosely identified issues.

Post back any details from K3B or Device Manager...

---

### Post by MystaMax on 2007-11-27
I'm using Nero Linux to burn DVDs. I don't have K3b installed, so I went to Device Manager to find out more.

I found my DVD Drive in the device manager, and took a look at the advanced properties. Here are some results:

storage.cdrom.dvd = true
storage.cdrom.dvdplusr = true
[B]storage.cdrom.dvdplusrdl = false
[/B]storage.cdrom.dvdplusrw = true
storage.cdrom.dvdplusrwdl = false

The above info proved very valuable. Thanks for the lead. *I wonder why it defaults to false?* It also lets me change the value from false to true, but I haven't done it yet. I'd like to know what others think about changing this boolean expression from false to true. *Is there a possibility that I could damage my drive?* I'll probably try it on my work laptop (Dell D620 having the same problem) first. I'll be extremely happy if this is all I have to do.

I also found a firmware update @ the [Pioneer DVR-107BK website]("http://www.pioneerelectronics.com/pna/v3/pg/support/details/0,,2076_310070215_83265402,00.html"). I'll have to go into windows to perform the firmware check and update. I'll probably do this first.

Let me know what you think, and thanks for the help so far. :)

---

### Post by MystaMax on 2007-11-27
Ok, I tried to changing the boolean for storage.cdrom.dvdplusrdl on my Dell laptop in device manager, but it kept reverting back to its default. So no luck w/ changing it.

I'll be updating the firmware on the drive tonight, but I doubt that helps. This is just not cool, that ubuntu won't recognize these DVD+DLs.

I'd like to know if anyone has DVD+DL working properly?

---

### Post by crjackson on 2007-11-27
Unless your DVR-107 is radically different than mine it will never burn DL discs.

Here is a screen shot using Nero Windows - 

My DVR-112L burns DL DVD's under Ubuntu just fine using both K3b and Nero Linux 3

---

