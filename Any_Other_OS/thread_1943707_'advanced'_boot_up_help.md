---
title: "'advanced' boot up help"
date: 2012-03-19
forum: Any Other OS
---

### Post by theHands on 2012-03-19
Hi,
I have a netbook with windows 7, xp, linux mint , and pingEee on it.

I have a 'grub customizer' programme running from pingEee that allows me to customize the start up menu with a picture, and boot order options.

I'm trying to make a total hard disk image in case of any problems.
I succeeded with clonezilla.
But after it finished, it told me i may need fix the linux booter if i ever put this image onto my computer to restore it.

ive no idea how to go about it, specially when i have 4 os's on there, and two linux. 
i do know my booter is running off of pingEee( the last os i put in) but as i say, pingEee is also running the 'grub customizer' programme.(if that makes a difference)

is it a simple process to fix the booter in linux??


Or is there a total hard disk back up programme that leaves the boot up intact in the first place?

Thanks

---

### Post by Perfect Storm on 2012-03-19
Moved to Other OS/Distro Talk.

---

### Post by Snow Keld on 2012-03-20
GRUB is located in your linux partition.

if you restore your entire system (say, due to HDD failure) and restore, grub will be restored as well. with one problem.

you must have grub installed to your MBR (master boot record) of your HDD, this part will not be restored.

having multiple systems installed should not make any difference, only which system will control grub.



the only way i have ever fixed the issue is either, install a new/other linux os to make a new grub, or recently i have live-boot then chroot into the installed system and run "grub-install /dev/sd..."



maybe someone can provide a better way?

---

### Post by theHands on 2012-03-20
> **Snow Keld said:**
> GRUB is located in your linux partition.
 
if you restore your entire system (say, due to HDD failure) and restore, grub will be restored as well. with one problem.
 
you must have grub installed to your MBR (master boot record) of your HDD, this part will not be restored.
 
having multiple systems installed should not make any difference, only which system will control grub.
 
 
 
the only way i have ever fixed the issue is either, install a new/other linux os to make a new grub, or recently i have live-boot then chroot into the installed system and run "grub-install /dev/sd..."
 
 
 
maybe someone can provide a better way?
 
 
Thanks for the reply.
 
You mean, put the operating sytems bacm on the netbook, then add a 5th linux, just so it makes a fresh grub?
 
Surely there is a way to just inject a 'grub' into the sytem once its installed?
but perhaps not..
confusing..
and kind of makes backups pointless.

---

### Post by lisati on 2012-03-20
I don't see why installing an extra Linux just to install grub would be necessary - it should be possible to do so from within one of the existing installations or possibly from a Live CD. Having never done it myself, I will defer to the advice of others.

---

### Post by theHands on 2012-03-20
Seems no one has the answer on this one...

i guess i would have to install my 4 os's from my back up disc, then delete & re-install one of the linux os's.. probably 'pingee' because thats the one not showing on the boot menu after backing up.
Then hopefully when i do that.. it will sort itsself out,...

I guess just intalling and configuring one OS if i ever get failure is better than having to do all four..

---

