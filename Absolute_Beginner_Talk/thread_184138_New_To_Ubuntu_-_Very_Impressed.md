---
title: "New To Ubuntu - Very Impressed"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by RaigyCar on 2006-05-29
This morning i was only using Windows XP.

Then i discovered an Operating System thread on another forum and thought i would give Linux ago.

I downloaded and creaded a "Live CD" of Ubuntu.

I have to say i am very impressed.

I haven't even installed Ubuntu on my PC yet i am just running it off a CD-ROM, yet i am connected to the internet and writing this message.

I was wondering how the live CD works, i am connected to the internet, running off a CD-Rom how does that work??

Plus i have saved files on my Ubuntu desktop, while running the live cd does that get saved on my C: Hard Drive??

I have just bought a new external hard drive, i will probably partition that and install ubuntu on that, is this possible?

Cheers!

---

### Post by user1397 on 2006-05-29
[quote=RaigyCar]I was wondering how the live CD works, i am connected to the internet, running off a CD-Rom how does that work??[/quote]
The live-cd runs independently using your ram, so it does not affect your hard drive.

[quote=RaigyCar] Plus i have saved files on my Ubuntu desktop, while running the live cd does that get saved on my C: Hard Drive??[/quote] Nope!

[quote=RaigyCar] I have just bought a new external hard drive, i will probably partition that and install ubuntu on that, is this possible?[/quote] Yep!

---

### Post by mostwanted on 2006-05-29
Installing Ubuntu on free space (like a new harddisk) is very simple. The installer should have an option to detect and install to free space (the old text-based installer did, ayway), so you don't even have to partition yourself.

It will detect Windows as well and set up a bootloader so you can choose between the two when you start up your computer.

---

### Post by IYY on 2006-05-29
> 
I was wondering how the live CD works, i am connected to the internet, running off a CD-Rom how does that work??


It pretends that your RAM (memory) is your storage space. Of course, this means that you have less RAM to be used as memory, so it's much slower than an installed version.

> Plus i have saved files on my Ubuntu desktop, while running the live cd does that get saved on my C: Hard Drive??


No. If you formatted your drive with the FAT system, you would be able to mount it and write to it in Linux. If you formatted with NTFS (the default for Windows right now), you wouldn't be able to write to your drive safely, just read.

---

### Post by Ubuntuud on 2006-05-29
[QUOTE=mostwanted](the old text-based installer did, ayway).[/QUOTE]

I'm sure the new one will do so as well, espresso uses gparted (at least, that's how it looks).

---

### Post by steve.horsley on 2006-05-29
[QUOTE=RaigyCar]This morning i was only using Windows XP.

Then i discovered an Operating System thread on another forum and thought i would give Linux ago.

I downloaded and creaded a "Live CD" of Ubuntu.

I have to say i am very impressed.

I haven't even installed Ubuntu on my PC yet i am just running it off a CD-ROM, yet i am connected to the internet and writing this message.

I was wondering how the live CD works, i am connected to the internet, running off a CD-Rom how does that work??
[/QUOTE]
It runs an in-memory filesystem, like a RAM-disc for all the changeable stuff. It uses the CD as-is for all the read-only system stuff in order to avoid filling the whole of memory with the CD contents. It works very well, except that it is much slower than a proper install of course, because a CD is much slower than a hard disc.
> 
Plus i have saved files on my Ubuntu desktop, while running the live cd does that get saved on my C: Hard Drive??

No - the in-memory disk contents disappear when you reboot. Since Linux cannot write to NTFS partitions, you best bet is to put a USB memory stick in, and save the files there for now.
> 
I have just bought a new external hard drive, i will probably partition that and install ubuntu on that, is this possible?

Cheers!
Sorry, I don't know. You might try searching tihis forum - I'm sure the subject will have already been discussed.

---

### Post by jamesford on 2006-05-29
not really related to your questions, but if ur planning to install to harddisk id wait until thursday, thats when the next version of ubuntu is scheduled for release, version 6.06 (aka dapper). do id download that, i dont know but you are probably using 5.10 (breezy)

---

### Post by H.E. Pennypacker on 2006-05-29
I never understood how the Live CD was able to handle itself like the hard-drive.  I couldn't understand how it al worked, and its good to know. 

> not really related to your questions, but if ur planning to install to harddisk id wait until thursday, thats when the next version of ubuntu is scheduled for release, version 6.06 (aka dapper). do id download that, i dont know but you are probably using 5.10 (breezy)

I absolutely can't wait.  It's really exciting to see new stuff.  I thought June 1st would have been on Tuesday or something, but I guess I can wait 48 more hours.

---

