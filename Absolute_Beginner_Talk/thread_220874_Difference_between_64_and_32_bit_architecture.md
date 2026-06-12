---
title: "Difference between 64 and 32 bit architecture"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2006-07-22
Hi,
Is there a performance difference between using Ubuntu on a  64 or 32 bit pc?  If I were to build a  new system specifically for Ubuntu which architecture should I chose?

---

### Post by AirRaven on 2006-07-22
I reccomend you just go with the standard 32 bit i386 Ubuntu- the AMD64 version has a lot of problems with program availability- it's generally a lot easier to just use the normal version.

Any computer that supports the x86 instruction set will be fine with the standard i386 install- basically the full range of Intel chips and AMD chips. There's not really a performance drop when using 32 bit Ubuntu on an Athlon64 processor, and the lack of programs is a huge stumbling block- so just go for 32 bit.

---

### Post by Kilz on 2006-07-22
> **AirRaven said:**
> I reccomend you just go with the standard 32 bit i386 Ubuntu- the AMD64 version has a lot of problems with program availability- it's generally a lot easier to just use the normal version.
Wrong, there is no lack of program availability. Fact is the 64bit OS can run 32bit programs, so if there is one missing, you can run the 32bit version.

> **AirRaven said:**
> Any computer that supports the x86 instruction set will be fine with the standard i386 install- basically the full range of Intel chips and AMD chips. There's not really a performance drop when using 32 bit Ubuntu on an Athlon64 processor, and the lack of programs is a huge stumbling block- so just go for 32 bit.
Wrong , wrong, wrong. There are reported problems running the 32bit OS on 64bit hardware. There is a huge performance drop if you want to run some 64bit programs. Rippers, encoders, 3dmodeling, and anything with large number crunching. As said above there are no programs missing. That is 64bit FUD from people running a 32bit OS that have little if any knowledge on the subject.

---

### Post by AirRaven on 2006-07-22
> **Kilz said:**
> Wrong, there is no lack of program availability. Fact is the 64bit OS can run 32bit programs, so if there is one missing, you can run the 32bit version.


Wrong , wrong, wrong. There are reported problems running the 32bit OS on 64bit hardware. There is a huge performance drop if you want to run some 64bit programs. Rippers, encoders, 3dmodeling, and anything with large number crunching. As said above there are no programs missing. That is 64bit FUD from people running a 32bit OS that have little if any knowledge on the subject.

My mistake then. I was going by the experience of a friend with 64 bit Breezy. 

Apologies.

---

### Post by Kilz on 2006-07-22
> **AirRaven said:**
> My mistake then. I was going by the experience of a friend with 64 bit Breezy. 

Apologies.

Its ok, but there is a world of difference between 64bit Breezy and 64bit Dapper. You are not the only one who is misinformed. It is best if someone asks the difference between 32bit and 64bit to refer them to [the 64bit forum]("http://www.ubuntuforums.org/forumdisplay.php?f=134"). They can read about some of the problems/benefits and have people who are running the current 64bit OS give them up to date info. :-D

---

### Post by ironfistchamp on 2006-07-22
This is quite an interesting post as I run 32bit OS on 64bit h/w. I don't seem to have any problems. Well I do but I put them down to me just being careless or the universe being out to get me. 

What kind of problems are seen? And how can you run 32bit s/w on a 64bit OS. I heard that it was impossible.


Thanks

Ironfistchamp

---

### Post by Kilz on 2006-07-22
> **ironfistchamp said:**
> This is quite an interesting post as I run 32bit OS on 64bit h/w. I don't seem to have any problems. Well I do but I put them down to me just being careless or the universe being out to get me. 

What kind of problems are seen? And how can you run 32bit s/w on a 64bit OS. I heard that it was impossible.


Thanks

Ironfistchamp

There are reports of things running slow, crashing, etc. When the 64bit OS was used problems stoped.
Running 32bit software isnt impossible. It was on Breezy, not on Dapper. There is always the [option of a chroot]("http://www.ubuntuforums.org/showthread.php?t=157412"), or a 32bit os inside of a 64bit one. Thats mainly for people wanting to run lots and lots of 32bit software. But thats not nessasary, Dapper will run 32bit software without it.
Launchpad says there are 20323 binary packages for i386 and 19942 binary packages for and64. For 98% of the 32bit software there is a 64bit version in synaptic. For the rest it may mean following a howto, or running setup scripts to install a 32bit program. Like the firefox with pulgins/wine howto/scripts in my signature.
[There is also a sticky]("http://www.ubuntuforums.org/showthread.php?t=191205") in the 64bit section(with a name that needs to be changed because the subject has) with links to the howto's.

---

### Post by ironfistchamp on 2006-07-22
What about getting things from source? Do you need specific source code designed for 64bit OSes or can you use any old code and compile for your 64bit OS?

---

### Post by Kilz on 2006-07-22
> **ironfistchamp said:**
> What about getting things from source? Do you need specific source code designed for 64bit OSes or can you use any old code and compile for your 64bit OS?
The few things I have found nessasary to compile 64bit versions from source could also be used to compile 32bit versions. I compiled the comical .cbr reader into .deb files last month. The amd64 and i386 packages were compiled from the same code.

---

### Post by ironfistchamp on 2006-07-22
Wow thanks I am going to download the 64bit dapper and give it a shot. Thanks alot.

Ironfistchamp

---

