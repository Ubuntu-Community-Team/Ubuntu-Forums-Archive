---
title: "No ubuntu"
date: 2012-04-24
forum: Apple Hardware Users
---

### Post by ferrenm on 2012-04-24
MacBook Pro 5.1; Intelmac; Time Capsule (hourly backups, and a good thing too!); OS X 10.6.8; 250 GB hard disk partitioned as 150 GB for Snow Leopard, 125 used, 25 free, and 100 GB MS-DOS (FAT32), empty; rEFIt; ubuntu-12.04-beta2-desktop-amd64+mac. 

Convert latter from .iso to .dmg/.img per instructions. Burn to CD per instructions. Copy to USB stick per instructions. Do that again later to another USB stick.

Net result: one laconic penguin shows up in rEFIt. The only thing he ever says is 'Boot error'. Other than that, one CD and 2 USB sticks that cannot be recognized, read, erased, repaired, or reformatted by anything in my system or available for trial on the web.

Much the same happened when I tried with earlier versions. I live in the south of France, in a village where Blackberries are the high tech of the elite and the web chugs along at 50 kb/s. Nearest Mac guru is a 50-km drive, and me with a bicycle. I read French, but conversation with the Occitan-speaking natives does not work well.

I may have had an actual Ubuntu desktop show up for about 10 minutes once, but I wasn't expecting it, didn't recognize it for what it was (thinking it just another web-page demo). If it was real, it hasn't been back.

I guess my question is, if I get 5 CDs for $5, might one of them work on a Mac? (If 'Yes', could I ask, 'Is that an article of faith, or have you actually seen it happen?' Are any of the CDs in Mac-readable .dmg format? 5 .isos aren't much help!

[Web-page glitch: I'm not allowed to create tags. Must use existing tags. No discernible way to discover what tags exist.]

---

### Post by Curtis6767 on 2012-04-24
Did you verify your disc?

[http://ubuntu.osuosl.org/releases//precise/MD5SUMS](http://ubuntu.osuosl.org/releases//precise/MD5SUMS)

How to do the checksum:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by audiomick on 2012-04-24
Did you know that there is a dedicated subforum for macs?

[http://ubuntuforums.org/forumdisplay.php?f=328]("http://ubuntuforums.org/forumdisplay.php?f=328")

I think you might have more luck there with your questions. I am not sure, but if you use the "report abuse" button on the left of your post and ask politely, a moderator might move the thread over there for you.


As far as tags go, I assume you mean the ones like this
[tag][/tag] for formatting and stuff in a post? I believe the ones here will all work on this forum.

[http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by strask on 2012-04-24
> **ferrenm said:**
> Convert latter from .iso to .dmg/.img per instructions. Burn to CD per instructions. Copy to USB stick per instructions.
Which instructions are you following, can you provide a link? That might help us figure out what's going wrong.

> [Web-page glitch: I'm not allowed to create tags. Must use existing tags. No discernible way to discover what tags exist.]
I think if you start typing a tag, one character at a time, it will provide a drop-down list of existing tags that match what you typed so far. Works for me, anyway.

---

### Post by audiomick on 2012-04-24
> **strask said:**
> 
I think if you start typing a tag, one character at a time, it will provide a drop-down list of existing tags that match what you typed so far. Works for me, anyway.

Hmm, never seen that.

The tag for a link is

[noparse] [ ]( ) [/noparse]

to make it like this

[ http://ubuntuforums.org/showthread.php?p=11870427#post11870427 ]( http://ubuntuforums.org/showthread.php?p=11870427#post11870427 )

---

### Post by strask on 2012-04-24
> **audiomick said:**
> Hmm, never seen that.

The tag for a link is
Yeah, I think the OP is talking about thread tags, that show up on the list of threads to help identify the topic of conversation. So this thread might have tags like mac, install, .iso, etc. They are labels, not markup. There is an option to enter up to five of them when you create a post, down below the main text entry box.

---

### Post by strask on 2012-04-24
I found this information that may explain troubles you are having with usb-boot: [http://refit.sourceforge.net/help/usb_disk.html](http://refit.sourceforge.net/help/usb_disk.html)

---

### Post by ferrenm on 2012-04-24
> **ferrenm said:**
> MacBook Pro 5.1; Intelmac; Time Capsule (hourly backups, and a good thing too!); OS X 10.6.8; 250 GB hard disk partitioned as 150 GB for Snow Leopard, 125 used, 25 free, and 100 GB MS-DOS (FAT32), empty; rEFIt; ubuntu-12.04-beta2-desktop-amd64+mac. 

Convert latter from .iso to .dmg/.img per instructions. Burn to CD per instructions. Copy to USB stick per instructions. Do that again later to another USB stick.

Net result: one laconic penguin shows up in rEFIt. The only thing he ever says is 'Boot error'. Other than that, one CD and 2 USB sticks that cannot be recognized, read, erased, repaired, or reformatted by anything in my system or available for trial on the web.

Much the same happened when I tried with earlier versions. I live in the south of France, in a village where Blackberries are the high tech of the elite and the web chugs along at 50 kb/s. Nearest Mac guru is a 50-km drive, and me with a bicycle. I read French, but conversation with the Occitan-speaking natives does not work well.

I may have had an actual Ubuntu desktop show up for about 10 minutes once, but I wasn't expecting it, didn't recognize it for what it was (thinking it just another web-page demo). If it was real, it hasn't been back.

I guess my question is, if I get 5 CDs for $5, might one of them work on a Mac? (If 'Yes', could I ask, 'Is that an article of faith, or have you actually seen it happen?' Are any of the CDs in Mac-readable .dmg format? 5 .isos aren't much help!

[Web-page glitch: I'm not allowed to create tags. Must use existing tags. No discernible way to discover what tags exist.]
Strask was right about 'tags'. And probably also about Apple trying to boot from USB. 

As for Curtis6767's suggestion about verification, Terminal did a hash for the download of 12.04-beta2-desktop-amd+mac, and it reads 7c72fc1fe8f051d05c4466028fa4608d
but the hash page tells me about heron and lynx and meerkat and narwhal and ocelot, but knows nothing about pangolin. (Odd, I seem able to remember the animals but not the adjectives. Sorry.) Can't read the disc, so there's no way to verify it.
As to which instructions--i've wandered all over the Ubuntu pages this last month, trying everything I came across that looked relevant. Macs don't read .iso, so the Mac pages say to use use Disk Utility to make a .dmg/.img disk image, which it claimed to have done. 
Thanks for the help: I'll try to move this thread over to the Mac world.

---

### Post by oldos2er on 2012-04-24
Thread moved to Apple Users.

---

