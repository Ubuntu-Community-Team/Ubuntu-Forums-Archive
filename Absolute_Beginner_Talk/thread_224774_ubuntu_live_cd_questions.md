---
title: "ubuntu live cd questions"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by garnet on 2006-07-28
Questions:

1 when i boot up and run ubuntu from the cd and i configure the email client to send an email does it write anything to my xp operating system or is it just in ram memory?

2 if i left it running could it recieve an email?

3 when running the live cd do i have access to any files already on my hard drive... can i save files to my hard drive?

---

### Post by benuski on 2006-07-28
> **garnet said:**
> Questions:

1 when i boot up and run ubuntu from the cd and i configure the email client to send an email does it write anything to my xp operating system or is it just in ram memory?

2 if i left it running could it recieve an email?

3 when running the live cd do i have access to any files already on my hard drive... can i save files to my hard drive?


1.  The live cd writes nothing to your memory.  It is running completely off of the RAM and the cd itself, making it much slower than the installed version, but nothing is written.

2.  If you left it running and configured it right, sure, it would recieve emails.

3. On the livecd, you will have read access to your windows files, but you cannot save anything to your hard drive unless it is formated as a FAT32 drive.  There is no official support for writing to an NTFS drive in Ubuntu yet.

---

### Post by garnet on 2006-07-28
Thankyu benuski for the fast reply !

Some more questions if you have time.

1 What if your have a blank hard drive with no other operating system, formatted as FAT32 as you say... would it then run like a normal system, except it is running off the cd rom and would be slower?
What i'm thinking here is a failsafe system for my dear old mother... even if is a little slow.

2 In the above scenario could the whole of ubuntu be loaded into ram and how much would be required if so... this might free up the cd rom?

3 In the above scenario how would USB and printer support be ?

Again thanx for your time.

---

### Post by benuski on 2006-07-28
> **garnet said:**
> Thankyu benuski for the fast reply !

Some more questions if you have time.

1 What if your have a blank hard drive with no other operating system, formatted as FAT32 as you say... would it then run like a normal system, except it is running off the cd rom and would be slower?
What i'm thinking here is a failsafe system for my dear old mother... even if is a little slow.

2 In the above scenario could the whole of ubuntu be loaded into ram and how much would be required if so... this might free up the cd rom?

3 In the above scenario how would USB and printer support be ?

Again thanx for your time.


Well, if you just have a blank FAT32 drive, I would just install Ubuntu straight onto it instead of running off of the live cd.  But, theoretically, it would run just like a normal OS; however, I've never tried it or ever read of anyone who has. But I'm sure those sorts of people are out there.

I don't think you can load the whole operating system into RAM and then remove the CD.  I'm pretty sure that it only loads the bare minimum of what is needed at any given time, and reads the CD when it needs to open up a new program.

USB support should be fine, since its built into the kernel.  I'm not sure on printing, since I have never printed anything on linux, but I would think it should also be fine.

Feel free to come back with any more questions you have.

---

### Post by garnet on 2006-07-28
thanx benuski
Yes i suppose it is a strange idea. my mother just needs a setup that remains consistent for the few emails, few text documents and odd printing requrements she has. she lives way out in the country and her computing life becomes very frustrating when something changes on her operating system that causes her confusion or system problems. she just needs something that is simple and consistent.

if this scenario worked she would have to configure the email client each time and save the emails as files to the hard drive or just use a webmail account... which i think she does anyway.

---

### Post by kinematic on 2006-07-28
> **benuski said:**
> Well, if you just have a blank FAT32 drive, I would just install Ubuntu straight onto it

not a good idea :-& 
linux has it's own file systems.

---

### Post by garnet on 2006-07-28
[https://help.ubuntu.com/community/LiveCDPersistence]("https://help.ubuntu.com/community/LiveCDPersistence")

kinematic & benuski:

the link above to LiveCDPersistence, is this something close to what i was thinking about ?

---

### Post by erikaaboe on 2006-07-28
Garnet-
I'm relatively new (two days) to playing with Ubuntu but have been looking at the Persistent CD option. I do not think that you would get much benefit from having your mother boot from a CD and write configuration info to a loopback or USB device. It would probably be just as static for your mother to boot from the hard drive into an installed system. If you are willing to reformat the hard drive, installing ubuntu onto it would probably be a better option. The Persistent CD really is useful for transporting configuration and files from PC to PC. 
-Erik

---

