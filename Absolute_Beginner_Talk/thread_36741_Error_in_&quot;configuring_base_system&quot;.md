---
title: "Error in &quot;configuring base system&quot;"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by asarwate on 2005-05-24
After much pain and agony (caused I think by a bad CD-ROM drive), I installed the base system.  However, upon reboot when it gets to the line "Configuring Base System" I get the error code:

send-mail : warning : fork : address family not supported by protocol

Now I don't particularly need sendmail running, but it seems to be hanging the whole installation process.  Control-C doesn't cancel whatever's going on, so it appears the installer has to cross this hurdle or die trying.  Any advice?  I suppose I could try to wipe the drive and do a fresh install, but would like that to be a last resort.

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=asarwate] Any advice?  I suppose I could try to wipe the drive and do a fresh install, but would like that to be a last resort.[/QUOTE]

It should be the first. The ubuntu install is VERY sensitive. Sometimes reinstalling can go a long way.

---

### Post by Xof on 2005-08-26
I'm having the same problem, did a fresh install of Ubuntu. But it hangs on the above warning.

Anyone has a solution for this?

---

### Post by greymoose58 on 2005-10-15
I've got a similar problem......

After a bit of mucking around with the CD (I ended up burning it again, but at 4x) I've got to the point of rebooting the machine. Once it fires it gets as far as "Configuring Base System" and just repeats that message. No error message as such. :confused: Could this be related?

The machine is a 233 MMX with 128mb RAM. It ran Hoary fine a few weeks ago. I'm installing Breezy fresh on a new hard drive for a friend.

Cheers.

---

### Post by JamesGreenhalgh on 2006-04-30
Hi,

Had the same problem when stuffing around with upgrading from breezy to dapper. 

Solution: 
#modprobe unix

In my case, unix module wasn't in. This module is used for some inter-process communication, and the lack of it resulted in the error.

YMMV

Cheers, 
James

---

