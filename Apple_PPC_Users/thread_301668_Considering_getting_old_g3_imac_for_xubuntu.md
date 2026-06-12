---
title: "Considering getting old g3 imac for xubuntu"
date: 2006-11-17
forum: Apple PPC Users
---

### Post by Tommerz on 2006-11-17
Hey everyone,

I'm considering getting an old g3 imac and running xubuntu on it. 

I'll need wireless support but otherwise there aren't many other needs I have besides the mac running and being stable :)

Do you think this would be a good idea? I've noticed lots of posts mentioning problems installing on the old imacs, are those exceptions to the norm or are there big problems with ubuntu and early imacs.

Any advice would be much appreciated, I'm considering getting it as a Christmas pressie. :)

---

### Post by stmiller on 2006-11-17
It's is somewhat of a more involved process to install on 'old world' macs. But it is easy on new world macs. I'm not sure if G3 iMacs are new world, or old. They are right on the time when that changed.

[https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)

So make sure it's new world machine, and Ubuntu will install fine on this machine. You can use USB wireless solutions for wireless. 

Lots of people use Linux on the G3 iBooks and have commented how great it runs.

---

### Post by markd1216 on 2006-11-17
Knowing what you're running on would be helpful.  I put Ubuntu on a 600 MHz (Graphite) iMac with 768 MB RAM and an 80 MB hard drive.  While my main system is still OS X on other newer Macs I thought I'd give Linux a try out of curiosity.  I still find OS X better from a consumer/user ease of operation but Linux is certainly  a nice change from the windoze at work. As with all systems these days RAM is all important.

Two things to consider if you try it.  After booting to the live CD you will probably end up with a black screen because of lack of video hardware support.  You will have to use some easy terminal commands and editing to get the monitor to work.  The second issue I had was very slow loading of web pages, which was overcome by reverting IPv6 to IPv4 -- something I knew nothing about but again got good information from the ubuntu forum site. 

There also seem to be many plugins that are not available for PPC so the total web experience is not available.

I am not particularly tech-savvy but if this is a spare computer and you are curious, give it a try.  Just back up the old Mac in case you want to revert. 

Mark

---

### Post by n_hendrick on 2006-11-17
I just bought a iMac G3 old world and am running Kubuntu 6.10 fine. Its a little laggy but you can almost double the memory for 15 bucks which I'm gonna do. The specs of this iMac are as follows:
600mhz
40gig
128ram
ati rage 128 pro 16ram
cdrw 25x
haron kardon sound system
15 inch monitor
I just got it off of [http://www.geeks.com](http://www.geeks.com) . It was only $104 dollars which surprised the hell out of me. The video driver was a little hard to setup. You'll need a linux distro you can run a command prompt from like gentoo or slackintosh as to mount root and edit xorg.conf. And the only way I could get it to install was by the alternate method (theres a whole other cd for ppc which does a text install only), but other than that I'm on a fully function Kubuntu terminal, pretty groovy. The boots kinda slow 76 secs and sometime I have to wait 10sec for a program to load but that should be remedied in a couple days since I already ordered the PC100 SDRAM for it. I'd say go for it....I've learned alot about macintosh and linux ppc since and I'm glad I bought it...:-D

---

### Post by oswaldkelso on 2006-11-17
All imacs are newworld. If its a tray loader 333mhz and under (if memory serves me right) I dont think you can get wifi, the ibooks use the apple airport card and you can only get it for slotloaders (350mhz > check when it was introduced ? because it may have been only from a certain processor only) 

You need at least 250mb ram, not an easy upgrade on tray loaders, easy on slot loaders. Tray loader can have a limit as low as 250mb max ram (some can go upto 500mb but it was luck of the draw if yours would take it). I think it was a 1gb limit on slot loaders.

I have owned both a 333mhz and 500mhz, and IMHO the 500 is a still useful
machine. Only go with a tray loader if its given to you!! My daughter now has the 333 (250mb) and its running edubuntu ok but it will never set the world alight, infact it can be painful on larger files. (slackintosh was alot faster with xfce). 

If you have to go for a tray loader or anything with less than 250mb ram use the alt cd.

---

### Post by ign on 2006-11-18
I'm posting this from a **bondi blue G3 233mhz, 192mb ram, 4G hard drive, Rev. B iMac (tray load)** i bought back in october 1998. Yesterday I installed Xubuntu Dapper 6.06.1 in it using the live CD and I'm happy to announce you that it works quite well, with some minor tweaking involving the blank screen problem (it's well documented in this formus) which is solved with minor changes in xorg.conf

I don't have a wifi card for this machine, so I can't tell you anything on that matter.

---

### Post by Tommerz on 2006-11-18
Awesome, thanks for the feedback!!

Now I just need to work out where the best place to buy one is :)

Does anyone have any ideas? I'm UK based, I've looked on ebay and they seem to be available there fairly regularly, does anyone know of any particularly good places to find them?

---

### Post by ixus_123 on 2006-11-18
you *should* be able to use usb wifi - just check the chipset.

Finding an Apple airport card is like finding golddust. They are rare & often get sold for more than a ne wexport extreme card on ebay!!

---

### Post by timbobsteve on 2006-11-19
I am running 6.10 Edgy on an ibook G3 900Mhz. I see no problems with Linux and the G3 processors. As mentioned before, make sure you track down a new-world mac... not because old-world is bad, but just cause it will be simpler for you in the long run.

Also a note on USB wireless. I did the same thing for my mac... unfortunately I am 2 different wireless cards in and still yet to find a card that support Linux-PPC. I have 2 cards that support Linux perfectly, but the drivers don't compile on PPC because of some architecture differences (endianness if you want to know)... this has been a major bummer for me, because OS X support one of the 2 cards, but linux-ppc supports none. I should note again, both cards are Linux supported... but not Linux-PPC. Make sure you know what card you are getting before you buy it and do some research for Linux-PPC compatability (I only looked for linux compatability and suffered because the drivers are not PPC).

Anyways... I say go for the old mac and bring it back to life with Ubuntu 6.10 it will run great.

---

### Post by samden on 2006-11-24
There are lots of great success stories here. An iMac G3 running linux seems to be a good idea. However getting it to run linux is not always as easy as it sounds. Most people seem to have had few issues with installing ubuntu, which is great. But I have an iMac G3 slot loader, 500Mhz that I have been trying to install linux on for two weeks now. I have tried so far:

Ubuntu 5.10, 6.06.1, 6.10 alternative install cds
Ubuntu 6.06.1 live cd
Xubuntu 6.06.1 live cd
Debian net install and business card cds
Fedora Core 6
Mandriva 2005

I still do not have a working linux system. I really want Xubuntu or Ubuntu 6.06.1, or Debian running on the computer. But it is more difficult than it sounds sometimes for a newbie.

Go ahead and try. It seems to work fine for most people. But don't spend too much money on the computer as there is always the possibility that it might not work as easily as you think...

P.S. If anyone wants to look at [http://www.ubuntuforums.org/showthread.php?t=300122](http://www.ubuntuforums.org/showthread.php?t=300122) and see if they might be able to help solve my problems I would be grateful! I have had lots of support so far, which I am very grateful for, but haven't been able to get to the heart of the matter - why none of the distros appear to install, and seem to crash half way through installing the base system.

---

