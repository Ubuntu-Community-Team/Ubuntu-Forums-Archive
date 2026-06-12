---
title: "Even more problems"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by HackCoders on 2007-10-11
FFS, this has got to be the hardest OS I have ever come across, It's so easy to use once your in but for gods sake installation is so hard!

OK well, yesterday I made around two threads, regarding issues I have with the installation of ubuntu, basically it was giving a GRUB error yesterday, (error 21)..Today I installed the Gutsy Gibbon, I selected "Do not install boot loader", just so I don't need grub since I will only be using linux, no other OS.

After BIOS POST it says "Error loading operating system"...I try to install lilo via an app called "Super GRUB disc" or something like that, no luck at all

So now I want to format my computer and select the boot loader option but I don't know how to format via terminal.

Can anyone suggest a linux distro as good or better than ubuntu? How is redhat? or knoppix?

I'm so tired of this, I'm new to the whole partitioning thing and what not, so I don't know what this hd0, sda stuff are..

I need some help! :(

Edit: After installing lilo, instead of saying error, it says "No boot signature found in partition"

---

### Post by skymera on 2007-10-11
its obvious when upgrading to latest ubuntu therws going to be problems, but Gutsy is still in testing.

can u put live CD in and reinstall GRUB?

redhat is more for business i think

try pclinuxos

[www.pclinuxos.com](www.pclinuxos.com)

then again, they are all the same virtually.

linux - unix, just look different

---

### Post by HackCoders on 2007-10-11
Well I had these problems with 7.04 yesterday too

How do I install grub while in the live cd?

I tried

Root (hd0)
setup (hd0,0) and (hd0)

Tells me it can't access the drive or something like that.


My computer specs:

160GB IDE HDD
Core 2 CPU
Asus P5B-E with latest BIOS  --I read somewhere this mobo might be the problem

---

### Post by skymera on 2007-10-11
ok live cd

type in terminal

```
 
grub

root (hd0,1) <-- replace with youtr drive, ive done HD1 partition 2 for example

setup (hd0)

quit 
```


then restart

---

### Post by HackCoders on 2007-10-11
How do I find out what numbers I should use?

For me, I formatted my whole drive and just installed linux on it.

---

### Post by skymera on 2007-10-11
ok first!

```
 find /boot/grub/stage1 
```

that give you partition for your ubuntu

then follow the rest.

im off to college now, good luck with everything :wink:

---

### Post by HackCoders on 2007-10-11
Cannot be found ... There is no grub folder on my computer =\

Bah :( dammit, I don't wanna go back to XP!

---

### Post by n3tfury on 2007-10-11
> **HackCoders said:**
> 
I'm so tired of this, I'm new to the whole partitioning thing and what not, so I don't know what this hd0, sda stuff are..



if you don't know what those are, you won't get any further with other distros, sorry.

---

### Post by HackCoders on 2007-10-11
Well I have basic knowledge of that stuff, just not when everyone goes off about partition numbers and whatnot, it all confuses me..

Since when is it a very hard thing just to install an OS

What about fedora, maybe I should give that a shot? It's 3.5GB :(...

How do I format the C drive via ubuntu live cd? What do I type in the terminal? I'm gonna try installing the 32bit one..

---

### Post by Ant_Merlin on 2007-10-11
Hiya, you would be best using the Live CD and let it setup the drive for you. when it gets to the right part select, USE FULL DRIVE, AUTOMATIC. on the list, it should be third option down when it asks you which partition to use. It will then format, setup and setup grub boot. grub boot is best left to install on its own.

---

### Post by HackCoders on 2007-10-11
OK Then I'll give that a try..

If this doesn't work, I'll give fedora a go, if that doesn't work... back to XP :(

---

### Post by hyper_ch on 2007-10-11
Do you have any data on the drive(s) that you want to keep?

If not, then just reinstall the whole thing and select tell the installation program to use the full disk and also have Grub installed.

If you have more than one drive in there, be carefull to select the right now.

If you have multiple drives and IDE mixed with SATA ones it can become a bit more complicated.

---

### Post by HackCoders on 2007-10-11
Yeah well I formatted and removed XP to get linux, so I was kinda hoping it would go out well.

I selected do not install boot loader because last night I was having issues with grub, I have updated my BIOS today, so I might just go ahead and do a normal install and format the HDD.


I'll go do it now.

---

### Post by hyper_ch on 2007-10-11
well, if you wiped your harddisk and did not install Grub then you had no boot loader at all... I doubt a system works without any bootloader...

Just get the Gutsy CD and da a full-install... although if your harddisks are already wiped you may want to choose to create a seperate /home directory from the beginning... that's not really difficult (if you know how) and it's not damaging when you have no valuable data anyway on your harddrive ;)

---

### Post by HackCoders on 2007-10-11
I selected / as the mounting point, when ever I select /home or anything, it says no root mounting point is defined or something like that


And, I thought GRUB was only if you have more than one OS, so I unticked it since I would of been using linux only, so I wanted direct boot

Anyway I'm doing a re-install now, I hope this goes well

Thanks for the suggestions guys ^_^

---

### Post by dwhitney67 on 2007-10-11
> Can anyone suggest a linux distro as good or better than ubuntu? How is redhat? or knoppix?
Try Fedora 7 or the soon-to-be-released Fedora 8.  (actually 8 is out, but it is a beta release).

---

### Post by HackCoders on 2007-10-11
I'll try 7 if this doesn't work, and if I like it (Thats if it works), I'll get 8 when its officially released.

---

### Post by HackCoders on 2007-10-11
OMFG

It worked!, thanks everyone!

I formatted and installed the 32bit ubuntu, YAY!!!

---

### Post by HackCoders on 2007-10-11
OK right now I'm configuring my wireless adapter

Ummm, it says to go to terminal and type this:

CD ~/inf/drivername.inf       I know where the file is, I just don't know what to put in the ~ part, It's my LEXAR USB Drive, I tried putting it as /LEXAR/inf but it doesn't work

How do I get the drive letter for devices in linux, or is that just in windows?


Also, when I go to my HDD, there's a massive bunch of system files..like usr folder, boot etc..can I make those hidden or anything? They take too much space and I don't want anything happening to it


All in all finally I have linux

---

### Post by philinux on 2007-10-11
go easy step by step.

Just imagine a while back if somebody gave you a pc clean as a whistle, hard drive not formatted and a windows disk and said install the operating system and get it going from scratch. 

Thats why most people buy a pc preloaded switch on and go even mac. You are taking another step all together. It's a challenge yes. But there's help here!

---

### Post by HackCoders on 2007-10-11
Hmm I'm guessing it was a BIOS issue, Probably the bios update fixed it because I tried all the ubuntu disc's I had yesterday and all gave grub error :)

I'll search for my wireless card here..

---

### Post by HackCoders on 2007-10-11
I've decided to stick to windows for the next week, until I move houses, there I will have a connection via ethernet cable which worked fine in ubuntu, I just don't have the space to do it in my current situiation

I used ubuntu for a few hours without the internet, and the things that were on there so far were great ^_^, I like it...

Thanks for the help everyone

---

### Post by Martje_001 on 2007-10-11
> **HackCoders said:**
> I've decided to stick to windows for the next week, until I move houses, there I will have a connection via ethernet cable which worked fine in ubuntu, I just don't have the space to do it in my current situiation

I used ubuntu for a few hours without the internet, and the things that were on there so far were great ^_^, I like it...

Thanks for the help everyone
Whith internet it's much cooler ;). You can just install programs with one click and so on.. :D

---

### Post by -grubby on 2007-10-11
you have to install Grub to even load Ubuntu!

---

### Post by shankhs on 2007-10-11
For ALL new Gusty users Here is (I think) a very useful link:
[http://www.fsckin.com/2007/09/28/how-to-install-gutsy-gibbon-a-21-step-guide-for-technical-support/](http://www.fsckin.com/2007/09/28/how-to-install-gutsy-gibbon-a-21-step-guide-for-technical-support/)

---

