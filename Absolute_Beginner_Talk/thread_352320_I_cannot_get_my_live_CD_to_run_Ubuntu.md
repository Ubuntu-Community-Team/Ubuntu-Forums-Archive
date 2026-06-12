---
title: "I cannot get my live CD to run Ubuntu"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-03
Hi

I have just downloaded and burnt a copy of ubuntu (6.10 ).

I can boot from the CD and get the menu (start or install ubuntu etc.) but when I select the 'start or install' option, I get some messages about loading the kernel, the screen goes black, the computer appears to reboot (I get the Dell loading BIOS screen and then I go straight back to the live CD menu again.

Can anyone help?

Thanks

---

### Post by dexter on 2007-02-03
> **ubername said:**
> Hi

I have just downloaded and burnt a copy of ubuntu (6.10 ).

I can boot from the CD and get the menu (start or install ubuntu etc.) but when I select the 'start or install' option, I get some messages about loading the kernel, the screen goes black, the computer appears to reboot (I get the Dell loading BIOS screen and then I go straight back to the live CD menu again.

Can anyone help?

Thanks

Have you tried the safe mode as well ?

---

### Post by xmastree on 2007-02-03
> **ubername said:**
> I can boot from the CD and get the menu (start or install ubuntu etc.)
What CD did you burn? It should just boot right into the GUI, with the install launcher there on the desktop.

---

### Post by ubername on 2007-02-03
I burnt ubuntu-6.10-desktop-i386.iso using isoburner.

Thanks

---

### Post by ubername on 2007-02-03
> **dexter said:**
> Have you tried the safe mode as well ?

I don't know how to do that, I'm afraid

---

### Post by steve.horsley on 2007-02-03
Press F1 instead of enter when the CD boots, I think. There are several help screens on F1, F2, F3 etc.

---

### Post by Sean Heron on 2007-02-03
It may have changed since dapper (you have edgy, the latest version), but in my version (dapper) when it give me the options: Install or run Ubuntu, it also says:
-run Ubuntu in safe graphics mode
-do a memory test (or something like that)
-check the Cd for errors.

What the fellow above meant is, have you tried the "run Ubuntu in safe graphics mode" yes (because you can install from that as well, I know I have :D).

P.S. I myself have tried the version 6.10 (edgy) ubuntu live cd, and I got a similiar error to yours on both safe graphics and normal mode (crashes just before the login screen). I currently have Kubuntu 6.06 (dapper) installed, after running the live CD in "safe mode".
Regards Sean

---

### Post by ubername on 2007-02-03
> **Sean Heron said:**
> It may have changed since dapper (you have edgy, the latest version), but in my version (dapper) when it give me the options: Install or run Ubuntu, it also says:
-run Ubuntu in safe graphics mode
-do a memory test (or something like that)
-check the Cd for errors.

What the fellow above meant is, have you tried the "run Ubuntu in safe graphics mode" yes (because you can install from that as well, I know I have :D).

P.S. I myself have tried the version 6.10 (edgy) ubuntu live cd, and I got a similiar error to yours on both safe graphics and normal mode (crashes just before the login screen). I currently have Kubuntu 6.06 (dapper) installed, after running the live CD in "safe mode".
Regards Sean

Ah now I understand! Yes, I've tried the safe graphics mode and exactly the same happens.

---

### Post by bodhi.zazen on 2007-02-03
I would presume either you have a bad burn or hardware incompatibility.

First, did you check the md5 sum of the downloaded iso and check your brun ?

Second, computer info. CPU ? Monitor ? Graphics card ?

---

### Post by ubername on 2007-02-03
> **bodhi.zazen said:**
> I would presume either you have a bad burn or hardware incompatibility.

First, did you check the md5 sum of the downloaded iso and check your brun ?

Second, computer info. CPU ? Monitor ? Graphics card ?

I don't know how to check the md5 sum (I don't even know what it is!)

Computer is Dell Dimension DIM4600 P4 3.00GHz 512Mb RAM

Monitor is Dell 17 flat screen

Video card is NVIDIA GeForce FX 5200

Thanks for the help so far

---

### Post by xpod on 2007-02-03
Welcome to the forums ubername

It could well be a dodgy burn as bondi mentioned but if you dont have a reasonable amount of ram then that might also be the cause of your problems.Even  people with decent specs though can have issues with live cd`s so your not  alone m8

Might be a case for the alternate cd  if all else is failing but wait and see what these guy say first:) 
Good luck

EDIT:that answers that then:-)
EDIT2:try burning at a slower speed possibly....x4 ?

---

### Post by Sean Heron on 2007-02-03
Before going to the bother of burning a new CD, I´d run the function : Check if CD has errors (same place as "safe grafics mode" :D ) if edgy still has that. I would have asumed that can be trusted to tell you if the CD is OK or not ...

---

### Post by bodhi.zazen on 2007-02-03
> **ubername said:**
> I don't know how to check the md5 sum (I don't even know what it is!)

Computer is Dell Dimension DIM4600 P4 3.00GHz 512Mb RAM

Monitor is Dell 17 flat screen

Video card is NVIDIA GeForce FX 5200

Thanks for the help so far

OK the problem may either be a bad burn (it happens).

Start by checking the md5sum of the iso

For basic info see here: [http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

md5sum confirms the integrity of your downloaded iso.

Does your CD burning software check the integrity of the burn ?

Also, as xpod and others may have indicated, if the md5sum is OK, burn the iso to cd at a slower speed ( I assume you know to burn the iso and not copy it as data to a cd ???)

If that fails, you may have a problem with the nvidia driver, but that seems less likely as in that event the CD should boot and you would get an error message about X.

HTH

Hi xpod :p

---

### Post by Infernal Byte on 2007-02-03
It might be a problem with your Dell Bios, even though your able to boot automatically from the CD, try pressing F2 or F5 or whatever it is on a Dell to get to the boot menu and manually select boot from your CD.

...

---

### Post by ubername on 2007-02-03
Many thanks to you all for your help. I will try the suggestions and get back to you.

---

### Post by ubername on 2007-02-03
> **bodhi.zazen said:**
> OK the problem may either be a bad burn (it happens).

Start by checking the md5sum of the iso

For basic info see here: [http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

md5sum confirms the integrity of your downloaded iso.

Does your CD burning software check the integrity of the burn ?

Also, as xpod and others may have indicated, if the md5sum is OK, burn the iso to cd at a slower speed ( I assume you know to burn the iso and not copy it as data to a cd ???)

If that fails, you may have a problem with the nvidia driver, but that seems less likely as in that event the CD should boot and you would get an error message about X.

HTH

Hi xpod :p

OK the md5sum (of the .iso on my PC) is b950a4d7cf3151e5f213843e2ad77fe3
but I can't find anything to compare it with. I use Isoburner, I don't know if it checks the integrity of the burn. I am just about to burn again at a slower speed.

---

### Post by ubername on 2007-02-03
While my burn is happening, can I ask a further question?

I followed some advice from the web (I will post a link if anyone would like) which allowed me to create something called a Systemrescue CD which booted to Linus, then with a bit of messing I got to run something called gparted.

I originally had a single 79GB windows partition. I now have (and don't blame the instructor, this was me doing my thing) a 3GB FAT32 partition at the front of the disk, a 7GB ext partition (I think it's ext I can't see it in windows but that's what the instructions said. I assumed it was where I was going to put ubuntu) and a 69 Gb Windows partition following that.

How many miles off course am I?

---

### Post by psycosmyth on 2007-02-03
The Geforce cards had some issues but I forgot which one. Just a thought.
Don't give up, just keep posting and we will help you until you get what you need to know.

---

### Post by ubername on 2007-02-03
> **psycosmyth said:**
> The Geforce cards had some issues but I forgot which one. Just a thought.
Don't give up, just keep posting and we will help you until you get what you need to know.

Thanks

Would the start menu appear correctly (which it does) if there were issues with the GeForce card?

BTW I've re-burned at a slower speed (x2, at least that is what I specifed, I've no way that I know of to check) and I am still getting the same problem.

Can someone tell me what normally happens when you boot from the 6.10 disk and select 'start or install ubuntu'?

---

### Post by ubername on 2007-02-03
> **Sean Heron said:**
> Before going to the bother of burning a new CD, I´d run the function : Check if CD has errors (same place as "safe grafics mode" :D ) if edgy still has that. I would have asumed that can be trusted to tell you if the CD is OK or not ...

Hi 

Sorry for not getting back sooner. I tried the 'check CD' function and it does exactly the same thing: reboots and goes to the start menu. (I am calling it the start menu for simplicity; It has the options to 'start or install..., start in safe graphics mode, check CD, memory test or boot from first hard drive)

---

### Post by ubername on 2007-02-03
Meanwhile I am downloading v6.06 LTS to see if that will work.

I am such a novice at Linux that some of you may be thinking 'Why is he persevering with ubuntu; why not get another distro?' 

The reason, odd as it may sound, is that I spent 7 years living in South Africa and the word Ubuntu means something to me.

That has to be one of the weakest reasons for picking one piece of software over another, but it does it for me!

---

### Post by bodhi.zazen on 2007-02-03
> **ubername said:**
> OK the md5sum (of the .iso on my PC) is b950a4d7cf3151e5f213843e2ad77fe3
but I can't find anything to compare it with. I use Isoburner, I don't know if it checks the integrity of the burn. I am just about to burn again at a slower speed.

That is the correct md5sum for the Edgy i386 desktop iso.

For LTS : 

fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso

---

### Post by ubername on 2007-02-03
> **bodhi.zazen said:**
> That is the correct md5sum for the Edgy i386 desktop iso.

For LTS : 

fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
Thanks bodhi,

I am currently having problems writing the 6.06 iso to a cd! If it's not one thing, it's another.

---

### Post by ubername on 2007-02-03
YEEHAA!

Posting from an ubuntu booted machine from the hard drive!

Thanks to everyoone. I can't remember exactly whose advice got me thorugh but it was a team effort so thanks a mill!

Now wait for the flood of calls for help as I actually get using the thing!

Cheers

Although it's 6.06 not 6.10

---

### Post by xmastree on 2007-02-03
Great feeling, isn't it? Congrats, and welcome aboard.

:guitar:

---

### Post by ubername on 2007-02-04
> **xmastree said:**
> Great feeling, isn't it? Congrats, and welcome aboard.

:guitar:

Yup. it is certainly a good feeling! It also runs so much faster than XP home does. I am v. happy.

---

### Post by ubername on 2007-02-12
> **ubername said:**
> I don't know how to check the md5 sum (I don't even know what it is!)

Computer is Dell Dimension DIM4600 P4 3.00GHz 512Mb RAM

Monitor is Dell 17 flat screen

Video card is NVIDIA GeForce FX 5200

Thanks for the help so far

I burnt another 6.10 CD and got a bit further: The kernel loaded and I got to a desktop. However 'Install' from there caused the same problems; clicking it  causes  a reboot to the CD install menu.

That said, I am now a way down the line with my 6.06 install, and don't see anything I am missing. My current plan is to use this setup until I know why I want 6.10 and then work on upgrading / overwriting.

See you later!

---

