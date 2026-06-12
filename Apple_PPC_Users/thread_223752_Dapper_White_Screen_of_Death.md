---
title: "Dapper White Screen of Death"
date: 2006-07-26
forum: Apple PPC Users
---

### Post by sven04 on 2006-07-26
Hi All,

I have an older Digital Audio G4 533 with 640 megs of ram that I want to use to run Ubuntu Server. The problem is I can't use any of the Ubuntu Dapper CD's to install from. When I boot from the CD I either get a completely white screen that just hangs or sometimes I get "lucky" when choosing another install image and get a white screen that goes black then hangs (like there is no signal going to the monitor. my green led on the monitor turns orange).

I can, however, install 5.10, set up ssh under 5.10, and then upgrade to dapper using the process outlined at < [http://psychocats.net/ubuntu/dapper.php](http://psychocats.net/ubuntu/dapper.php) >:
% sudo aptitude update
% sudo aptitude upgrade

When I reboot into Dapper (without the CD in the tray) I get the "White Screen of Death" again. I am, however, able to SSH in from another computer and admin stuff just fine. Since this will be a server I guess this will be ok but I really want to understand:

1) What can I do to make the Dapper install CD behave like the 5.10 release?

That is, work... no white screens.

2) In the interim, how can I fix the "White Screen of Death"?

According to < [http://support.apple.com/specs/powermac/Power_Mac_G4_Digital_Audio.html](http://support.apple.com/specs/powermac/Power_Mac_G4_Digital_Audio.html) > I have a NVIDIA GeForce2 MX with
32MB of SDRAM video card.

I want to start from scratch with Dapper -- properly partition the drives, install a clean version 6.06, and update things from there.

All of the CD's I have burned work fine on my 17 Inch Powerbook so I do not  think that the CD's are the issue.

Big thanks for any help you can provide!

---

### Post by avtolle on 2006-07-27
Big guess: install the correct drivers for your video card.

---

### Post by sven04 on 2006-07-27
gee... that was helpful.

---

### Post by don_pucci on 2006-07-27
Same problem with me. 

I have a G4 (quicksilver) and I successfully installed 6.06 desktop on it.  I however cannot install the server (specifically the LAMP server).  All I get is a white screen and sometimes a black screen then my monitor goes out of range (if I choose an option other than the default).

Anyone have any ideas?

I have tried the video=ofonly which did not work.

---

### Post by don_pucci on 2006-07-28
I have also tried the alternate cd....with the same problem.

I can boot from both a ubuntu and kubuntu live cd no problem.

also, the ctrl+alt+f1 does not give me a prompt of any kind, i just get the yaboot screen.

---

### Post by avtolle on 2006-07-28
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

---

### Post by don_pucci on 2006-07-28
ok..so the link you gave says the following that is relevant to my system:

===============================
3D Nvidia Video Card Driver

No Nvidia Video cards have 3D acceleration enabled automatically with Ubuntu, because the manufacturer does not release open source drivers. However, it is possible to activate 3D acceleration. The process depends on which type of video card you have.

   1. If you have an older TNT, TNT2, TNT Ultra, GeForce1 or GeForce2 card, install the nvidia-glx-legacy and nvidia-settings packages from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).

   2. Alternatively, if you have a newer card, install the nvidia-glx package from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).

   3.To enable the new driver, run the following command in a terminal:

sudo nvidia-glx-config enable 

   4.You may adjust the settings of the new drivers by running the application nvidia-settings (see the section called “Start a Program Manually”). If you wish, add a menu entry for this program (see the section called “Menu Editing”).

===============================
How do I add these packages if I cant boot into the OS?

The white screen is the problem...and I get it when trying to install.

---

### Post by don_pucci on 2006-07-28
also....why would the live cds work fine?

---

### Post by avtolle on 2006-07-28
Don't know why the live cds would work fine; that has me stumped. I noted in some threads by G3 owners who faced the white screen and otherwise had boot problems that sometimes repeated attempts to get to the terminal were necessary, that is, try the ctrl-alt-F1 repeatedly. I didn't have your problem, and am only trying to pass along some of what I have read in the event you didn't see it.

---

### Post by don_pucci on 2006-07-28
Thanks, I will try modding the xorg.conf again.

Hopefully that will work.

So much for the big move to Ubuntu!

> **avtolle said:**
> Don't know why the live cds would work fine; that has me stumped. I noted in some threads by G3 owners who faced the white screen and otherwise had boot problems that sometimes repeated attempts to get to the terminal were necessary, that is, try the ctrl-alt-F1 repeatedly. I didn't have your problem, and am only trying to pass along some of what I have read in the event you didn't see it.

---

### Post by avtolle on 2006-07-28
Good luck; if I run across anything which might be helpful, I'll post.

---

### Post by don_pucci on 2006-07-28
much appreciated.

---

### Post by don_pucci on 2006-07-28
ok..so i am quite the noob.

ctrl+alt+f1 doesnt seem to do much for me.

I get yaboot and a prompt that says:

boot: 

What am i doing wrong?

thanks again for anyones help.

---

### Post by don_pucci on 2006-07-30
anyone?

---

### Post by tseliot on 2006-07-31
> **sven04 said:**
> 1) What can I do to make the Dapper install CD behave like the 5.10 release?
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by don_pucci on 2006-07-31
Thanks for the post...but as I noted, the alternate cd also gives the same White Screen.

I guess it is just not meant to be....I will just use XAMPP on OS X.

---

### Post by tseliot on 2006-07-31
> **don_pucci said:**
> Thanks for the post...but as I noted, the alternate cd also gives the same White Screen.

I guess it is just not meant to be....I will just use XAMPP on OS X.

At least try point 3 and 4...

---

### Post by don_pucci on 2006-08-01
SIGH...I really appreciate your guys help.

but, how am I supposed to try anything with a white screen?

the whole problem is that I cannot get a prompt...but I guess I did not make that clear enough.

> **tseliot said:**
> At least try point 3 and 4...

---

### Post by avtolle on 2006-08-01
don_pucci: your problem and that of the OP has me stubbornly trying to figure it out, if not for you, for others who have the issue. Tseliot refers to booting into the recovery mode at the GRUB menu; since we are on Macs, we don't have GRUB, we have Yaboot; my question: is there a way to access the "recovery mode" in yaboot? I didn't see it, but there is much I could be missing. Thanks to anyone who can help.

---

### Post by avtolle on 2006-08-01
[http://www.ubuntuforums.org/showthread.php?t=143309&highlight=Recovery+mode+Yaboot](http://www.ubuntuforums.org/showthread.php?t=143309&highlight=Recovery+mode+Yaboot) Linear, in the 4th post, indicates there is an indirect way to get into recovery mode from booting the Alternate Install CD. Apparently, there is no direct way to do this; anyone have anything else to add?

---

### Post by don_pucci on 2006-08-01
OK, I will try booting into recovery mode from the Alternate CD and then type: 

_pkg-reconfigure xserver-xorg_

and then:

_reboot_

Do i also have to edit the xorg.conf?  I guess it couldnt hurt to try.

Thanks again for your assistance.  I will post when I have an update.

---

### Post by avtolle on 2006-08-01
That should be dpkg-reconfigure xserver-xorg, i believe. Will look for your post.

---

### Post by don_pucci on 2006-08-02
Well..choosing the RESCUE option from the Alternate CD gives me almost the same problem.  This time my monitor goes blank (assuming it has gone out of range).

This is becoming such a pain in the arse.

---

### Post by don_pucci on 2006-08-02
I am almost certain that modifying the xorg.conf will solve the problem, however this is not possible as I am unable to actually get a command line to do so.  I am so very lost.

---

### Post by avtolle on 2006-08-02
I concur. It's very frustrating to read all the threads on this Forum concerning similar problems, without there being a set of fixes to which to refer the poster. I'm truly fortunate, in that w/my G4 Cube, stock (except for the additional 512 mb RAM I added), I had no such problems. Again, I'll keep looking to see if I can find any answer, and will post if I do. Thank you for your updates.

---

### Post by don_pucci on 2006-08-03
I truly appreciate your help.

I think I have decided to abandon using Ubuntu for now and will go with another distro for my PPC.

Thanks again.

---

### Post by don_pucci on 2006-08-03
I truly appreciate your help.

I think I have decided to abandon using Ubuntu for now and will go with another distro for my PPC.

Thanks again.

---

### Post by Gossie on 2006-08-03
The last two days I have been trying to install Dapper Drake on a:

* G3 power pc Blue&White Mac
* 450 MHz 
* 208 MB ram (pc 100sdram chips)
* 8,5 GB harddisc
* MAC OS 9.1

It has OS 9.1 for operating system, and it worked ok. 

Then I put the Dapper Drake install cd for power pc in it, hold "c" and restart. I got a blank screen (or sometimes grey). This white screen also appears when I use:

* desktop  install powerpc burnt at 4x speed, 
* alternate install powerpc burnt at 4x speed,
* Ubuntu 5.10 Breezy Badger install powerpc burnt at 4x speed.

Every try I hold down the "c". I get a blank screen (sometimes grey). I tried the ctrl-alt-F1 as well instead of "c", but that doesn't do anything. And when I have an Ubuntu cd inside, and restart while NOT holding down "c", I get a "default catch!, code = 300" running across the screen.

When I restart the computer without a cd in it, it gives a question mark. When I put the MAC OS 9.2 cd in it - for which espacially I travelled to Amsterdam  today! :D - I get sort of a knoppix live session meant to install os 9.2.

My question is, does someone know a method to let this nice G3 know there is a newborn Drake in the world?

If it doesn't work, I will get OS 10.3 to work with during the coming weeks. Now, I will try a fresh install of OS 9.2 and if that works, try the Ubuntu install cd('s) again.

Good night, Gossie from Utrecht, the Netherlands

---

### Post by avtolle on 2006-08-03
Gossie: [http://www.ubuntuforums.org/showthread.php?t=219532&highlight=Mac+G3](http://www.ubuntuforums.org/showthread.php?t=219532&highlight=Mac+G3), posts 4 and 5, address at least a part of the issue you are having.

---

### Post by bwilson on 2006-08-03
I had the "white screen of death" problem during install too. I found that the install worked when I set the screen resolution to 1024x768 in Mac OS X, then rebooted with the installation CD. The white screen does appear for a minute or so, but eventually I see the GNOME installation desktop.
I hope this helps.

---

### Post by Gossie on 2006-08-04
Thank you! I will go and get another monitor from the give-away-shop that can work with 1024. This one can only manage 800x600. 

(There are a lot of monitors in the give-away-shops. When I got this monitor last week, they said to me: "Please choose one and take three!").

---

### Post by don_pucci on 2006-08-04
So you are saying to install OS X, then change res to 1024x768 and then reboot with the ubuntu install cd?  I dont see how that would work, but I will definitely try it.  Thanks!

> **bwilson said:**
> I had the "white screen of death" problem during install too. I found that the install worked when I set the screen resolution to 1024x768 in Mac OS X, then rebooted with the installation CD. The white screen does appear for a minute or so, but eventually I see the GNOME installation desktop.
I hope this helps.

---

### Post by kioshi on 2006-08-05
I dunno, I've suffered so much with Ubuntu 5.10 (both Live and not) in my iMac G3, I get the impression Ubuntu isn't ready for Macs yet. Anyhow I'll try Dapper.

---

### Post by godard on 2006-08-05
A lot of the experiences occurring on G4's and some G3's are related to this bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508) 
I have the latest version of the kernel and it will still not fully boot, you may however be able to use the old breezy kernel in the meantime.

---

### Post by Gossie on 2006-08-06
> **don_pucci said:**
> So you are saying to install OS X, then change res to 1024x768 and then reboot with the ubuntu install cd?  I dont see how that would work, but I will definitely try it.  Thanks!

I managed to change the resolution, using another monitor, to 1024x786, because I got the harddisc back to work and installed OS 9.2.2 

(After I had pressed the wires inside it worked :)

With the big resolution and the big monitor, I tried to boot from the Dapper desktop powerpc, Dapper alternate powerpc, Breezy 5.10 powerpc, Yellowdog linux 4.1 (I read that's good for Macs), all burned at 4x speed, but I get either:

x. a prompt without cursor, saying: "type mac-boot or type shut-down"); or
y. the white or the grey screen; or
z. the letters "default catch!, code=300" etc. running accross the screen (if I do not hold the "c" key down).

The pc doesn't seem to react to my burnt linux cd's. The discs spin around, but the cd-rom green light turns off and it doesn't load anything. With apple-cd's the light stays on and the Mac becomes happy (or, is told to be happy by the cd :evil: ).

With OS 9 running, I can read the Dapper cd's in the file browser.

The key(s) (combinations) control-alt-F1, (control-apple-F1?), and shift don't do anything, I'm sorry to say.

I will just get OS 10.3 next week and try again with ship-it cd's.

I don't like to try hacks like control-option-n-v as someone suggests ([http://www.ubuntuforums.org/showpost.php?p=1344592&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=1344592&postcount=6")), cause I dont have a very good fire escape in my house - don't take it personal, I'm just a newbie to Macs!


Could it be that I need a IDE harddrive and not the SCSI that I have now? ([http://www.ubuntuforums.org/showpost.php?p=787384&postcount=52]("http://www.ubuntuforums.org/showpost.php?p=787384&postcount=52"))

---

### Post by Gossie on 2006-08-06
well, we hung in another harddrive, and with an IDE harddrive I can type in the shell!

There appeared to be a second harddrive in the pc, an IDE, but it is probably broken. We took that one out. The IDE that is inside now, is supposed to be working. The SCSI is now shut off.

We got another cdrom drive too, to be sure.

No I can choose to type "mac-boot" or "shut-down", it says.

So now I'm gonna read this forum again to get the next step right.

---

### Post by Gossie on 2006-08-06
but well, I cannot load the cd's

Shaking the pram has no result (I took that risk)

When I hold down the "c" key, I get a prompt but cannot type

When I don't hold down the "c" key, I can type in the prompt

When I type "mac-boot", then it says "Default catch!, code=300 at ('blah-blah')"

"boot-cd" it doesn't know what that is.

Pressing "ctrl-alt-F1" does not react.

I got an empty IDE harddisc hanging in there, the cables of the SCSI Mac OS harddisc are loose.

At the background of the prompt (Firmware version 3.1.1) there is an icon of a blue folder, blinking with a face and a question mark. What you feel is what you get?

---

### Post by GREGMACKENZIE on 2006-08-08
Hi All,

Just a thought but I did get Hoary to install on my iMac 333 tray loader without running into the white screen. Someone suggested following an upgrade path from Hoary, to Breezy, to Dapper instead of trying to run the Dapper installer directly. If you have to take your imac apart it sounds like your working too hard. ;)  

My iMac won't even boot Dapper from the live cd so I get nowhere with the xorg modification since I can't get to the command prompt. From my reading this is related to a kernel problem. I also noticed that in the Ubuntu Desktop Guide for Dapper that it doesn't even mention the G3 as a supported processor. G4 is the last one in the list. It would be nice to have a simple working solution if Dapper is in fact intended for the G3. :confused: 

What's the general thought on this live CD fiasco? Is there a working solution?

Greg

---

### Post by GREGMACKENZIE on 2006-08-08
By the way this is what happens to my iMac slot loader 333 with 288mb of ram and rage pro video:

I didn't have any trouble installing Hoary 5.0.6 on my iMac but Dapper just won't install. Here's what happens:

To boot the Dapper installation CD on an iMac you have to hold down the “c” key with the cd in the drive. On booting there is a black screen, followed by a white screen, followed by a black screen with a boot prompt. Here's where problems set in. The system starts to boot but a white screen appears with the following message:

“Cant Allocate Initial Device Tree Chunk
Apple imac open firmware 3.0.f2 built on 04/23/99 at 14:31.03
copyright 1994-1999 Apple Computer Inc
All rights reserved
ok
0 > _”

Greg
:-\

---

### Post by avtolle on 2006-08-08
A few notes from my reading of various threads and from my personal experience. First, as I have previously posted in another thread(s), I did a dist-upgrade from a fully functional Breezy install on my G4 Cube, with absolutely no problems, have continuously updated as the same show up, etc. Therefore, for those who can, if you can install Breezy (5.10) and get it working, do so, then try the dist-upgrade. In that way, you can avoid the issues with the problem kernel on the Desktop (Live) CD iso.

Next, (here comes my Mac ignorance), on the G3 systems; it is my understanding that 6.06 PPC works on "new world" G3s (more or less; some tweaking of kernel or xorg.conf, etc. is needed from time to time), but on "old world" G3s (and earlier ppc chips), it is necessary to install Boot-X, with various copying of kernel information, etc. so the computer may boot from OS 9, etc., then recognize the Linux kernel. So, this may explain why G3s are not shown in the Guide, for not all of them can boot (at least "kind of") from the CD.

Third, some posters have had success using the "Alternate Install" CD, due to some bugginess of the graphic installer on the Desktop CD. I know Gossie has tried this without success, but am wondering (again from other threads) whether part of the issue is the lack (at least initially) of a Mac OS on his particular computer. There is some relationship there; I'm not experienced/knowledgeable enough to figure it out right now (or ever?).

Anyway, the above is offered for your consideration FWIW.

---

### Post by Gossie on 2006-08-08
Hi everybody,

Also with OS 9.2.2 running, I cannot boot from the cd's. I will get ship-it cd's from the intelligence information club downtown! 

What do you think, would Ubuntu make a difference between SCSI and IDE harddiscs?

Greetings, Gossie

---

### Post by Gossie on 2006-08-10
Well, there seems to be something wrong with the cd-rom drive of my powerpc G3. Because the OS 9 cd won't boot anymore, and also the OS X 10.3 installation cd that I got today, and the Ubuntu Breezy Badger ship-it cd for the Mac don't boot.

I have a SCSI harddisc that belongs to the Mac. 

Then there is an IDE cable with first a harddrive (master) en then a cdrom drive (slave).

At first it would boot with apple-cd's, like the OS 9 installation cd. But now we changed the cdrom from master to slave (harddrive was master and still is master).

I will try again with another cdrom drive and then use the ship-it cd's.

Thanks for listening! Bye. :KS

PS: My main goal is to install Ubuntu, the OS X is because I might need its linux terminal to give reboot commands.

---

### Post by Gossie on 2006-08-12
Hi!

An expert got my cdrom drive working after he put the second (IDE) HDD into master...

BUT it only boots with apple cd's...

I read here that this could be the case with ALL Blue&White G3 computers!

[http://www.ubuntuforums.org/showthread.php?t=8984&page=2](http://www.ubuntuforums.org/showthread.php?t=8984&page=2) (posts 17, 18, 19)

So I may accidentally have the wrong cdrom drive for booting Ubuntu on a Mac.

I will try 5.04 again.

---

