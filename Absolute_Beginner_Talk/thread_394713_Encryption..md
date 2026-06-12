---
title: "Encryption."
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by yeprst on 2007-03-27
Hi. I'm a new user and I care about my HDD security (laptop)

Ok. I've read some posts and found things about dm-crypt, cryptoloop and etc.. LUKS...

Even tried Mandriva's integrated encryption, but it can only handle /tmp and /home encrypted. 

And my needs are:

1. Fast and easy encryption setup
2. I want at LEAST these partitions be encrypted - /tmp /home /var /swap.

Who can help me to do this easy and fast ?

---

### Post by Falados on 2007-03-27
> **yeprst said:**
> Hi. I'm a new user and I care about my HDD security (laptop)

Ok. I've read some posts and found things about dm-crypt, cryptoloop and etc.. LUKS...

Even tried Mandriva's integrated encryption, but it can only handle /tmp and /home encrypted. 

And my needs are:

1. Fast and easy encryption setup
2. I want at LEAST these partitions be encrypted - /tmp /home /var /swap.

Who can help me to do this easy and fast ?

I don't know how easy it will be, but this site seems to have a lot of the info you may require.

[http://www.saout.de/tikiwiki/tiki-index.php](http://www.saout.de/tikiwiki/tiki-index.php)

---

### Post by kahrytan on 2007-03-27
I was just reading about this myself. And I happened upon the wiki for Ubuntu.  Check out the [Security section]("https://help.ubuntu.com/community/Security") of the Community Wiki. It's near the bottom under Encrypted file systems.

---

### Post by yeprst on 2007-03-27
but are speaking here about EASY encryption setup ? :))

well this is TOO tricky for me, setting up all these kernels and so on. I just want great encryption capabilities like in XP. for example I use Drive Crypt (German software) to encrypt my entire windows partition. and it modifies MBR and asks for two passwords, and ir provides plausible deniability. If I enter the second set of passwords - data desctruction process is started then :)

---

### Post by yeprst on 2007-03-27
and it's critical to me... having my HDD encrypted is real critical to me. cause I work for Russian Ministry of internal affairs.  I gave Ubuntu a try, thinking it's real userfriendly distribution. yes it is. but there is NO easy encryption manuals for me. I'm just a user.. and no guru..

---

### Post by macogw on 2007-03-27
Why do you need to encrypt swap?  It doesn't store any data.

---

### Post by Falados on 2007-03-27
> **macogw said:**
> Why do you need to encrypt swap?  It doesn't store any data.

While the computer is on, it stores everything that you are doing.  If (possibly) someone had access to a dump of your unencrypted ram, they could potentially reconstruct what you were doing at that time, or maybe all they need is the contents of a file you happened to be working on.

---

### Post by kahrytan on 2007-03-28
I understand. I am pondering if I should take a plunge and try encryption. I want to see how the performance is.

If you just want to encrypt a few files, try GNU PG. Then just encrypt the flash drive that stores the keys.

---

### Post by yeprst on 2007-03-28
well, I can't still find any easy security solution which will not require me to install some modules and read 12 pages of documentation/code to install it. 

And after that Linux is called a SECURE os :) without easy encryption options - ubuntu for me is unusable, sorry. 


bye, bye.

---

### Post by dr_d on 2007-03-28
Yes, it'll certainly be hard to get something like this working. You'll likely have to compile your own kernel, which is a big pain, and need to be done again every time u want to upgrade your kernel.

HOWEVER. If you really, really care about security, more is possible on linux than under windows.

Check this out: [http://www.mcdonald.org.uk/StegFS/](http://www.mcdonald.org.uk/StegFS/)

It's a steganographic file system. Say you've got your drive encrypted. What happens if a judge orders you to give up the key. What if somebody threatens you. What about torture. Certainly these cases are probably a bit extreme, but for arguments sake.

If you have stegfs, you can plausibly deny the existance of encrypted data on your hdd. There are some drawbacks to using it, but if security is what you're after, it's just the thing.

Anyways, yeah.

---

### Post by yeprst on 2007-03-28
but this requires me to compile a kernel module. and it's only for some file hiding purposes. 

But that's not what I need. I need my /home /swap and / be encrypted and authenticated via USB token (simple USB drive i.e.) and I want it to be user-friendly :)
I guess there is no solutions. I've already googled...

here's what the say at StegFS FAQ

* So StegFS is better than a cryptographic file system such as CFS,
TCFS, etc?

Well, yes and no.
The information hiding comes at a price. To ensure the security we
have to allow data in the file system to be accidently overwritten. To
avoid losing files we, therefore, write several copies of each file
block and inode so that, if some are overwritten, others can hopefully
be recovered. This replication obviously requires more disk space for
a given file. There is also a performance penalty due to the need to
write several copies of everything. There is also the risk that all
copies of a given block will be overwritten, in which case its
contents are lost.

If you don't think you need the plausible deniability aspect, then
don't use a steganographic file system, use a cryptographic file
system instead. You will get better performance, waste less disk space
and stand less chance of files being destroyed.

---

### Post by ice60 on 2007-03-28
here are two threads about encryption when i asked about it -
[http://ubuntuforums.org/showthread.php?t=339797](http://ubuntuforums.org/showthread.php?t=339797)
[http://www.suseforums.net/index.php?showtopic=32963](http://www.suseforums.net/index.php?showtopic=32963)

my HDD failed right after i did the ubuntu/truecrypt thread one, but it should work. i tried it out on a test box and it looked like it was working with the little time i spent with it.

---

### Post by dr_d on 2007-03-28
Yes, that is the *big* disadvantage to using StegFS. Otherwise I'd probably be using it myself.

You can't deny the cool factor though :)

---

### Post by yeprst on 2007-03-28
But I am not speaking about being COOL, I speak about security and stability. This is not a game for me like "will it work or not" it's my everyday life, being secure. And Ubuntu unfortunately cannot offer me an easy to setup and 99% stable security option regarding HDD encryption. 

Windows does. But I paid ~250 USD for the software, but it works for 3 years already and saved my *** for several times. 

Anybody? Any ideas in Ubuntu ?

---

### Post by ice60 on 2007-03-29
you could use this until you find something, it's very easy to setup and use, it adds a right-click option in nautilus (it's what i was talking about in one of my posts i linked to. i said it was broken, but it was just using the wong key)
[http://www.ubuntuforums.org/showthread.php?t=108513](http://www.ubuntuforums.org/showthread.php?t=108513)

---

### Post by High Roller on 2007-04-10
> **yeprst said:**
> But I am not speaking about being COOL, I speak about security and stability. This is not a game for me like "will it work or not" it's my everyday life, being secure. And Ubuntu unfortunately cannot offer me an easy to setup and 99% stable security option regarding HDD encryption. 

Windows does. But I paid ~250 USD for the software, but it works for 3 years already and saved my *** for several times. 

Anybody? Any ideas in Ubuntu ?

Well, here's my suggestion.  Give Debian 4.0 (Etch) a try.  It supports LUKS encryption and is capable of encrypting everything but /boot.  The GUI installer of the OS gives you the ability to encrypt the hard disk via the partition manager.  From what I gather you wouldn't need to rebuild the kernel modules either as LUKS is part of the base system.  Fedora offers something similar I believe but don't count me on that.

I don't think that there's anything out for Linux that will encrypt your hard drive similar to Windows applications such as DCPP or Safeboot solo.  Those programs are nice because you can encrypt you whole drive while the system is running.  But that has a downside as well...  you can't "whiten" the drive before you encrypt because you're base system is already on the drive.

There's also the hardware IDE controllers you can buy that encrypt at the bios/hardware level.  They're also a little more tamper proof in that there's no MBR for an adversary to install a keylogger etc.

---

### Post by LaurelLynn on 2007-04-10
Dear yeprst,

This thread explains how to use Truecrypt on Ubuntu. I have used it on XP, it´s available for both:

[http://ubuntuforums.org/showthread.php?t=199367](http://ubuntuforums.org/showthread.php?t=199367)

It´s secure and easy to use.

I believe it is just the thing you are looking for. You can´t encrypt  / though or the system won´t be bootable.

---

### Post by High Roller on 2007-04-10
> **LaurelLynn said:**
> Dear yeprst,

This thread explains how to use Truecrypt on Ubuntu. I have used it on XP, it´s available for both:

[http://ubuntuforums.org/showthread.php?t=199367](http://ubuntuforums.org/showthread.php?t=199367)

It´s secure and easy to use.

I believe it is just the thing you are looking for. You can´t encrypt  / though or the system won´t be bootable.

I don't think that will meet his/her objective.  TrueCrypt is a container encryption solution and has its uses but probably wouldn't be what this person is looking for:  "encrypting at LEAST these partitions - /tmp /home /var /swap."  Your system probably wouldn't startup unless there was some type of Pre-Boot Authentication to get access to /tmp /home /var /swap...

Just throwing out some ideas to see if they fly :)

---

### Post by LaurelLynn on 2007-04-11
Dear High Roller,

Truecrypt stores the encrypted data on a partition or in a file, which it makes it look like a drive to the os, through a custom driver.  At least that is how it works on windows

Your right though, problem is the os has to mount the drivers.  If you encrypt the drives with the os, how do you boot to mount the drive your booting from?

Maybe if the Truecrypt drivers are added to the kernel, and /boot is unencrypted??? But thats speculation

---

### Post by LaurelLynn on 2007-04-11
Yep, Truecrypt seems to work as a new filesystem compatible with both Linux and Windows. From the manual:

[INDENT]Q: Will I be able to mount my TrueCrypt partition/container after I reinstall the operating system?

A: Yes, TrueCrypt volumes are independent of the operating system. However, you need to make sure your operating system installer does not format the partition where your TrueCrypt volume resides.[/INDENT]

Might be workable. No matter what solution you use though, /boot has to be on an unencrypted partition, because GRUB can´t read the kernel if it´s on an encrypted drive.

Here is where the manual is:

[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

They have Ubuntu specific downloads as well!

---

### Post by hyper_ch on 2007-12-22
Get the Ubuntu Gutsy Alternate install cd. Upon installation you can chose to encrypt the whole system. Everything but /boot will then be encrypted.

---

