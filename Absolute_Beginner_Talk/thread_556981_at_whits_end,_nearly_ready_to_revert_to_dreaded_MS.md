---
title: "at whits end, nearly ready to revert to dreaded MS Vista"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-09-22
so I have been a happy user of ubuntu since Xmas 2006, not a long time. first on Dapper and for the last two weeks or so on Feisty

but I have been having numerous problems and it is driving me nuts.

1. 5 ppl use the machine. If I log onto one of the other libraries (actually, what is the place where eac. person logs onto called.. ie. /home/user ? - library is just a literal translation from Hungarian, but it sounds too MS to me.) everything is fine in 3 of them.

but in mine, my son's and in a sixth one used for testing things, there is no sound... the little voume control icon sends an error msg... *no volume control Gsteamer and plugins and/or devices can be found.

what to do about this? why is it working for some of the users and not for others?


2 Opera will not launch

3. Epiphany will not launch

I had this problem in Dapper and a friend was taking care of it and installed Feisty but that did not solve the problems, they still do not launch.

4. I thought I would reinstall the entire system. I downloaded the desktop iso but when I checked it with md5sum it never had the correct hash, I tried several times.

5. I have a CD that my friend gave me, but I cannot get the machine to boot form that CD, so I cannot instlal everythign from that either.

6. Actually the original issue was an Xserver thing and that is what my friend/collegue was taking care of when he installed Feisty for me. 

7. windows/panels - When I log on to my onw *library* I can open everything, cept opera and epiphany, but whatever window is open moves to the upper left and I cannot move it, resize it or see what is behind it. I cannot see the top panel with the Ubuntu menues -Appliations, Places, System.  

8. none of us have the synoptic/repositories, or whatever that thing is called... for some reason it did not install with Feisty.

PPl here have been very helpful in the past, one of the reasons I have staye dwith Ubuntu but I really need a computer that runs smoothly and that we can all use... Nothing worse then sitting down to prepare for a class you have to teach in 3 hours and th ecomputer not working, or having sutdent papers to correct but no computer to do it on, or to have a translation job due in an hour but no computer....

please help me solve these issues.. I really do want to keep this house a MS Free Zone!!!!!! It's an ethical issue with me.

robi

---

### Post by James7 on 2007-09-22
As far as booting from the CD goes, do you have your BIOS set to boot first from CD? When you first start your computer, you have a second or two to enter the BIOS. Usually there is a splash screen (mine says Toshiba) and you can hit a certain key (mine is F2, but others may be different, like ESC or something---sometimes it is noted on the splash screen itself). This should let you into the BIOS. There you can go to the 'boot order' section and see if it is set to boot first from CD. It may be that it is set to boot first from your hard drive....

---

### Post by armandh on 2007-09-22
you may not have better luck with vista.
when known good disks will not boot suspect hardware settings/problems.
when a user that is only for testing has the problems suspect cumulitive mistakes. I suggest delete the old tester user/add new tester user
if you have really messed it up reload with 7.04 desktop [once you can boot]. 
remember machines in mission critical must run use need to be left in the simple, stock and plain configuration.
but if you must move to windows dont forget all the free window apps you find on line.

---

### Post by beanco on 2007-09-22
I entred BIOS, mine uses teh Del ky, went ove to the boot option, then down to the one that said CD or whatever it was... I chose to boot from CD, extied that and chose save settings....

the computer booted again but form the harddrive, not from the CD!!!


I really do not want to use VISTA. I do not want to use any MS stuff if I can avoid it...


robi

---

### Post by floke on 2007-09-22
Try creating another user with plain settings and see if their sound works -- if so just shift all your stuff over to the new account.

For booting you might have to press something like F1 etc at startup to get a boot menu -- google your PC model to find out.

Before ditching ubuntu for MS, try another distro - there's loads out there - MEPIS has very good hardware support, Linux Mint is very good and is based on ubuntu. See [www.distrowatch.com](www.distrowatch.com)

---

### Post by MrKlean on 2007-09-22
For the CD.. trying burning one at a slower speed.  It may have been corrupted at a high speed !

---

### Post by beanco on 2007-09-22
> **floke said:**
> Try creating another user with plain settings and see if their sound works -- if so just shift all your stuff over to the new account.

For booting you might have to press something like F1 etc at startup to get a boot menu -- google your PC model to find out.

Before ditching ubuntu for MS, try another distro - there's loads out there - MEPIS has very good hardware support, Linux Mint is very good and is based on ubuntu. See [www.distrowatch.com](www.distrowatch.com)

created a new user, but how to move everything over there? but this will not solve the original problem of why the original user was corrupted!!!


I entered the bios set up using del. are you saying that in addition to that F1 may take me to a different boot up menu?


I really like Ubuntu so I am not too interested in changing distros!

robi

---

### Post by alienexplorers on 2007-09-22
Not to harp upon what MrKlean said, but did you burn your disk at the slowest speed your cd-writer will burn the .iso......  Did you check the MD5 Checksum.....  Any of these could cause the problems you are experiencing.

---

### Post by beanco on 2007-09-22
> **alienexplorers said:**
> Not to harp upon what MrKlean said, but did you burn your disk at the slowest speed your cd-writer will burn the .iso......  Did you check the MD5 Checksum.....  Any of these could cause the problems you are experiencing.

The disk was burned by a colloweague, in the IT department , I assume he burned it slowly. I will not be able to ask until Monday,

I will try to check the MD5 momentarily... but I was having problems with it last time I chekced.

namely, everyime I cd to the dvd/cd drive the file cannot be found. When I 'ls' the drive it lists a file that it certainyll not on the CD int e drive but one that was burned months ago....


[PHP]test@robi:/cdrom$ ls
eves munka[/PHP]

of course I could be doing this all wrong.....


robi

---

### Post by alienexplorers on 2007-09-22
Some light reading:
```
Burning CDs in Linux: Tips and Tricks
Making Sure the Download's Right

Dee-Ann LeBlanc
Tuesday, July 30, 2002 11:39:36 AM

Before you even get to the point of burning a CD-ROM, it's a good idea to check whether or not the complete file downloaded properly. This policy is especially a must when it comes to large files such as ISOs for a Linux distribution. In cases like this, many FTP and web sites offer what's called a file containing what's called an MD5 checksum.

A checksum is simply the number of bits that this file is supposed to contain, but just used by itself provides no extra assurance that a file hasn't been tampered with, since anyone could just change the value stored in the checksum file. Combining MD5 with the checksum issue does add a level of security. An MD5 checksum is a 128-bit set of characters that are produced using the file's original contents, and can be reproduced just as any fingerprint can be taken twice.

So between being worried that a file hasn't fully arrived, and wanting to be sure that the file you got, say, off a mirror or a third-party site hasn't been tampered with, you can get the original MD5 checksum value from the file's main provider. Your MD5 checksum checker will then calculate the checksum that should be assigned to the file you downloaded, and compare it to the file you grabbed that contains what the MD5 checksum should be.

If they don't match, then something's wrong.

You don't need a fancy tool to check an MD5 checksum. You don't need to download anything, either. The program md5sum comes with most mainstream Linux distributions, and if it's not installed by default it's probably on your distro's CD-ROMs somewhere. First download the file itself, and then edit the corresponding file containing the MD5 checksum, or copy and paste the MD5 checksum from the web site into a file. After the MD5 checksum in the file, put the name of the file you want to check, and the path if it's not in the same directory as the MD5 checksum file.

You then use this program in the format:

md5sum --check MD5checksumfilename

The md5sum program runs a MD5 checksum on the file specified with MD5checksumfilename, and then compares its answer to the MD5 checksum in the file.

For example, I might download nethack-3.4.0-1.i386.rpm. On the site where I download this, there's a list of MD5 checksums for all of the different versions of this file, including:

20cc27bee69ba82adbd60df04efb9a7a  ./binaries/linux/nethack-3.4.0-1.i386.rpm

The left portion is the MD5 checksum, and the right portion is where this file is on their particular site. However, when I download this file, I save it just in my home directory. So I make a text file in the same directory containing only the following:

20cc27bee69ba82adbd60df04efb9a7a  nethack-3.4.0-1.i386.rpm

After I save the text file as nethacksum, I type :

md5sum --check nethacksum

The result is just what I was hoping for:

nethack-3.4.0-1.i386.rpm: OK

```

---

### Post by alienexplorers on 2007-09-22
Some more info:
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by beanco on 2007-09-22
i tried downloading the live Cd myself, I ran the md5sum command. the hash it produced did not match the ones on the ubuntu site.

I mentioned this to my collogue and he burnded me a CD form his comptuer.

I wanted to check the has on it just now and I got that msg I posted in my last reply.


so I have a CD in my computer. I want to check it what do I type at command line?


robi

ps. i tried using that ubuntu.community/howtomd5sum and got that last msg....

---

### Post by alienexplorers on 2007-09-22
You know it might just be easier to start over with a good new disk and go from there.  I am out of idea's.

---

### Post by beanco on 2007-09-22
> **alienexplorers said:**
> You know it might just be easier to start over with a good new disk and go from there.  I am out of idea's.

that is what i started to do this morning but I could not ge the LIVE CD to download properly... the hashes did not match... this is what actaully caused me to start this thread!!!!




so I have downloaded it twice and both times the stinking hashes did not match!

robi

---

### Post by beanco on 2007-09-22
md5sum-ed it again, this is what I got


[HTML]test@robi:~/Desktop$ md5sum ubuntu-7.04-desktop-i386.iso
c644a729e07c1ce4350d97d9cae10ff5  ubuntu-7.04-desktop-i386.iso
[/HTML]

robi

---

### Post by kelvin spratt on 2007-09-22
i have never hash checked any distro and never had a problem, i write to Verbatim DVD-RW at max speed, most downloads have small errors cheap CD media and DVD media burn with horrendous error rates, and can give errors in the hash check, always turn things not needed off as it could effect your burn, icandy comes to mind if burning in windows spyware, adaware, and viruses, will cause your burn to fail  i also use a top flight burner. please don't take offence at what i'm saying just trying to help.

---

### Post by moredhel on 2007-09-22
If you run epiphany and opera through terminal then it should come up with errors which you can post here and we can try and resolve them =]

---

### Post by alienexplorers on 2007-09-22
These are the checksums for Fiesty Fawn:
> 50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

---

### Post by heldal on 2007-09-22
You might need to have someone check your hardware first. Even Vista can't cope if the machine is broken. There's at least a couple things that says you're barking up the wrong tree:

1. You say you can't boot off a CD even after double-checking BIOS settings. If that is a known good CD that works on a different machine with the same CPU architecture, your box is toast.

2. That you can't match the MD5-sum on a downloaded file means it somehow has become corrupted. Any hardware involved in the transport (network, memory, cpu, disk etc) and storage of the file might cause such problems, but the most probable culprit is a broken harddrive.  A corrupted harddrive is also typical for some of the other problems you describe. The inconsistency between the different user-accounts might very well be caused by partly corrupted configuration-files in those users home-directories.

Run a complete hardware diagnostic job on your computer and replace any broken parts.

---

### Post by James7 on 2007-09-22
> **heldal said:**
> You might need to have someone check your hardware first. Even Vista can't cope if the machine is broken. There's at least a couple things that says you're barking up the wrong tree:

1. You say you can't boot off a CD even after double-checking BIOS settings. If that is a known good CD that works on a different machine with the same CPU architecture, your box is toast.


I agree, and frankly if you can't boot with a known good Ubuntu CD, how can you boot with a Vista install CD or any other CD?:(

---

### Post by Bothered on 2007-09-22
> **beanco said:**
> 2 Opera will not launch

3. Epiphany will not launch

As said above, could you try running these in a terminal and post the results. e.g. for epiphany:

```
epiphany
```

> **beanco said:**
> 4. I thought I would reinstall the entire system. I downloaded the desktop iso but when I checked it with md5sum it never had the correct hash, I tried several times.

You could try downloading using bittorrent - it's more likely to download without errors. You can find links to the torrent files on a mirror, e.g. [here]("http://www.mirrorservice.org/sites/releases.ubuntu.com/7.04/").

> **beanco said:**
> 5. I have a CD that my friend gave me, but I cannot get the machine to boot form that CD, so I cannot instlal everythign from that either.

Does your computer attempt to boot from the CD at all? Do you get the CD startup screen (with boot options)? If not, then your BIOS may not be set to boot from the CD. Enter the BIOS configuration and change the boot order, putting the CD drive before the hard disk.

> **beanco said:**
> 8. none of us have the synoptic/repositories, or whatever that thing is called... for some reason it did not install with Feisty.

I don't understand. You mean none of you can run Synaptic? Does it not appear in System->Administration->Synaptic Package Manager?

---

### Post by beanco on 2007-09-22
```
Bothered;3407162As said above, could you try running these in a terminal and post the results. e.g. for epiphany:
```



OK, Here you go:

[HTML]test@robi:~$ epiphany

 (epiphany:24291): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(epiphany:24291): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(epiphany:24291): libgnomevfs-WARNING **: Failed to create service browser: Bad state

[/HTML]

and for Opera, this:

[HTML]test@robi:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored[/HTML].



I will also try the torrent site...




[HTML]Does your computer attempt to boot from the CD at all? Do you get the CD startup screen (with boot options)? If not, then your BIOS may not be set to boot from the CD. Enter the BIOS configuration and change the boot order, putting the CD drive before the hard disk.[/HTML]

Well, like I have said, I went into BIOs and chose the CD BOOT option, I will try it again.


[HTML]I don't understand. You mean none of you can run Synaptic? Does it not appear in System->Administration->Synaptic Package Manager?[/HTML]

exactyl, it does not appera!!!!


As to the CD I have, I have no idea if it is good or not. I just assuemd it was!!!!!
But as I said earlier when I try to check CDs or DVDs I always have it showing that a file that was written long ago on a Cd that is not in the machine as being mounted so I cannot see what is on the current CD... but this is laikely me doing something wrong rather than the machine.

However, I am not beyond saying the machine is in need of a check over. Are there any diagnostic tools I could use  easily to check or am I going to need to have a technician with all the know-how do it?

thanks for all the help

Robi

PS. I know that if some hardware is broken then I will not be able to use Vista. and that I will have to replace the hardware... in fact if that turns out to be the case it would be the simplest solution.

---

