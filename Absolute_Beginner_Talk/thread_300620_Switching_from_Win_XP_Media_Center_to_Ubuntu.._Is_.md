---
title: "Switching from Win XP Media Center to Ubuntu.. Is it right for me?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by thumper13 on 2006-11-15
I've dabbled in Ubuntu numerous times, I do like it. This is why I'm considering running Ubuntu as my OS instead of that "wonderful" piece of software called Windows.
 
Recently, I've become victim of one of many Windows XP flaws. I'm about tired of dealing with this piece of crap. I've also looked at Windows Vista, and to me it's the same as Windows xp with a different interface. 
 
I'm definitely debating either switching to Linux solely, or scrapping my PC and buying a Mac. I'm not new to Ubuntu or Linux, but I'm nowheres near a professional. I'm, of course, willing to learn though.
 
A little about my computer
 
HP Pavilion a1330n (Currently running Windows XP Media Center SP2)
 
AMD Athlon 64-bit 3800+
1024 MB RAM (Shared with video)
ATI x200 onboard video
Onboard sound and network (Sound is Realtek AC97, unsure about the network card.)
250 gig S-ATA hard drive
DVD Rom
Lightscribe DVD Writer
Card-reader-thing
17" Neovo LCD monitor
Hp Media keyboard and mouse
Logitech Dual Action game paddle
 
I also have a wireless network (I am connected by wire though. The concern is that I would like to know if I can still use the same network where the other 3 machines are running Windows) Its a D-Link WBR-2310 router, if that helps.
 
I use basic cable internet, through Rogers Inc, Ont. Canada
 
I use my computer for a variety of reasons, but mainly school and gaming. School is taken care of, thanks to the lovely people at OpenOffice. I know how to get my MP3's to work and whatnot, so that part of the install is no prob.
 
THE ONLY THING STOPPING ME is that through research, I've found mixed reviews on playing World of Warcraft (My anti-drug) in Linux. As i stated, I'm not a newbie, but I'm no professional. For me, I'd need it to be pretty straightforward, as I have no idea how to troubleshoot Linux ;) Even reading reviews on wine, cedega (which is pay, i'd rather not pay, thank you very much, but if it's the only alternative, i would) and something called Crossover (i think), I've heard people have problems with them all, ESPECIALLY with my ATI video card. If it is really hard to get it up and running well, I think I would be better off buying a Mac. But my computer is fairly new, and I prefer Ubuntu Linux OS over Mac OSX anyday. Also, I would need to be able to use my card reader (it's a built in job, not usb. It attaches straight to the motherboard. I haven't tried using it on the Live cd tho.)
 
It would be awesome if Linux had a program for Lightscribe out. I know there are progs to burn discs, but I mean so I can flip the disc and use Lightscribe to label it. I'd also like to keep use of the media buttons on my keyboard.. You never realize how much you use them 'til you don't have them anymore. I also have the Media Center remote for my PC, and I'd be overjoyed if that worked too (Although, I've never looked into the possibility of watching DVDs on Linux to begin with. If its possible, can I use my remote to pause/play/rewind etc?)
 
If you made it this far in my post, thanks for reading it. I realize I'm asking a lot of questions in one post, and you might even think I'm demanding. (LOL) The truth is though, I just want to make sure Linux is right for me before I dive head first into it.
 
Any input would definitely be appreciated, and if you are running this type of machine (HP Pavilion), please leave some input, I'm interested in finding out what this machine is capable of.
 
Thanks,
Dan :)

---

### Post by Taigrr on 2006-11-15
As much as I hate to say it, I enjoy Media Center. I don't know why..

But, I also love Ubuntu.  Anyway..

FOr your World of Warcraft problem, you might try "Cedega", it's a program like wine (I guess?). Might do the trick!

---

### Post by d3v1ant_0n3 on 2006-11-15
I can't really answer *any* of your questions, sorry.

I will offer you one suggestion tho: DUAL BOOT

I know it sounds pat, but basically, give it a try. It's stunningly easy to install Ubuntu on a windows machine without killing your windows install, and pretty simple to take it off again if you find it's not for you.

This will also allow you a safety net while you find your feet in Linux ( I was a fool and didn't give myself this option)- and if you can't find programs you need in Linux, you still have your windows install for those tasks.

For my needs, I find Ubuntu perfect. i does all my day to day computing tasks wonderfully (much better than Windows, IMO), and also allows me to learn a lot more about my computer and the way it runs.

---

### Post by gigaferz on 2006-11-16
I also have a pavilion, not as complete like yours.
But YOU RAISE a very interesting point. Lokk all those features you have right now. Your machine just works fine.

Honestly before anything ,try the live cd for at least 2 weeks.

Lokk at my thread.. It just worked! now little by little im adding features according to my needs.. But the basic stuff is there...also look at the sticky threads before anything else..

[http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)
[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

The only reason Im going into linux is because the security
reasons.For example not even if you pay for it its guaranted to work..
We got spysherrif on a computer with the almighty norton and all the whistles that make your computer a turtle... Thats an insult for all the people under windows..

---

### Post by Tim Prosser on 2006-11-16
I would definitely dual boot, at least for a while, rather than going cold turkey.  It really isn't that difficult if you have some spare disk space.

It is really helpful to have at least one reasonably sized partition that is FAT32 rather than NTFS so that you can read and write it from Ubuntu and Windows reliably.

You probably only need a maximum of 10GB for the root Ubuntu partition (mounted on /), and maybe 1GB for a swap partition, but how much you need for your home directories (ie /home) depends on how many files you would keep exclusively on Ubuntu.  

I have no experience of getting WoW or game paddles to work - I think that might well be your biggest headache.

However, I use my Ubuntu build for all multimedia stuff.  There is an application called MythTV ([www.mythtv.org](www.mythtv.org)) that works extremely well with most TV cards and also with lirc (which supports most remote controls after a bit of fiddling, although check yours).  I don't have a conventional TV in the house, I record everything in Myth and watch it wirelessly on a laptop (you can have separate backends and frontends), or on a projector if it is worth it.  I haven't seen an advert for a long time - its very easy to skip, or even use the built-in ad detector, provided you don't watch live (I don't).  It also plays DVDs with the menu and remote support, although you do have to use libdvdcss for commercial disks which is technically illegal in some countries.  If you can't be bothered with Myth (it can be a pain to install, although Edgy has a 0.20 build in one of the repositories which works pretty well), then Xine, Kaffeine and Totem all play DVDs successfully - I think Xine can be configured with a remote.

For cutting or re-encoding video manually, I use Avidemux, and there are several apps for DVD creation, although some are not massively user friendly.

As for your Lightscribe DVD burning - there is an app that works with K3b, although its probably not free in one way or another.  See [http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

Workwise, yes, I don't think you'll have any problems using OpenOffice (although watch out, its a bit unstable at the moment - see other threads - you might want 2.0.4-2).  My other half uses our Linux machine exclusively for work (mostly report writing and map drawing) and communicates with lots of other companies without difficulty.

Good luck!

---

### Post by hyper_ch on 2006-11-16
If you are absolutely positive about switching to linux then I would recommend you the following:

(1) Backup all your data
(2) Reinstall Windows - and don't forget the security updates and firewall and anti-virus proggy
(3) Install Linux (X/K/Ed/Ubuntu or any other distro...) - a rule of thumb for the swap partition is twice the size of your ram :)

Then for normal use just use your linux install (which should be default in the boot manager) and for gaming you will have a very light WinXP (without left-overs from countless programs that will reduce performance)...
I assume when you game you don't do other stuff on your computer... at least that was the case for me when I still played on my computer... so a dual-boot might be the best thing to do

---

### Post by thebucksstop on 2006-11-16
I've just made the jump myself, and am now all set up with a dual-boot (XP is still essential for Photoshop - GIMP just doesn't hack it!). One thing I found really useful is Explore2fs, which allows Windows to read and write to Ext2 and Ext3 - meaning there's no need to suffer all the drawbacks entailed with FAT32.

All in all, I'm really happy having made the switch, though gaming has proven to be a bit of a nuisance - I'm still working through things to try and straighten them out (in my head at any rate!)

---

### Post by Bazzaah on 2006-11-16
I'd just like to add that I put Ubuntu on my machine a few weeks ago thinking that it'd be a bit of fun. I haven't used Windows in any meaningful way since I put Ubuntu on a slave HDD.

Both Dapper and Edgy have been great for me, especially with Beryl and were it not for an expensively added-to install of MS Flightsim on my XP install, I'd switch 100% to Ubuntu. 

I have an ATI card and as long as you do a bit of reading of the various guides about installation you shouldn't have any problems. My experience at least was completely trouble free.

---

### Post by hyper_ch on 2006-11-16
The buck: If you have a dual core processor maybe you want to consider using vmware and load windows within ubuntu itself to work with photoshop... on a single core processor (like my amd sempron 2500 it's just veeeeery slow to load a virtual windoze ^^)

---

### Post by Bachstelze on 2006-11-16
Get yourself a nice nvidia card and you should be OK for WoW. And if you still have problems with it, the community is here to help you, I don't think all the people who play WoW in WINE are 'professionals' ;)

If I were you, I'd setup a dual boot and I'd try to get it all working. If it works the way you want, fine. If it doesn't, just delete it :)

---

### Post by thumper13 on 2006-11-16
Thank you all very much for the input :) 

Taigrr: I have read that there are several issues with Cedega and ATI video. I really like ATI cards, and even this onboard one runs WoW beautifully, so I really don't want to have to switch video cards, if at all possible.

d3v1ant_0n3: Dual boot is definitely an option I've considered, but I've heard that a dual boot will make my performance on my computer suffer (I don't know if this is true or not.) Being a gamer I'd really like to have WoW run as nice as possible. I realize it won't be perfect, since i'm porting it to linux, but I'd still like it to be playable :)

gigaferz: Those links are great. You are right, I do have a lot of features. But my windows install is going down the tube and tbh, i just need a change. I have a copy of Dapper in my closet that i've tinkered with before, but rather than pull out my HP dvds and reinstall windows, i am considering Ubuntu. I really like how ubuntu works (makes my machine go a little faster too, i think.). Also, support here is great. in 1 day, i already have this many posts... whereas to call Microsoft i could sit all day on hold (lol)

Tim: Thanks for the post, i'll definitely be looking for some of that information when/if I migrate to ubuntu :)

sjau: That would probably be what i'll do, if i go to Ubuntu. Some programs I use for school WILL NOT run in anything but windows (that I know of.) But again, I have heard that I will suffer a performance loss. I've heard it's really significant, like if it were 2 fps or something on WoW  I wouldnt care, but from what I understand, if I dual boot, WoW becomes unplayable in Linux or Windows, it's just too slow.

thebucksstop: Thanks for that info, I'll definitely need it if I want to access anything.. I was going to post that question actually, but you answered it :) With explore2fs, can I play media from a windows part in linux? or even copy it out? if I could just do that, that would make me a happy happy person.

Bazzaah: I know the feeling. If it weren't for damn Warcraft I'd be a linux user already. Its not installing my ati card that worries me. It's getting it to run properly in games. Thats what I need, but, again, I've heard ATI video cards + World of Warcraft = barf, and that's what concerns me.

HymntoLife: I have a linux setup already on a POS that I found in my complex's dumpster.. It's a dapper install. I love it. The community is actually one reason I want to switch. People are nice enough to help new users. Like I said before, I'm kind of biased towards ATI, and I'm not a big fan of nvidia. Besides, if I open the side panel of the case, my warranty is void. (Fear not, I already called HP and they said I can load whatever software I want as long as I don't modify the hardware.)


Again, thanks for all the replies, I was kind of surprised I'd get this number. But still, if there's anyone out there that would like to offer an opinion, please do, I need lots of input. As well, if you have a computer similar to mine with an ATI vid card, and you play WoW on your linux box, let me know, i'd love to find out how it runs :)

Cheers,
Dan

---

### Post by drenicky79 on 2006-11-17
I faced a similar dilemma. Decided after reading about Vista that I did NOT want to shell out $500+ to "upgrade" the machines I have now (desktop runs XP Pro, Toshiba Qosmio G25 laptop runs XP Media Center). 

The Toshiba has 120 gig of storage split between two 60 gig SCSI HDs, so I simply wiped drive D, installed Edgy there and I now have a dual-boot laptop. Installation was really flawless and took an amazingly short amount of time. After some time goes by I will likely upgrade the Windows half of this laptop to Vista Ultimate (I want to keep the Windows features that are integrated with the laptop - and I am also locked into a Windows environment at work), but the desktop machine will get converted to Edgy exclusively very soon. I can't say enough about how easy it was to get this up and running. Lots of my Windows friends tried to frighten me about doing this, but I feel like a great weight has been lifted from my shoulders. I don't *need* Windows after all.

---

### Post by hyper_ch on 2006-11-17
Well, Windoze runs fine on my AMD Sempron 1.4 Ghz with 1 GB DDR Ram in vmware... it's just slow and slows down also kubuntu edgy... a dual core would be a great solution there... you could then even start windoze from it's own partition... there is somewhere a howto...

Dualbooting will not reduce performance at all... you will have two OSes installed and you will access only one or the other... for the moment dualboot is probably your best option...

---

### Post by gn2 on 2006-11-17
Rather than dual-boot you could use a virtual PC with VMWare or Parallels?

What is the problem you are having with Windows, chances are someone on here will know how to fix it.......?

---

