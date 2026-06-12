---
title: "compatibility questions"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by shadows123 on 2007-08-16
Ok i really want to be sure before downloading, that i can run it :P
as i got a limit of download / month :(

so,
firstly is it only available to 64 bits?
i was a bit confused with what it said...
well my pc can't run 64 bits...
and, regarding the booting,
now i currently have windows XP, if i would install ubuntu on another partition would i have to do some stuff to get the booting working or will it work directly? :)

edit : what about wireless usb internet?

Thanks a lot for your support!
- Shadows123

---

### Post by amazingtaters on 2007-08-16
1. There is a 32bit version of fiesty. Just choose the standard option from the download page.
2. If you boot with the live cd it will change absolutely nothing on your hard drive. Thus you can test drive Ubuntu to see if you like it. Note that it will probably run slower via live cd than an install, so don't judge speed based on the live cd.
3. When you intall ubuntu GRUB will be installed and grub can easilly handle booting Windows. I dual booted with Vista for several months until going pure Ubuntu.
4. Wireless USB internet will work, though you will probably have to install divers. There's plenty of guides on the forums.

---

### Post by Arthur Archnix on 2007-08-16
> **shadows123 said:**
> Ok i really want to be sure before downloading, that i can run it :P
as i got a limit of download / month :(

so,
firstly is it only available to 64 bits?
i was a bit confused with what it said...
well my pc can't run 64 bits...
and, regarding the booting,
now i currently have windows XP, if i would install ubuntu on another partition would i have to do some stuff to get the booting working or will it work directly? :)

edit : what about wireless usb internet?

Thanks a lot for your support!
- Shadows123

I'm going to assume you're talking about Ubuntu. In which case, no, there is also a 32 bit version. Yes, in Windows is already installed when Ubuntu is installed a new bootloader called Grub will be written to your MBR and let you choose whether to start windows or ubuntu. 

Wireless depends on your card, very many are currently supported, but you should check out whether your hardware is [supported]("http://www.google.ca/search?q=linux+hardware+compatibility&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").  USB... well, I've never heard of any problems at all. Internet, depends on whether you have a LAN or just wireless, in which case check out the link above first.

---

### Post by shadows123 on 2007-08-16
ok well i'll download it some time later :)
thanks a lot for answering the questions :)
ubuntu looks good enough to me :D

---

### Post by amazingtaters on 2007-08-16
Definitely give it a try, at least via the live cd. It's a very good OS.

---

### Post by shadows123 on 2007-08-16
hmm
i've been on several site's and it showed me compatible usb wireless ones..
and i didn't find mine :(
it's a topcom one.. :(

---

### Post by bobplano on 2007-08-16
there's also a 32bit version [here]("http://www.ubuntu.com/getubuntu/download"). just make sure it says standard personal computer. you could also get it shipped ([https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/"))
 
for the installing you will want to defrag your windows partition. choose the manual partition thing and make your windows partition smaller.  then make an ext3 partition mounted to "/"(at least 4 gigabytes) and a linux-swap partiton that is at least 25 megabytes, preferably bigger. grub, a bootloader should allow you to boot to both windows and ubuntu. it automatically installs so you shouldn't have to worry about that. wireless is a bit iffy so post your wireless card here

edit: wow talk about late. this forum goes so fast

---

### Post by shadows123 on 2007-08-16
my topcom's usb is 
it says lol :
Topcom
Skyr@cer Wireless USB Stick 11b V.2

edit : and what's this ? i'm kinda confused why do i need this? lol
 linux-swap partiton that is at least 25 megabytes, preferably bigger

indeed i'm a beginner XD

---

### Post by ugm6hr on 2007-08-16
Swap: see the answers here [http://ubuntuforums.org/showthread.php?t=527224](http://ubuntuforums.org/showthread.php?t=527224)

As for your USB wifi - you will need to use *ndiswrapper* - you will not be able to check if it works until after you have installed Ubuntu....  Just ask for advice again when you get to that step.

This [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/) suggests that it should work...

---

### Post by tango_ninja on 2007-08-16
@shadows 123

if you're concerned about exceeding bandwidth to download the system install cd, many can be ordered for free (you just pay the shipping, and sometimes it's completely free :)  )

ubuntu 7.04 feisty fawn -[https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

kubuntu 7.04 [http://kubuntu.com/shops.php]("http://kubuntu.com/shops.php")

i installed kubuntu only a few days ago and discovered that there were quite a few updates to download afterward, so take this into account as well.

best of luck

---

### Post by shadows123 on 2007-08-16
hmm.. i have found this :
Card: Topcom Wireless USB Stick 54 Mbps - V2
Chipset: SiS163u
usbid: 0d8e:0163
Driver: Tested with different versions of the sis163u.sys driver.
Other: Kernel: 2.6.13-gentoo-r3 (Genkernel generated, 4k_stack, SMP & Preempt disabled) Ndiswrapper 1.15: I had to replace the Gentoo net.wlan0 rc-script with my own modified version, because with the original, only version v1.05 of the sis163u driver works and it has some association problems. remark: USB stick connected to USB 1.1 port.

buut.. it will be slower??
mine is 11 b and that one 54 mbps??
hmm...

oh and, lol yeah i can handle it... if i download it at night, it counts 50%off my bandwidth :D

---

### Post by amazingtaters on 2007-08-16
You'll be fine as far as bandwidth goes using ndiswrapper to get your wireless working. All ndiswrapper does is allow your windows wireless drivers to work in linux, more or less.

---

### Post by shadows123 on 2007-08-16
so actually i download that ndiswrapper and then, my windows driver? lol as my driver isn't in that list.. 
or do i need to download their driver versions?

lol i'm sorry i ask a lot of questions but i really don't know a lot about ubuntu :P

---

### Post by ugm6hr on 2007-08-16
This might help explain everything:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

And it's best to just use the Windows 98/2000/XP driver for your USB wifi card - it may well work.

---

### Post by shadows123 on 2007-08-16
omg thanks..
hmm oohh my last question.. :P

edit : stil have another one i see :P
Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.
i don't relaly get it :P

what is the most RECOMMENDED space for a the swap partition?

Thanks..
there sure are a lot of people helping each other :)

---

### Post by ugm6hr on 2007-08-16
The LiveCD allows you to try Ubuntu out before installing - it boots direct from the CD, and runs (albeit slowly).  You can then install from there, which leads you through things from within the Graphical Desktop.

However, the AlternateCD supports more hardware, but installs using a "text-based" user interface - the same as installing Windows.

As for swap size - the easiest thing is to allow Ubuntu to decide for you.  But, generally speaking, 2x RAM up to a maximum of about 1GB is about right for most people.

---

### Post by amazingtaters on 2007-08-16
Recommended size for your swap partition is twice the size of your RAM, or at least make it equal to the amount of ram you have, unless you've got a lot of ram. I have a gig of ram, so making my swap partition two gigs didn't make much sense, but if I had less ram it would be a better idea to have double the size of my RAM.

---

### Post by shadows123 on 2007-08-16
nice thanks a lot guys :)
i have a gig rams,
i'll put 4 gb then.. if it's bigger i suppose it'll be faster :P and i have enough space so.. :)
and i think i'll use livecd so i'm sure i like it hehe :P

edit : can you mount a linux-swap partition? if yes to what should i mount it?

Thanks..

---

### Post by ugm6hr on 2007-08-16
> **shadows123 said:**
> 
i have a gig rams,
i'll put 4 gb then.. if it's bigger i suppose it'll be faster :P 

Not strictly true.  

I'm no expert, but there are apparently some arguments for not making it too big.  I don't think you'll gain anything from making it any bigger than 1 GB-ish.

But don't take my word for it - do a bit of googling to investigate.

---

### Post by shadows123 on 2007-08-17
i see ...
thanks .. lol
btw i had start it today with live cd :P omg it's beautifull lol :P,
i will install it later today... :P

oh, and does ubuntu have a rar extracter installed in default?
Thanks..

---

### Post by ugm6hr on 2007-08-17
> **shadows123 said:**
> oh, and does ubuntu have a rar extracter installed in default?


I think you can install *unrar* and *p7zip* from Synaptic package Manager to give better compressed file handling.

---

### Post by shadows123 on 2007-08-17
ok thanks a lot :)
i'm going to install it right now :P

---

