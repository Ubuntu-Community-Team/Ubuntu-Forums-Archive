---
title: "ubuntu good on some bad on others"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by noshutdown on 2007-12-26
I installed ubuntu on my 5 year old home built p4 2.8 GHz Prescott computer with an Asus board 865pe chipset, nvidia geforce video card, and ocz cas2 ddr ram  2gigs, and a wd raptor HD. Install went fine. I had WinXp Pro installed on drive C and a  D drive for storage, I used the manual install to utilize the partition resizer. I resized my partitions and everything went well. Next I installed mandrake 10.1 and then SuSe 10.3 just for comparison purposes. Everything is still good. Ubuntu is great, Mandrake is ok...just a little trickier to use and I think Suse is just like Ubuntu except that Suse wants to take over the Linux bootloader. i worked it out and Ubuntu is working beautifully. I have quadruple boot system now.Xp corp, ubuntu, mandrake and suse.
 
Next after much persuasion, I talked a friend into trying the ubuntu live disk on a similar system that I built for him. When he saw that he could access his windows parttions from Linux he liked it. When I showed him that he could use ubuntu linux's irc clients and ftp clients to download and upload to his windows archives, he started to like it very much! The only complaint I got was that he couldn't install flash player to opera browser. I believe it has something to do with PATH:s and ./Hidden directories and ./files. I haven't worked that out yet because I am very new to linux...well I admit it I'm a NUBE when it comes to doing things in linux from the command line editors.

Now I'm really hyped about Linux Ubuntu ver 7.10. I tried it on someone  else's quite old Amd Durion 1033 MHz processor system and could not get the live disk to startup.All I got was lines of text with basically numbers and the word HUH? scrolling across the screen. I thought that maybe it was because it was over clocked but the dude didn't want me to mess with his system any more . That was that.
Then I tried ubuntu 7.10 live disk on a brand HP Laptop with Amd Turion dual core, 3 gigs of ddr2 ram and 120 gig ibm drive. The same thing happened it looked like it was going to run the live disk and I got about 70 lines text scrolling very slowly with the same message as last machine. some numbers the the word huh? with the ? after huh and then more numbers and and some text.

Whats up dosen't Ubuntu like AMD Processors or is it just that the HP  laptop was to new and propriatry or is ubuntu having problems vista certified systems? And as for the old Durion, whats up with that? Ubuntu should know about every device and driver in that system.

Thanks

noshutdown

---

### Post by Samhain13 on 2007-12-26
I wouldn't say the Ubuntu doesn't like AMD Processors because it installed well and runs fine in the computer I'm using. I have an AMD Sempron 2400. But then, I can't account for the others.

---

### Post by Hospadar on 2007-12-26
well I doubt it's the CPU, it's most likely some other part of the hardware (no Idea which).  do you know at all what errors you got?  have you tried any other distros on those machines?

---

### Post by LaRoza on 2007-12-26
For Opera: Get the Opera 9.5b release, it works with Flash fine (using it now). It is beta, but no major problems are apparent.

For AMD, there are many issues that can arise, and the processor is rarely the issue. It is likely the bios or motherboard. Most problems can be fixed. If you post the error messages, help will be easier. The video card can be a problem too, especially if it is ATI.

---

### Post by RomeReactor on 2007-12-26
Hi, welcome to the forums.

The problem with Opera and Flash is that the stable version of Opera (9.25 at the time of this writing) has trouble detecting the Flash plugin downloaded from Adobe's website; to make matters worse, the flashplugin-nonfree package in the repositories has a bug which makes Flash invisible to both Opera and Firefox; the solution at the moment--for Opera--is to use the [latest Beta version]("http://www.opera.com/download/linux/?ver=9.50b"); if you downloaded Flash from adobe's website, then Opera should be able to recognize the plugin; if you installed the package from the repositories, you need to install [a corrected version]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb") which should be available in the repositories soon. More on installing Flash for Opera [here]("http://ubuntuforums.org/showthread.php?t=644075").

As for installing Ubuntu on computers with AMD processors, I have to say that both my PCs have AMD chips--one a 1.6 Ghz Sempron, and the other an 800 Mhz Duron--and I haven't come across any problems directly related to them; the PC with the Duron has 256 MB of RAM, so I have to perform the installation using the Alternate CD ([direct link]("http://mirrors.xmission.com/ubuntu-cd/7.10/ubuntu-7.10-alternate-i386.iso"), [BitTorrent]("http://mirrors.xmission.com/ubuntu-cd/7.10/ubuntu-7.10-alternate-i386.iso.torrent")), but other than that it runs very decently. Maybe there are certain components in the PCs you couldn't get Ubuntu installed on, such as the video card (always a factor) or a wireless device. Make sure the system has at least 256 MB of RAM to install using the Live CD, and even in some cases that isn't enough, as is the case with my Duron system.

So, in short, my recommendation is give the Alternate CD a try.

EDIT: Too slow...

---

### Post by bobpur on 2007-12-26
In my opinion, linux likes AMD just fine. I've used it on Athlons and Durons, single and dual cores, high-end and bargain boxes.
I believe the problem you are experiencing is a video problem. Even on newer machines you might try using the "vesa" driver option.
One of my machines with a 5600+ AMD x2 in a socket am2 Asus mobo with an XFX 7600 GT video card will not boot unless the "vesa" option is used.

---

### Post by Tux.Ice on 2007-12-26
Ubuntu will install on x86 processors made by both Intel and AMD.

---

### Post by Tux.Ice on 2007-12-26
i cant believe nobody figured that out-wow

---

### Post by LowSky on 2007-12-26
> **Tux.Ice said:**
> it because theres a different version of ubuntu for intel processecors and a different version for amd processors

the version for amd is called the x64 version

You are absolutely WRONG!!!

x86 is for processors that can handle 32bit computing, which was standardized by intel, but works fine on all AMDs. Trust me I'm using it on an AMD and intel machines.

AMD64 is the standardization for 64bit level computing. And it works fine on all AMD Athlon64 and Intel 64 chips.


So please dont post lies.

---

### Post by LaRoza on 2007-12-26
Error fixed, so I deleted this.

---

### Post by Martin Witte on 2007-12-26
this looks similar to issues reported in this thread, [http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115), so maybe you have an issue with an usb device

---

### Post by jan quark on 2007-12-26
I know what you mean. I have encountered the same problems with Ubuntu:
Long lines with huh? It seems to be either a problem with the burned .iso cd/dvd or some hardware issue. Don't figured out yet. But I get this error message when I try to install Xubuntu 7.10 from my DVD+RW. No error messages with a "normal" CD-R, whatsoever. 
You are not alone.:lolflag:

---

### Post by Tux.Ice on 2007-12-26
whoops seriously i did not know that i thought x86 worked only on intel and x64 worked onl on amd

srry---
im stil mostly a noob
forgive me

---

### Post by LaRoza on 2007-12-26
> **Tux.Ice said:**
> whoops seriously i did not know that i thought x86 worked only on intel and x64 worked onl on amd

srry---
im stil mostly a noob
forgive me

The naming scheme is confusing, isn't it?

---

### Post by Niniel on 2007-12-26
> **jan quark said:**
> I know what you mean. I have encountered the same problems with Ubuntu:
Long lines with huh? It seems to be either a problem with the burned .iso cd/dvd or some hardware issue. Don't figured out yet. But I get this error message when I try to install Xubuntu 7.10 from my DVD+RW. No error messages with a "normal" CD-R, whatsoever. 
You are not alone.:lolflag:

I can second that! Some optical drives seem to be a problem. I installed Ubuntu 7.10 successfully from an alternative install CD-RW on a machine with a Memorex DVD-RW (2 x Athlon 1500), but when I tried putting it on my Dell box (P4, not sure who made the DVD-ROM), the installation ended with an error when the software was to be installed. Grub install failed as well. Yet when I check the CD in the Memorex drive it's reported to be error free. 
What a weird problem. Maybe burning the ISO to a regular CD-R will help, or I'll just try to fix Grub and then go from there. 
But anyway, in this case it was clearly the combination of optical drive+ media that proved fatal.

---

### Post by noshutdown on 2007-12-26
Thanks for the responses LaRoza and RomeReactor  and everyone else.
I  haven't tried any of the fixes for opera and flash yet, I'll get around to it.

As far as the install errors on Amd boxes I think that the reason is, is that the old duron which is supposed to run at 1033 is only running at 850 Mhz is Something to do with his ram but I'm not sure it's been a long time since I put that system together. I know that the multiplier,bus speed  and memory speed are all adjustable. i just forgot how to set the bus speed and mem speeds and multpliers for that particular cpu and chipset. If I go into the cmos setup utility, I can set it to auto on everything then the system runs at 850mhz- 8.5 multiplier, 100 bus and 100 memory bus. If set it at 8.5 x 133 mhz which is the speed of the sdram, i get 1033 on bootup and windows runs fine but I have that problem installing the Ubuntu Live cd. If I set the memory to SPD it posts at 850 Mhz. I just can't remember and of course he lost the mother board manual. So I just left it at 850 Mhz since I didn't want get blamed for something that he did and I would have to go  back there and fix what ever got messed up. 
in one of the posts someone said that he had to get an alternate disk for an amd system with an AMD 800MHz processor. Also the duron sytem does have an old ATI all-in-wonder card, that may be a factor as well. 
The HP semparon amd 2 system has an Nvidia  video chip of couse it is  wireless has a camera and card slots and a light-scribe drive as well  lots of other goodies or badies depending on how you look at it. All I know is that for a brand new Laptop with all the bells and whistles vista home premium does not impress me much at all and the system does have problems every now and again. That's why wanted to show him ubuntu! I built Ubuntu up as greatest OS since sliced bread and that the transition from a novice  windows user to ubuntu will be easy for these knuckle heads that really can't do anything on a computer but browse and email and listen to music and watch movies. All I know is that I felt a little fooliish after the big ubuntu sales pitch i had go through just to get them to try it and I couldn't get Ubuntu installed on either Amd system.

I don't know how to take a screen shot in ubuntu while it's trying to install and I cant pause it either like in micro$oft when it boots.
all I can remember for the errors are this:
it would go thru the devices such as drives and usb and core drivers with a  number 27122066 bind huh? and then some hexadecimal or BCD coded address after each line. The numbers would pretty much go up in succession ie. 27022001, 27022002, etc. The computer would start very slowly going through the tables one by one and usually say failed at the very end of the line some things would pass. 
The same basic thing happened on the HP vista home premium laptop with the AMD core 2 Semparon 
a fairly new system built maybe 3 months ago or so.

Thanks for your help everybody- BTW i'm not exactly a newbie to linux. my first attempt was redhat 5.0 which was night mare for me about ten years ago, then I tried redhat 5.5  where I was at least able to get x-windows to work, then KDE and GNOME and the network card installed, never was able to get get the sound drivers going though. Then my next atempt at linux was slackware 7.1 which I can't use on my system for some reason, probably because slackware 7.1 doesnt know about hyper threaded cpus and, well I guess my five year going on six year old system is to new for slackware 7.1. To bad because I wanted to use cfdisk to partition with. Im sure I can get that application to work on ubuntu somehow. I just need to apply myself a little more and learn all of the commands and how to navigate the paths via command line. I know that linux is multi process operating system and I can pipe a commmand to another command and run commands behind commands with &&. Now that everything is gui and auto install and very windows like it will much easier for me  to advance in Linux. 
I have 3 old books on linux that from the old red hat distros and one later book printed in 2001. Most of the information  is obsolete but i know the commands and command line syntax hasn't changed that much...I think???


noshutdown

---

