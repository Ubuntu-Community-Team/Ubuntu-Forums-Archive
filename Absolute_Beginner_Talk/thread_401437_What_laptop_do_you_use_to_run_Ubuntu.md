---
title: "What laptop do you use to run Ubuntu?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Fob on 2007-04-04
I'm a newbie to Ubuntu. I'm a student, and I want to run OpenOffice and GIMP along with some other, widely available linux programs. I need a laptop for portability, and a decent sound card, hard drive, screen, keyboard etc.

 I've read that Ubuntu will run on any computer that runs Win.Vista, but also that Ubuntu doesn't necessarily support the hardware for these PCs. So what laptop do you use?

 Also, take a look at the specs for the Dell Inspiron E1505. Will this machine run Ubuntu and support everything?

Thanks,
~Fob

---

### Post by oilchangeguy on 2007-04-04
go to [www.google.com](www.google.com) enter your laptops, name, model, and the word ubuntu in the search line.

---

### Post by Feba on 2007-04-04
From what i've seen, the biggest problem with laptops is internal wireless cards/drivers... if you can take care of that, I can't think of anything else that would be a problem.


And yes, Ubuntu should run on any PC that runs Vista, along with most PCs that run XP. Ubuntu is much less demanding on PC performance than Vista, and not too much more demanding than XP.

As with almost any computer you will likely have some sort of problem with something at sometime, no matter how well you plan it, so focus more on your ability to work around problems than problems in the first place.

---

### Post by Jsu07 on 2007-04-04
I run UBUNTU on my Dell E1505. It has the intel wireless a/b/g card (845 i think).....1.66ghz duo core with a 120gb hard drive. You have to tinker with the resolution a little bit to get the resolution right. But other than that everything works fine right out of the box. It also notices the duo core processor out of the box.....hope this helps!

John

---

### Post by Medieval_Creations on 2007-04-04
I run it on an old P3 IBM ThinkPad as well as a no-name brand 2Ghz Celeron.  It finds all the hardward no problems.  Even wireless (which is typically a problem).

If you are more looking for what types of Laptops work the best with Linux, I would probably say IBM & System76. (From personal experience).

[http://www.system76.com/](http://www.system76.com/)
[http://www.lenovo.com/us/en/](http://www.lenovo.com/us/en/)

---

### Post by Happy_Man on 2007-04-04
[http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505](http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505)

There! A full guide for your computer model! And it only took 10 seconds!

---

### Post by hardyn on 2007-04-04
just stay away from ATI and broadcom.

---

### Post by billygates on 2007-04-04
I have a IBM Thinkpad T60 with an ATI card and it works like a CHAMP.  Wireless works better with Ubuntu than with XP.

Running beryl on this thing at 1400x1050 is beautiful.

---

### Post by mrsticks on 2007-04-04
I run edgy just fine on my Averatec 5500.  Though I think the 5500 is discontinued, I would say most newer Averatecs would work OK.
I know a friend of mine had a dell inspirion ( dont remember the model ) and he had a hard time with his integrated wireless.

---

### Post by ahaurw01 on 2007-04-04
> **hardyn said:**
> just stay away from ATI and broadcom.

I run Dapper on my Dell Latitude D810 and it has an ATI card and broadcom wireless card. The wireless didn't work out of the box, but following an easily found how-to on the forums got it up and running. Also, the video card has given me zero problems whatsoever. I set up Beryl according to the most popular method for ATI cards and it worked without beautifully (literally). I've never had any showstopping problems with hardware (or anything for that matter) using dapper on this system, so I'd definitely recommend it.

---

### Post by rustybronco on 2007-04-04
Toshiba satellite pro 4300 using edgy had to add acpi=force for the fan operation, linksys wpc54g-v2 wireless works out of the box, minor shut down issue corrected,  I worked out each problem one at a time and it's rock stable.

---

### Post by sargeras on 2007-04-04
I have an alienware (see sig) and have had no problems with any hardware.  Wireless worked out of the box (intelpro wireless).  I have had previous laptops (all with broadcom wireless) and found the ndiswrapper setup to go very smoothly and work right away.  I agree, that the wireless is usually the most problematic, so before buying any new unit check the compatibility of its wireless radio.  Also, I have found ATI graphics cards to create much more hassel (and lower fps) than nvidia cards.

Just my 2 cents.

---

### Post by JayTheHun on 2007-04-04
No problems on my Dell Latitude (1.6GHz), P4, 768MB RAM, PCMCIA wireless card.

---

### Post by mikawber on 2007-04-04
I dual boot Vista and Ubuntu Edgy on my Inspiron 9300 with a nvidia 6800 and an Intel PRO/Wireless 2915 card. Everything worked right away and I've had no problems with it.

---

### Post by kfries6 on 2007-04-04
I have a home desktop running Fiesty, and a Dell D620 laptop running Edgy and both run GREAT!

Just a few pointers on the D620 if you buy it though.  The video will appear to not work on first boot via the CD.  Not to panic... It will drop you to the command prompt.  Edit /etc/apt/sources.list and turn on the Universe repository.  Then do an "sudo apt-get update && sudo apt-get install 915resolution" from the command prompt.  The native resolution of the laptop is 1440x900 but X can not do that resolution without this package.  Once installed, "startx" and you are ready to go.

The only thing I have not had work out of the box is the Bluetooth, but Suse, Debian, and Fedora also failed on this device (all of them also failed on other devices as well unlike Ubuntu).

Like most laptops, the wireless is a real PITA.  I still have issues with wpa_supplicant, but can connect to public networks without issues.  This is an Ubuntu issue, not a Dell one.

Good luck on your search...

Kevin Fries

---

### Post by drs305 on 2007-04-04
Lenovo 3000 N100. It took some work to get the Broadcom internal wireless card working. Other than that, Ubuntu works great on this machine.

---

### Post by ryckmonster on 2007-04-04
Dell Lattitude D600, running Feisty beta, dual booting Windows XP

Like a charm.

---

### Post by Gina on 2007-04-04
Ubuntu is much less demanding than Wondows - I have Dapper (6.06) running on a very old desktop - a 450MHZ AMD with 128MB RAM and 10GB HD - dual-booting with Win 98se.  Works fine even with wireless.  Also have it on a newer desktop (about 3 years old)..  And before upgrading to Feisty, had Dapper running fine on a 6 year old laptop. An AMD 1.3GHz processor, 512 MB RAM with shared graphics and 30GB HD - dual-boot with Win XP.  

Any PC you can buy should run Ubuntu quite happily.  Yes, I had to use ndiswrapper on the wireless adapters - even though there was a driver for my PCMCIA card WPC45G Linksys, it's an old model and the Linux driver didn't work.  So had to disable the driver and use the Windows driver with ndiswrapper.  All this is well documented in here and the main Ubuntu website.

---

### Post by russo.mic on 2007-04-04
I don't know why people are so scared of ATI and broadcom.  

I never have any problems with either.  At first, I thought I was dammed with my HP zv6000, an ATI radeon 200M and 4318 broadcom wireless.  

Now I run 64 bit Ubuntu, Beryl, and never have ANY problems with my wireless. NDISWrapper works flawlessly.

---

### Post by dbbolton on 2007-04-04
i have a compaq presario with ati and broadcom, and i hate myself.

---

### Post by hardyn on 2007-04-04
> **russo.mic said:**
> I don't know why people are so scared of ATI and broadcom.  

I never have any problems with either.  At first, I thought I was dammed with my HP zv6000, an ATI radeon 200M and 4318 broadcom wireless.  

Now I run 64 bit Ubuntu, Beryl, and never have ANY problems with my wireless. NDISWrapper works flawlessly.


If you want the ATI to 'just work', that's fine, its works just fine... but if you ever want to venture in to game land... or do some other the other fancy things... it just doesn't cut it... and with us on the brink of feisty, the fglrx driver still does not support xorg 7.2 and there is no telling when this may happen.

I had an ati on my last machine, and it worked okey... but i am MUCH happier with the nvidia offering in my new one... im not saying that the nvidia is good... its just better than ati, they are both pretty poor.
but i must praise both companies for offering something... they don't have to produce a linux driver.

and if you are buying a new computer anyway... it would be nice to stay away from something that requires a wrapper and has a native linux driver.

---

### Post by kaniak on 2007-04-04
[url=http://www.fallensword.com/?ref=287372][img]http://66.7.192.165/banners/full_banner2.jpg[/img][/url

---

### Post by kaniak on 2007-04-04
And im not sure,check out the website^it will pass your time when you are not working

---

### Post by rusty4r on 2007-04-04
I just installed Edgy on my Toshiba Satellite M45 S26__ and even the wireless worked at first boot. Haven't noticed any issues yet.

---

### Post by tjvanwyk on 2007-04-04
I'm running Kubuntu (Edgy) on my Inspiron 6000, but I don't think they make the model anymore.

The only problem is my wireless card, which oddly enough worked fine in Ubuntu out of the box, but it hasn't worked ever since I last formatted and switched over to Kubuntu.

(For the record, I had issues with it in Fedora Core 6, too.)

The wireless card is a IPW2200BG.

---

### Post by kpkeerthi on 2007-04-04
Running Edgy on Dell XPS Gen 2 (M170) with nvidia 7800 GTX. Everything worked out of the box. No problems.

---

### Post by mand0 on 2007-04-04
I've got a HP dv6000 with nvidia GPU and Intel wireless. Everything works in Ubuntu.

---

### Post by NeoGreen on 2007-04-04
I installed Ubuntu on a Compaq nx9010, and it was an experience.  Installing wasn't the problem, it was getting the wireless card to work.  I had to install ndiswrapper then the the driver for it to run.  It was pretty hectic but I got it to work.  :)

---

### Post by palmerthegeek on 2007-04-04
I've had good success with Dell D610, wireless work out of the box, and after going through a clean install.  I've also install on some of the older Inspiron series.   Good luck.

---

### Post by LaurelLynn on 2007-04-04
I run Dapper on my Toshiba Sattelite M35X-S161.

Every driver was working from install, even the modem and the wireless

Laurel Lynn

---

### Post by Michaelt74 on 2007-04-04
I use a HP ZV5000 and everything works fine. I'm not too concerned about gaming as I got myself a Wii recently.

---

### Post by shotgunefx on 2007-04-04
Inspiron 8600. Had a couple issues like the Port Replicator sound not working but that was recently patched.

---

### Post by mcduck on 2007-04-05
Asus A6Ja. works perfectly, only the web cam probably doesn't have Linux drivers but I might be wrong about that as I haven't even tried to get it working. Everything else works great, battery life is about 30 min longer than in windows and Beryl runs fine :D

---

### Post by atselby on 2007-04-05
Works great on my Dell Inspiron 8600 that my Uncle gave me. I don't know if he had any problems with an install but the wireless and sound etc. all worked and work fine.

---

### Post by thepaul on 2007-04-05
I am running Ubuntu 6.10 on a three year old Dell Inspiron 1000.  It has 256M of RAM and a 30 Gig HardDrive.

I have a Dynex wireless G card and I have had no problems gettting online with it.  Previously I had a generic B card and it worked right from the get go.

---

### Post by alpopel on 2007-04-05
im using a asus a8jc. a few days ago i installed feisty and even the webcam works! everthing works now!! yeah!

---

### Post by Ench on 2007-04-05
I have eMachines m5310 with Ubuntu 6.06 and it works pretty good... recognized all the stuff :)

P.S. But I hate the laptop because it overheats and the whole eMachines M5310 series are terrible because all of them do this :(

---

### Post by Pikestaff on 2007-04-05
I run Kubuntu Dapper on a Lenovo 3000 C100 and basically everything worked right out of the box... sound, internet, everything.  Works great :)

---

### Post by AusIV4 on 2007-04-06
I have a Compaq Presario X6000 (about 2 years old, you can't find the model anymore). It has a broadcom wireless card that worked out of the box with Edgy, but it only gets 802.11b - in windows it supports g. I also have an ATI mobility radeon x600 that works (with Beryl), but I haven't had much success with gaming - if I can stand the choppiness for about 5 minutes, the system usually crashes.

The Presario X6000 is a desktop replacement, weighing in about 10.5 lbs, getting ~1.25 hours battery life, and having a 3.0 ghz Pentium 4 with HT. It runs very warm (a couple of times I've had to use an air can to dust it out or it will overheat).

Even if you could find a similar model, I wouldn't recommend it.

What I would recommend is my [System76 Gazelle]("http://system76.com/index.php/cPath/1_10?osCsid=999effd4d589505d9a7ba89d14fff016"). I recently decided I need something portable. My 10.5 pound beast is great for heavy computing, but I wanted something I could take to class.

I got the base line Gazelle Value - 512 MB ram, 1.6 ghz Celeron M processor, 40 GB disk space, Intel GMA 950 integrated graphics, and an Intel wireless card. It runs wonderfully. It gets 54 mbps on wireless, while the accelerated graphics aren't quite as advanced, they have great Linux drivers, so the performance is better than my radeon. Beryl worked with very minimal configuration, and it runs incredibly smoothly.

If I had it to do over again, I would have spent a little bit more and gotten a Core 2 Duo instead of the Celeron M, a bigger hard drive, and I'd be getting rid of my Presario. This summer I may decide to swap out the hard drives from my presario and my gazelle and get rid of the presario - I have a desktop if I need the power.

In short, I'd definitely recommend finding hardware with open source drivers. Intel wireless has the best support of any chipset I've run across. Nvidia has a pretty good reputation for good graphics cards, but if you don't really need the power, I'd go with the intel GMA.

---

### Post by chasen.ibarra on 2007-04-06
i am currently running ubuntu feisty on my macbook...and my i say it rocks like no other ;-)

---

### Post by erimar77 on 2007-04-06
I have a Dell Latitude D610, almost everything works great with the exception of the crappy headphone port that puts out nothing but static.. not linux's fault though.  Sleep doesn't work very well either.

---

### Post by nerdman978 on 2007-04-06
Hi I use Ubuntu on my Dell Latitude D600 and it works great except for the wireless card, I haven't figured out how to get that to work just yet (don't mean to hijack the thread but any help especially from the person above who has a Dell laptop with the Broadcom wireless card that I have)

**Edit** Oh yah and I use Xubuntu on my homebuilt crap computer.

---

### Post by GSF1200S on 2007-04-06
> **Feba said:**
> From what i've seen, the biggest problem with laptops is internal wireless cards/drivers... if you can take care of that, I can't think of anything else that would be a problem.


And yes, Ubuntu should run on any PC that runs Vista, along with most PCs that run XP. Ubuntu is much less demanding on PC performance than Vista, and not too much more demanding than XP.

As with almost any computer you will likely have some sort of problem with something at sometime, no matter how well you plan it, so focus more on your ability to work around problems than problems in the first place.

Not too much more demanding than XP?? How do you figure? With the system monitor, Firefox, and rythmbox running, and a custom theme with a CPU usage indicator embedded on the taskbar, im using 217MB. Im running between 2-8% CPU with music playing... Windows XP runs 212 for me with everything closed, and with me having spent an hour customizing what services are disabled. This is before opening Nod32 and ZA, which bumps it to 260MB idle. I managed to get XP to run 174MB once, but it crashed 15 minutes after bootup.. must have turned something off I wasnt supposed to..

My point is, how is Ubuntu harder on a PC than XP?? That doesnt make sense.. it uses less resources, its faster, and its more stable.. Am I missing something here?

**Edit** And what about Xubuntu, which is practically the same as Ubuntu with an XFCE interface

---

### Post by Hortinstein on 2007-04-06
the computer in my sig works great, just a little boot tinkering and NDISWrapper to make the wireless work, and its perfect with beryl

EDIT i shoulda mentioned i payed $609.00 for it with shipping included
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwhxp&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwhxp&s=bsd)

---

### Post by iblis on 2007-04-08
i use a dell inspiron 5100 - old, but hey, it was $200 at the time.

ati radeon 7500 - i use the free driver, and with a few tweaks, it rocks. 

but of course, i'm not much of a gamer. :D

---

### Post by HokkaidoHillbilly on 2007-04-08
As in my sig, I'm running Edgy on a Dell XPS M1210, 2GHz Dual Core (T2500), 2GB 667  RAM, 100GB 7200rpm HDD, GeForce Go 7400, Intel 3945 wireless and the A/V package (i.e. built in cam & mic) w/ a Japanese keyboard.

Even though I've gotta Japanese keyboard and an English setup,pretty much everything worked out of the box, and configuring the WLAN card was a breeze - even using WPA.  Just note that for people w/ the Intel 3945, automatic ESSID scanning doesn't work out of the box, so you'll need something like WiFi Radar via Synaptic.

Updating the nvidia drivers & making them play nice w/ Beryl was a bit of an adventure, but once I figured out what I was doing, absolutely no problems at all.

Haven't really tested cam/mic setup, headphones, bluetooth or built in MMC reader, but for the moment I don't really need those functions, so it's not that big of a deal to me.  (although I've read that setting up the M1210 camera can be a bit of a beast...).

---

### Post by lamalex on 2007-04-08
HP Pavillion dv5139us. Works wonderfully. 2.0ghz AMD Turion64 processor, 2gb ram, 802.11 a/b/g broadcom 4311 wireless (works with native linux driver), ATI x200m graphics (which I haven't had trouble with although seems like everyone else has), 120gb hd, decent sound w/ altec lansing speakers, 15.4 inch ws screen, and ~1.5 hour battery on the standard 6 cell. Open office works great, as does gimp, and tons of other stuff, actually every program I've tried, including beryl/compiz. I don't think they make em anymore though :( but if you can your hands on one theyre great.

---

### Post by InuyashaDuelist on 2007-04-08
I don't have a laptop to run Kubuntu on, but if I did, it would be [this](http://system76.com/index.php/cPath/1_12) one.

<3.

---

### Post by LanMax on 2007-04-28
Dell D810 (Work Laptop)

OS's: XP Pro & Ubuntu

- Release 7.04 Feisty From Edgy.
- Memory: 2.0GB
- HD: Sata 60GB
- Processor: Intel Pentium M 2.00Ghz
- Video Card: ATI Technologies, Inc. M24 1P [Radeon Mobility X600]
- Wireless: Pro/Wireless 2200BG Network

Issues: (at the moment)

- Beryl
- Extended Screen/Monitor

---

### Post by rickycodie on 2007-04-28
i run a toshiba satillite that's like 3yrs old and ubuntu works great.

---

### Post by Bachstelze on 2007-04-28
I'm very happy with my Asus, everything I need - and much more - works perfectly well.

---

### Post by steveneddy on 2007-04-28
I use a lappie from [System76]("http://system76.com"). It is an Intel Core 2 Duo running at 2 Ghz, 2 GIG RAM and an nVidia vid card with 256 mb RAM.

It runs great, looks great and I know it will run well for a long time.

Ubuntu comes pre-installed on these laptops and you can get one in almost every configuration that you want. Pricing is reasonable and the service after the sale is wonderful.

Good luck - SE

---

### Post by mk_gm1 on 2007-04-28
I'm completely new to Linux, and I've been running Feisty Fawn for the last week on a Sony Vaio PCGFR415S: 2.8 GHz p4, 512 MB RAM, 60 GB HDD, 128 MB ATI IGP345M shared graphics. 

I managed to install Beryl, but it doesn't work particularly well. Compiz works fine though.

My Broadcom based Belkin pcmcia wifi card was actually relatively straightforward to set-up. 

Only real problems I've had are with random freezes e.g. while I was typing this reply, I had to reboot Ubuntu once, and restart Firefox twice.

---

### Post by hackman on 2007-04-28
> **ahaurw01 said:**
> **I run Dapper** on my Dell Latitude D810 and it has an ATI card and broadcom wireless card. The wireless didn't work out of the box, but following an easily found how-to on the forums got it up and running. Also, the video card has given me zero problems whatsoever. I set up Beryl according to the most popular method for ATI cards and it worked without beautifully (literally). I've never had any showstopping problems with hardware (or anything for that matter) using dapper on this system, so I'd definitely recommend it.

UPGRADE!!!:guitar:

---

### Post by hackman on 2007-04-28
**[CENTER] Installing Ubuntu Edgy (6.10) on Dell Inspiron E1505 (6400)[/CENTER]**

I recently bought Dell Inspiron E1505 (it's Inspiron 6400 in small business section of dell website). Here goes my notes based on Ubuntu 6.10 (edgy) installation on it (as dual boot).

First, my configuration:

    * Intel Core Duo 2.0GHz, 1 GB RAM
    * 128MB ATI MOBILITY™ RADEON® X1300 HyperMemory™ Card
    * 120 GB 5400RPM SATA hard drive
    * Dell wireless 1390 card
    * Dell 350 Bluetooth module
    * Integrated Broadcom 10/100 network
    * Integrate sound card 

Most of the hardware was recognized automatically by the ubuntu installation. Audio was working great. Wireless and graphics required following steps. (I have yet to test bluetooth, so no notes on that yet)

Dell Wireless 1390 Card
Ubuntu edgy configures wireless card with bcm43xx driver, but I was not able to make it work with it. Your best option is to use windows driver on linux with the help of ndiswrapper .

    * blacklist bcm43xx driver, by adding following line in /etc/modprobe.d/blacklist

      blacklist bcm43xx

      Reboot after that.
    * Download wireless card windows driver (either from your driver CD, or from the dell website). Unzip the .exe file - you should see a DRIVER directory with bcmwl5.inf file.
    * Now comes the ndiswrapper: I first tried the ndiswrapper package shipped with ubuntu using following steps, but that did not work.

      install ndiswrapper-utils, and configure the drivers using it

      sudo apt-get install ndiswrapper-utils
      sudo ndiswrapper -i /path/to/bcmwl5.inf
      sudo ndiswrapper -l
      sudo modprobe ndiswrapper
      ---> It gave an error

      So I uninstalled ndiswrapper packages installed by ubuntu.
    * Then I downloaded ndiswrapper-1.27 source code from ndiswrapper site , and compiled it like this.

      sudo apt-get install build-essential   
      tar -zxvf ndiswrapper-1.27.tar.gz
      cd ndiswrapper-1.27
      make
      sudo make install
      sudo ndiswrapper -i /path/to/bcmwl5.inf
      sudo ndiswrapper -l
      sudo modprobe ndiswrapper

      and then configured wireless using System->Administration->Networking, and everything is working great since then.

      Do make sure to add the following line to /etc/modules to make it work after a
      reboot also:

      ndiswrapper

Display Driver for ATI X1300

In order to use the full capabilities of this card, you will need to install ATI linux drivers. There are two versions of it - one is open source, and another binary only drivers from ATI. I went with binary only drivers from ATI, as they seem to be the best option. I used following steps:

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-2.6.17.10-generic
sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

Once it's done, add the following line /etc/modules:

fglrx

and reboot the system (or you can load the module yourself, and restart the gdm).


Using windows boot loader for dual boot ( Advanced Users Only )
One can either install grub into MBR (master boot record) for dual boot, or one can use windowsXP's boot loader itself for dual boot. I choose windowsXP boot loader in MBR instead of grub for following reasons:

    * You can delete/destroy your linux partition (and thus grub files), and you can still boot windows (quite useful if you play with linux a lot like me).
    * With Windows MBR intact, you still have access to MediaDirect (it's quite useful to play DVDs without booting into full-fledged OS). If you use grub, you can't boot into your MediaDirect partition. 

Anyway here goes the steps :

    * Use Alternative Install CD for Ubuntu, as it allows to install grub on a partition other than MBR. Use that, and select your linux root partition for installing grub instead of MBR (remember to write down you root partition number while editing your partition table during installation).
    * After installation, use a linux rescue CD with grub shell support (e.g. RPL), and boot into your newly installed ubuntu with following commands:

      root (hd0,X)
      kernel /boot/vmlinuz-2.6.17.10-generic root=/dev/sdaY ro quiet
      initrd /boot/initrd-2.6.17-10-generic
      boot 

      Y is the linux root partition selected by you (e.g. 1 or 3 or 5 etc), and
      X = Y - 1.
    * Use following commands to create linux.bin file, and copy that to usb stick, or to your windows partition.

      sudo dd if=/dev/sdaY of=linux.bin bs=512 count=1

    * boot into windows XP, copy linux.bin to someplace in your windows partition (say C:), and then edit C:\boot.ini to add following line in the end:

      C:\linux.bin="Linux Ho Ho Ho"

      and you are set. If you want, you can decrease "timeout" at the start of boot.ini file to 10 secs instead of default 30 secs.
    * Now reboot your computer, and you will see the option of booting into linux from windows Boot Menu.

---

### Post by philby on 2007-04-28
Was installed and ran fine on a Dell9400 - T2600, 2gig ram, Nvidia 7900 card using withheld drivers. However had to remove and am now trying to put a dual boot system together for more testing.

Am a linux Novice but I have to admit the 7.04 is nice, seemed stable to me wireless card, bluetooth and all bits seemed to work. Impressed that plug and play on my external HDD USB2 work flawlessly, only problem is getting to grips with a new OS after using MS for so long.

---

### Post by [S|G] on 2007-04-28
I'm currently using Kubuntu 7.04 on an Acer 5630 laptop, and almost everything works great. Everything, including wireless and webcam, was detected when I installed it. I had to install 915resolution to get the screen working at 1280×800.

What I don't have working yet is the card reader (I read it was working under edgy, so it'll probably get fixed soon) and using dual monitors.

---

### Post by jerrylamos on 2007-04-28
I'm using an IBM Thinkpad R31, 1 gHz, 512 mb memory, 20 gb hard drive, dual booted with XP and Feisty.  Works fine, from an "ordinary laptop computer user" standpoint, internet mail, internet videos, browsing, Open Office word, spreadsheet, presentation, digital photo copy & print, LAN file sharing, ....  I don't do games and I'm into applications, not eye candy.  The trackpoint mouse was twitchy with Festy (not Dapper) however someone posted a fix.  I'm just getting into wireless.  It works on the XP and did work on Dapper with ndiswrapper; haven't gotten into it on Feisty.

Cheers, Jerry

---

