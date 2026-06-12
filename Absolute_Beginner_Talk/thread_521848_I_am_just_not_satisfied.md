---
title: "I am just not satisfied"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jcrespo on 2007-08-09
well, i have messed around with the ubuntu OS for a few weeks now, and i am just not happy with it, i would like to revert back to Windows vista, or at least set up a dual boot between the two, so i can give ubuntu another chance while still using an OS i am comfortable with. i would greatly appreciate any instructions on how to return to the Vista OS, or set up the dual boot.


   Thanks, JC

---

### Post by misfitpierce on 2007-08-09
Im not sure how to dual boot with vista but to completely reinstall vista from vista disc and thats it.

---

### Post by Jimmyfj on 2007-08-09
A few weeks isn't much considering that you are learning a totally different OS - Totally different from Windows that is.

Presuming that you only have Ubuntu installed on your computer you'll need the install DVD for Vista and then boot up your computer on that. Then, when Vista comes to partitioning the hard drive you just follow the instructions on screen. 

To dual-boot Vista/Ubuntu you need to install Vista first then Ubuntu. Remember to defrag your Windows partition before installing Ubuntu in a dual-boot.

---

### Post by jake16424 on 2007-08-09
> **jcrespo said:**
> well, i have messed around with the ubuntu OS for a few weeks now, and i am just not happy with it, i would like to revert back to Windows vista, or at least set up a dual boot between the two, so i can give ubuntu another chance while still using an OS i am comfortable with. i would greatly appreciate any instructions on how to return to the Vista OS, or set up the dual boot.


   Thanks, JC



i agree,, ive been using it for a few days,, dont get me wrong,, im used to STEEP learning curves,, but iwth the right information a steep learning curve is nothing, i have excelled in the past,, but this is dumb,, no universal way todo things, installers dont work. file system is like a bowl of spagettie,, im lost.. 

and, for the dual boot, when you see the bios screen pop up, hit ESC it shoudl enter into a boot menu,, or if not, then its DELETE for you.. then select the hard drive where windows is installed, if that fails,, hit F8 IMMEDIATLY after the bios screen goes away.

---

### Post by jeremy1138 on 2007-08-09
I'm running a dual boot system that I set up using norton partition magic...  It's working fine but i STRONGLY suggest that you just use the grub boot loader that comes with linux and DO NOT use Norton Boot Magic to select your os at start up.  You will need to create 2 partitions on your hard drive, one for linux and the other for windows and install each os on its own partition.  I've been using mine for over a year now with no trouble.

---

### Post by bjarneh on 2007-08-09
hehe, the learning curve is a bit steep on any Linux system I guess, i'm sure there is a lot of thread's here on dual-boot. 

but easiest way:

create some partitions for our different OS's.
(1/2 disk for Vista)
(almost 1/2 disk for Ubuntu)
(500 Mb swap or so)

then install Vista first (I assume you viped that out during Ubuntu install?)

then install Ubuntu, but you have to manuall set mount points on the partitions, default I think vipes the disk and makes it a 100% Ubuntu again :-)

after that has been done, your good to go...

---

### Post by mike102282 on 2007-08-09
If you didn't install Ubuntu on a separate partition you are out of luck you will have to reinstall Vista. What about Ubuntu didn't you like?

---

### Post by Jimmyfj on 2007-08-09
> **jake16424 said:**
> i agree,, ive been using it for a few days,, dont get me wrong,, im used to STEEP learning curves,, but iwth the right information a steep learning curve is nothing, i have excelled in the past,, but this is dumb,, no universal way todo things, installers dont work. file system is like a bowl of spagettie,, im lost.. 

and, for the dual boot, when you see the bios screen pop up, hit ESC it shoudl enter into a boot menu,, or if not, then its DELETE for you.. then select the hard drive where windows is installed, if that fails,, hit F8 IMMEDIATLY after the bios screen goes away.

Maybe Linux just isn't for you then.

@jcrespo

Further on the dual-boot: You shouldn't need to worry about a total wipe out of a new Vista install setting up dual-boot with Ubuntu. Just make sure to let the Ubuntu installer resize your disk then you'll be home safe.

Jake - Don't blame the system, the leaning curve IS steep, but, really, all you need is the time, and a desire to learn what real computing is all about. Not saying that Windows isn't real computing, it's just not FREE computing.

---

### Post by bjarneh on 2007-08-09
installers dont work? usually dpkg/apt is the best tool around

---

### Post by Het Irv on 2007-08-09
I just started using Linux and I really wanted to swich over completely.  But, there is a steep STEEP learning curve.  I run a dual boot w/XP and I think it is the best way to learn or if you have the system resorces look into using Vm-ware to emulate an Ubuntu system.  Keep hope Pinguins will rule the world computers one day.:twisted:

---

### Post by Het Irv on 2007-08-09
> **jeremy1138 said:**
> I'm running a dual boot system that I set up using norton partition magic...  It's working fine but i STRONGLY suggest that you just use the grub boot loader that comes with linux and DO NOT use Norton Boot Magic to select your os at start up.  You will need to create 2 partitions on your hard drive, one for linux and the other for windows and install each os on its own partition.  I've been using mine for over a year now with no trouble.

I am using Acronis Boot Loader...or something like that. I can't remember the name right now.

Anyway it works fine the only problem I have had so far is that it crashed once and had to boot to the repair console and rewrite my MBR.  But after reloading Acronis it has worked fine since

---

### Post by djchandler on 2007-08-09
> **jcrespo said:**
> well, i have messed around with the ubuntu OS for a few weeks now, and i am just not happy with it, i would like to revert back to Windows vista, or at least set up a dual boot between the two, so i can give ubuntu another chance while still using an OS i am comfortable with. i would greatly appreciate any instructions on how to return to the Vista OS, or set up the dual boot.


   Thanks, JC

Wipe your hard drive with dban first. You can get it from sourceforge.

Use your system restore dvd/cds that came with your new computer. If you have an OEM copy of Vista, it's just as easy. After Vista is installed, Ubuntu will install a program called GRUB in the MBR of you HDD from the install disk you used to get Ubuntu in the first place. Then when you boot your computer, you'll have several seconds to choose which OS to boot. The Ubuntu Live CD will sense there's another OS already on the computer, so it will give you the chance to divide your HDD before installing Ubuntu.

If you bought an upgrade to Vista, you'll probably need to re-install XP first, then the Vista upgrade, then run the Ubuntu Live CD.

What problems are you having with Ubuntu?

BTW, if I was going back to Windows, depending on my hardware configuration, I would seriously think about XP if possible instead of Vista unless you have a very high-powered system. That's just my two cents worth of advice.
 :(
DJ

---

### Post by jake16424 on 2007-08-09
no, i downloaded the installer for macromedia and,, nothing happens,, i did everything it said todo, the terminal returns the favor by telling me that the directory doesnt exist.

---

### Post by asmoore82 on 2007-08-09
> **djchandler said:**
> Wipe your hard drive with dban first. You can get it from sourceforge.

Shenanigans!! I can Shenanigans!!

seriously, though, what a waste of development/download time and precious hard drive lifespan.

if you must be paranoid, just boot any Linux LiveCD and

```
~ # dd if=/dev/zero of=/dev/hda
~ # dd if=/dev/random of=/dev/hda
```
until you are blue in the face.

personally, i just 'dd if=/dev/zero of=/dev/hda' for like 2~3 seconds and then Ctrl-C it ...
just enought to zero the Master Boot Record and Partition Tables
so that the next install disk will see an unpartitioned hard drive.

---

### Post by jcrespo on 2007-08-09
> **mike102282 said:**
> If you didn't install Ubuntu on a separate partition you are out of luck you will have to reinstall Vista. What about Ubuntu didn't you like?

i guess i am SOOL on vista, i prefer XP anyway. About what i did not like, for one thing, the steep learning curve, obviously, learning an entirely new OS isn't going to be easy, but this was just ridiculous, especially for a casual gamer/computer user like my self. I tried Linux in the first place because i was unsatisfied by the large amount of bgs in the vista program, but i think that i would rather deal with those, or switch to xp than get used to the complexity of linux. The second thing about linux that i did not like, was that it seemed geared more towards the computer savy than the casual user. It lo0oks like i will have to find my self an XP disc.

---

### Post by Het Irv on 2007-08-09
> **jcrespo said:**
> i guess i am SOOL on vista, i prefer XP anyway. About what i did not like, for one thing, the steep learning curve, obviously, learning an entirely new OS isn't going to be easy, but this was just ridiculous, especially for a casual gamer/computer user like my self. I tried Linux in the first place because i was unsatisfied by the large amount of bgs in the vista program, but i think that i would rather deal with those, or switch to xp than get used to the complexity of linux. The second thing about linux that i did not like, was that it seemed geared more towards the computer savy than the casual user. It lo0oks like i will have to find my self an XP disc.

As to the Casual gamer

If you are a person who does not mind putting gameplay over graphics you definatily need to keep Ubuntu somewhere. There are great games out there for Linux like Tremulous, Open Arena, and Battle for Wesnoth.  Keep in mind that open source tends to have more bugs than corprate sponsered software,  but open source bugs get fixed quicker.

---

### Post by Kedaeus_Sendre on 2007-08-09
I felt the same thing for the longest.. "It's retarded". But I'm much more fond of the Linux environment now that I've learned how to use it in the past 6 months. You can't migrate 100% of your windows experience over night.. it takes time. 

After a while I found myself having more fun tinkering with the OS than I did playing Guildwars or whateverthehell else I was playing at the time. 

I use my Linux box primarily for cruising the internet, music, and movies while i'm playing games on my windows rig. 

I've never was much of a user either - hell, i've installed it 20 different times on 6 different computers before I started to accept it. You've got to find your own reason for using it - instead of trying to replace everything you did in windows. Some things work better.. some don't.

My latest Linux Rig:
 Kubuntu 7.04 Fiesty Fawn
 256 MB Ram
 450mhz AMD K6II Processor
 Refurbished Monitor
 and a Cheap Video card

 The cost? 50 bucks.. (thats the biggest reason I use linux on my secondary computers)
 Works alot better - with less - than my AMD64 bit Dual Core Vista Machine does with more!

 And I suggest Windows 2000 w/ SP4 over XP.. IMO XP was the beginning of Trust Computing - and.. well.. TC = Death.

-Ked

---

### Post by cobrn1 on 2007-08-09
> **asmoore82 said:**
> Shenanigans!! I can Shenanigans!!

seriously, though, what a waste of development/download time and precious hard drive lifespan.

if you must be paranoid, just boot any Linux LiveCD and

```
~ # dd if=/dev/zero of=/dev/hda
~ # dd if=/dev/random of=/dev/hda
```until you are blue in the face.

personally, i just 'dd if=/dev/zero of=/dev/hda' for like 2~3 seconds and then Ctrl-C it ...
just enought to zero the Master Boot Record and Partition Tables
so that the next install disk will see an unpartitioned hard drive.

I like that idea - that's very clever... I'd have used my trusty Gparted CD to delete all current partitions, but your idea is very inventive... very nice - kudos! :):):)

Definately don't bother with the DBAN, you only really need it if you want to wipe the hard drive so forensics can recover anything (ie, if the feds or RIAA come a knocking...)



Linux does take time to get used to... it is better in many ways, and the more you learn about it the more you'll appreciate it (there's so much good to be said about the free software movement and open source...).However, I'd really recommend the dual boot to get used to it - ease the transition.


Oh, and a steep learning curve is made more bearable by lots of help - it's still going to be a steep curve tho... You just need to play around with it and get used to it... If you're not prepared to play about with the new OS, then why did you want to install it in the first place (not an unreasonable question... I'm not even saying linux isn't for you, like many seasoned linux veterans would ;) (not that I'm a seasoned vet by any means...:)), but if you don't want to play with it, why did you bother in the first place)

---

### Post by vexorian on 2007-08-09
You are the less likely to accept Linux, because you think you are great with computers, but you are only great with windows, phrases like "the file system is like spaguetty" shows so.

So, Linux is not for you, and possibly mac isn't either, do the world a favor and reformat your hard drive then install windows XP, not vista. It should do it. (Just use the windows XP for it, the "super user friendly"  text mode installer should allow you to reformat the computer 

If you want to experiment with ubuntu once in a while, I would recommend just installing xubuntu in a virtual machine in your comp. No need for dual boot if you don't really take it seriously.

---

### Post by MrKlean on 2007-08-09
Ppl say there's a steep learning curve !  Think of how LONG ago you started Windows !!  I started with dos 3...ummmmmmm...I think my learning curve with windows has been....ummmmmm.... 15 yrs LOL!!   I've been using Linux for abou3 months and loving it.  Plusssss, I've learned more about puters than I did before.  Come to think of it..I really only learned to use a curser and mouse !!  Not much else ; )   Just my 2 cents !!

---

### Post by cobrn1 on 2007-08-10
> **MrKlean said:**
> Ppl say there's a steep learning curve !  Think of how LONG ago you started Windows !!  I started with dos 3...ummmmmmm...I think my learning curve with windows has been....ummmmmm.... 15 yrs LOL!!   I've been using Linux for abou3 months and loving it.  Plusssss, I've learned more about puters than I did before.  Come to think of it..I really only learned to use a curser and mouse !!  Not much else ; )   Just my 2 cents !!

Ah hah - but you see, if you learn it all over several years, then it's not a steep learning curve, more of a gentle incline.

However, people (rightly or wrongly) expent to just install linux and be able to do absolutely everything, fix any problem right away, and in general, do things exactly the same way.

You see the difference. Learn OS in several years, not so steep. Learn OS in 15 mins, VERY steep...

---

### Post by ukulele_ninja on 2007-08-10
It doesnt sound like you have tried very hard to learn the OS then. Im only into my second week with Ubuntu and personally coming from a windows background, I love it! Ive found that the best way to learn it is to keep asking questions on here! No one seems to mind answering questions for you no matter how simple, so get to asking.... or give up and go back to vista but good luck with that. I just couldnt live with myself knowing i had given up on an opportunity to learn something new....:(

---

### Post by in_omaha on 2007-08-10
I have been using Ubuntu for a little over a year now and just love it. I have played around with Linux for a few years now trying out different ones, but seem to have settled down with Ubuntu. I can boot XP on linux using Virtualbox if i have to for something. As far as gaming goes, being able to play Call of Duty 2 is all I need and wine does just fine with that. I will be staying. Linux has come a long way!!! It does take some work, but anything worthwhile does!

---

### Post by cobrn1 on 2007-08-10
As many have pointed out, why are you bothering with vista?

XP does everything you need (apparently) and the next version of windows will supposedly be coming out in 3 yrs time... Unless you are a games and must play DX10 games (you could probably get away without DX10 for the next 3 years, given its current popularity) you could just cut out vista alltogether and wait for the next readmond offering...

Of course by then ubuntu will have had 6 more releases or so, and vista+1 won't be able to compare, but whatever...

Interesting question really, who thinks that open source will rule one day (soon)? I ask because it dawned on me this moring that the only way for OSS is up. Linux is already better in near every aspece. The next few years should improve things dramatically. Vista is forcing people away, and linux is ending up on everything from phones, to ipods and toasters...
It's starting to look like microsoft is going to be left in the dust very soon (but maybe I'm over optemistic - whatdayathink?)

---

### Post by jenson on 2007-08-10
I have just installed Ubuntu for one day! I have not been using it much yet. But I always cant control myself from logging in to Ubuntu and play around with it, it simply rocks! And if not only for the tasks that can only be done in Windows XP, I would have done a clean install of Ubuntu, instead of dual boot now. I find that I like Ubuntu now. I really want to see Ubuntu getting stronger and better and one day, to dominate the PC world and replace our dearest M$ =X Yes a bit over optimistic. But only when there are dreams there are miracles/possibilities/hopes!!!

I know the learning curve for a new OS is steep, the command looks a bit different to me but I love to learn how to use them with Ubuntu, I simply cannot resist the beauty of Linux and Ubuntu! Cool!

Give yourself 6 months or at least 3 months, my friend, you will love it!

Regards,
Jenson

---

### Post by mike102282 on 2007-08-10
> **cobrn1 said:**
> Ah hah - but you see, if you learn it all over several years, then it's not a steep learning curve, more of a gentle incline.

However, people (rightly or wrongly) expent to just install linux and be able to do absolutely everything, fix any problem right away, and in general, do things exactly the same way.

You see the difference. Learn OS in several years, not so steep. Learn OS in 15 mins, VERY steep...Yes, but if you use kDE the curve isn't nearly as steep because it is pretty much set up just like windows.

---

### Post by sparau on 2007-08-10
I've only just started with ubuntu - however i do have a background of off and on coding in *nix for 10 or so years in server environments.

But by far the best thing about *nix and ubuntu in particular is the community - so many great walkthroughs and help.

I haven't come across a problem yet that 1 google search and 1-10 cut and paste's havent fixed :) :)

Very impressed at what this OS is becoming - Kudos to all.

---

### Post by Dai Bando on 2007-08-10
I have been using linux for the past five years After being with Windows from 3.1. I installed Fiesty in April and I am glad to say that it does every thing for me that Windows did. I am 87 years old and if I can do it I can only think modern youth have no stamina. ( Prepare for flame war ).

---

### Post by bobpur on 2007-08-10
I am, also, new to linux (two years or so). When I get frustrated with Ubuntu or any distro, I remember the fun I used to have trying to program the VCR or unlocking the secrets of my TV remote control.
As for dualbooting, I suggest using two different hard drives. One for each OS. 
I've built several machines using this arrangement and have had fewer problems than trying to put both OS's one drive.
Install windows first and then linux (Ubuntu) as Windows tends to overwrite GRUB rendering  linux useless.

                                                              Good luck!

---

### Post by creedog on 2007-08-10
> **djchandler said:**
> Wipe your hard drive with dban first. You can get it from sourceforge.

Use your system restore dvd/cds that came with your new computer. If you have an OEM copy of Vista, it's just as easy. After Vista is installed, Ubuntu will install a program called GRUB in the MBR of you HDD from the install disk you used to get Ubuntu in the first place. Then when you boot your computer, you'll have several seconds to choose which OS to boot. The Ubuntu Live CD will sense there's another OS already on the computer, so it will give you the chance to divide your HDD before installing Ubuntu.

If you bought an upgrade to Vista, you'll probably need to re-install XP first, then the Vista upgrade, then run the Ubuntu Live CD.

What problems are you having with Ubuntu?

BTW, if I was going back to Windows, depending on my hardware configuration, I would seriously think about XP if possible instead of Vista unless you have a very high-powered system. That's just my two cents worth of advice.
 :(
DJ


dban... is a D.O.D. wipe realy necessary :lolflag:

---

### Post by Bartender on 2007-08-10
> **bobpur said:**
> I am, also, new to linux (two years or so). When I get frustrated with Ubuntu or any distro, I remember the fun I used to have trying to program the VCR or unlocking the secrets of my TV remote control.  As for dualbooting, I suggest using two different hard drives. One for each OS.  I've built several machines using this arrangement and have had fewer problems than trying to put both OS's one drive.  Install windows first and then linux (Ubuntu) as Windows tends to overwrite GRUB rendering  linux useless.

Pesky VCR controls anyways...
I agree with the two drives suggestion.  With one big modification.  If you have a relatively modern BIOS, there should be a keystroke you can enter as the PC is booting - F8 on my ASUS board but there are others - that drops you to a screen asking which device you want to boot from.  

This is NOT the same as going into your BIOS every time and re-arranging the boot device.  

What I'm talking about is one keystroke to stop the boot process, and a couple of clicks up or down to pick the boot device.  Just as easy as using GRUB, but the big difference here is you install Windows entirely to one drive and Linux entirely to the other.  No messing around with the Windows MBR or GRUB.  If you have that function in your BIOS it's as simple as unplugging the Windows HDD (just to make sure) plug in a second HDD, install Ubuntu entirely to that drive, then re-arrange the drives and jumpers appropriately.  If it's an IDE box, Windows at the primary clip and Linux at the secondary clip.  Easier with SATA.

And everyone keeps talking about a steep learning curve.  That phrase is intimidating to the newb.  It's not like 8th grade was good enuf for Windows and now you're advancing to college.  As long as you don't have to do some weird tweaking to get your wireless or printer or whatever working, it's mostly just plain old unfamiliarity.  Unfamiliarity can be overcome with a few weeks of mousing around and seeing where you go.

Not a big deal.

---

### Post by lepz on 2007-08-10
> **Dai Bando said:**
> I have been using linux for the past five years After being with Windows from 3.1. I installed Fiesty in April and I am glad to say that it does every thing for me that Windows did. I am 87 years old and if I can do it I can only think modern youth have no stamina. ( Prepare for flame war ).

Wohoooooooo great stuff Dai Bando, you have hit the nail right on the head. When I first started I was cursing this and that because I didn't know what I was suppose to do, I wanted everything NOW. Life is not like that, it takes time and the learning is ongoing but when I look back at my windows days it sure as hell is worth it. I'm still a n00b and will probably still be a year from now but I learn a little more each day. ;)

---

### Post by myk.dinis on 2007-08-10
Wow...87...that's awesome...

I've been with microsoft since dos 3(and change) and I started using linux with whatever the pre-slack version was using I think blackbox as my window manager...

I knew nothing going into dos and had to re-install like 20 times before it did what I wanted without a problem...same with every version of windows...

same with every version of linux...

I think if you want a safe, no config, works-outta-the-box solution go with a mac... or start fresh with ubuntu with no other OS experience...every OS is different...that's what makes them fun...

If you have a zeal for computing or just a desire to learn then I think that anything you install will be a joy and a heartache...

Remember that telephones used to be the big scary electronic device...people used to keep them in a special closet next to the foyer in their houses... Kinda like the pc in the office...

You can still be a tinkerer with the phone system...I do that today...
But you can also jut buy a phone (yep, even a cell phone) and it just works...

Many people with a desire to experiment with technology aren't satisfied with "just works"...
We want to know why, how and if we can make it better...or make it do something it wasn't made to do (see the nokia as an optical mouse hack) ...

Remember that unless you have mission critical software running, playing around with the OS isn't life or death...

Just back-up...All the time! :)  or make sure you have a spare drive laying around (jump drive, USB portable HDD, or the like) and leave all your personal stuff there, pr0n, word docs, resumes, movies, music, etc...

I'm using a dual boot setup, that looks like this: WinXp Sp2 - 10GB - NTFS. Data Hard Drive - 40GB - FAT32 (has the documents and settings folder from xp on it), Ubuntu Feisty - 80GB - ext3 with a / of 15GB, a swap of 1GB, and a /home of 64GB....

That way I can read/write data in both OS's to a central location without having to worry about permissions and what not...I can re-install xp or linux at will and my docs are safe...

You're wondering why I didn't make the 80GB the shared drive, well I'm keeping the 80GB as Linux forever and I only have to worry about reformatting the / partition if I ever have a non-recoverable filesystem error... And I'm going to be upgrading the 10GB disk to another 80 and I'll move win to the 40GB and have the other 80 as my shared drive...

I finally got it right recently and I love it...

Give it time (to original poster) how long did it take you to learn how to talk...I bet you have all sorts of fun with that now, right?

myk

---

### Post by jenson on 2007-08-12
> **Dai Bando said:**
> I have been using linux for the past five years After being with Windows from 3.1. I installed Fiesty in April and I am glad to say that it does every thing for me that Windows did. I am 87 years old and if I can do it I can only think modern youth have no stamina. ( Prepare for flame war ).

Wow Dai Bando,

I really salute you! You are the role model of all of us and newb. Great reply and this would definitely motivate more people to learn Linux/Ubuntu well and start loving it. I'm already deep in love with Ubuntu now despite the fact that I still need to get used to the days without using Windows XP. I dual boot my pathetic 40GB hard disk drive of my toshiba notebook and I hardly go back to Windows XP except for some PC gaming and programming on Windows platform. I'm so far ok with working on Linux platform for all the tasks I used to do it in Windows XP.

However I need to find out how to uninstall the java runtime environment that I accidentally installed onto  my Desktop using manual installation. Now I'm a bit regretted for not using the package manager instead. My fingers just get too itchy tying to fix things up on my own. Have a lot of fun playing around.

But you know, as a newbie, I always dont know the correct how-to, luckily I did not manage to mess the whole Ubuntu up to destruction :o :lolflag:

Regards,
Jenson

---

### Post by jcrespo on 2007-09-09
Sorry to up my old thread, but after another month of Ubuntu, i am just not happy with it, and even worse, it doesnt appear that my laptop came with nay sort of reboot disc for vista. i really need a way to remove ubuntu and get some sort of windows os back onto it. and for the record, i do not think i partitioned my hard drive when i installed Ubuntu. I really need help, so if you have anything at all to add, please, post it up.

---

### Post by porcorosso on 2007-09-09
> **jcrespo said:**
> Sorry to up my old thread, but after another month of Ubuntu, i am just not happy with it, and even worse, it doesnt appear that my laptop came with nay sort of reboot disc for vista. i really need a way to remove ubuntu and get some sort of windows os back onto it. and for the record, i do not think i partitioned my hard drive when i installed Ubuntu. I really need help, so if you have anything at all to add, please, post it up.

If your system came with Vista pre-installed (in other words, an OEM installation) then the manufacturer should be happy to provide you with an installation disc. Just call their customer support line. (IIRC Microsoft's arrangement with OEM Windows providers is that they are REQUIRED to provide such discs upon request of the customer. There might be a small charge for media / shipping / handling, but that should be about all there is to it.)

---

### Post by jcrespo on 2007-09-09
cool, so if i call up microsoft cs and tell them that i need an install disc and provide like a serial number or something, they will send me an install disc? thanks so much.

---

### Post by oilchangeguy on 2007-09-09
> **jcrespo said:**
> cool, so if i call up microsoft cs and tell them that i need an install disc and provide like a serial number or something, they will send me an install disc? thanks so much.

uh, no. re-read the post. you were advised to call cs of whoever made your computer. not microsoft.

---

### Post by nonewmsgs on 2007-09-09
> **porcorosso said:**
> If your system came with Vista pre-installed (in other words, an OEM installation) then the manufacturer should be happy to provide you with an installation disc. Just call their customer support line. (IIRC Microsoft's arrangement with OEM Windows providers is that they are REQUIRED to provide such discs upon request of the customer. There might be a small charge for media / shipping / handling, but that should be about all there is to it.)

i even called hp up when my laptop was still under warranty and asked them to replace cd1 and they told me no.  most of the major players put a way to make system cd/dvds an option in the start menu, but if your hard drive crashed before you made them, or the discs messed up, you're ******.

good luck getting back to microsoft without paying again.  their system is designed to make you buy it again.

---

### Post by jenson on 2007-09-10
> **jcrespo said:**
> Sorry to up my old thread, but after another month of Ubuntu, i am just not happy with it, and even worse, it doesnt appear that my laptop came with nay sort of reboot disc for vista. i really need a way to remove ubuntu and get some sort of windows os back onto it. and for the record, i do not think i partitioned my hard drive when i installed Ubuntu. I really need help, so if you have anything at all to add, please, post it up.

Btw, I'm not sure how the Vista works, for my case, I used to borrow a Windows XP CD from my friend, and look up for the product key on the label beneath my laptop. You should be able to install with the key there.

I think it shouldn't be any problem for you to install Ubuntu on almost all of the laptops in the market? Or you just don't like Ubuntu and prefer to go back to Windows Vista?

Hmm, I'm sure it would be better for you to look for someone living nearby your area to go to your house and help you on installing Ubuntu, since it looks like you are not able to make it working 100% with the helps provided by experts here?

Regards,
Jenson

---

### Post by porcorosso on 2007-09-10
> **nonewmsgs said:**
> i even called hp up when my laptop was still under warranty and asked them to replace cd1 and they told me no.  most of the major players put a way to make system cd/dvds an option in the start menu, but if your hard drive crashed before you made them, or the discs messed up, you're ******.

good luck getting back to microsoft without paying again.  their system is designed to make you buy it again.

Recovery partition or no, an end user who purchases a computer with an OEM installation of Windows these days is entitled to an OEM version installation CD of the OS. The rules were less clear in years past, but I've heard of no one being refused this courtesy recently, even if they had the original disc and lost it, by customer service from any of the companies with whom I've dealt -- and they include HP/Compaq, Dell, Asus, Toshiba, Alien (Don't ask.), Panasonic -- to name the ones I've dealt with for end users in the last couple of years.

If the OEM won't honor the request, you can also contact Microsoft CS. They take an interest in this sort of thing. If you can provide the key and proof that you are the rightful owner of the system to which that OEM key is tied, you will be able to get replacement media. It may not be free, but it won't be more than a few bucks for cost of materials / shipping / handling.

Oh, and it's important to get the OEM OS installation disc -- NOT the hokey "restore disk" which provides you with a crappy OEM installation of the OS which includes all of the junk software they should never have even thought of sticking on the system originally. I think a lot of people would be surprised at how well some versions of Windows work when they're not hamstrung by crapware.

---

