---
title: "Live CD wont start?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Thanatios on 2006-08-24
I got a friend that is trying to install Ubuntu, but when he starts up the Live CD, it just keeps loading and loading. (He kept it on for 6 hours, and it just woulnt load).

Maybe its his RAM?
He only has 224 MB of RAM.
It cant be his dvd driver, since its the newest one around.

Any suggestions?
Thanks in advance.

---

### Post by meng on 2006-08-24
6 hours? Wow that's dedicated.
At what point does it stop?
Things to consider are - corrupted download (do md5checksum); bad burn (reburn at lower speed).

---

### Post by Thanatios on 2006-08-24
It freezes at "Adding live CD user..."

I Myself think its the RAM. And whas wondering if its possible to install it another way? Without downloading the Alternative CD. =/

---

### Post by L_o_N_e_R on 2006-08-24
u need 256 MB of ram :(

---

### Post by Thanatios on 2006-08-24
Well, is there any other way to install it? Like some sort of Windows emulator for it (I heard something about OpenSuse, can someone explain more?)

And can someone tell me where to download the alternative CD?

Thanks in advance

---

### Post by L_o_N_e_R on 2006-08-24
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)



u will find the alternate cd there



btw if the live cd wont work then installing it wont work :(

---

### Post by ivandeterrible on 2006-08-24
this is a common problem with some users trying to boot into a linux distro. for a distro as big as ubuntu it is hard to try to get it working on older hardware, while not impossible

while there are minimum requirements to run this distro, you should have at least a 650 mhz intel/amd , 256 megs ram, and 8x or above dvd rom drive (16x cd read) the speed and loading time not only depends on ram and cpu, but alot of it has to do with cd read speed
it dont matter abt the drivers u have, just hardware

try to get it running on another computer to see wat happens
hope this helps

---

### Post by ivandeterrible on 2006-08-24
my bad =====should be 24x cdrom speed or above

---

### Post by SteveHoffmanUK on 2006-08-24
I am running Ubuntu on an old Dell Latitude CSx laptop with 128 of memory and an external CD-ROM reader that just barely works. 

My experience suggests that his problem is the CD. Downloading and burning the live CD has always been a bit dodgy -- you can easily get a corrupt download and also a bad burn. Even the CD I received from Ubuntu only worked once and then it got corrupted and I had to download and burn a new one.

So have him download a fresh live CD image, then burn it at the slowest speed possible (4X), and when he loads it, have him run the disk check.

---

### Post by Thanatios on 2006-08-24
well, first, there is nothing with his CD driver, it runs at 52x speed. Second, CD is fine, when he runs it on windows, it says its fine. Also, he made a test, and the test gave positive results on the CD.

BUT, the problem might be the CD itself, on wich he burned it. Not, how he burned or played it.

Looks like he burned it on a CD-RW.
> Luks says:
my cd driver is
Luks says:
52x reading
Luks says:
32x rw
Luks says:
and 52x burning
Luks says:
but the CD-RW is just 4x =/

---

### Post by depkmaster on 2006-08-24
I like SteveHoffmanUK answer. I had a Solaris instalation go bad because of a bad download or cd burn. I wonder if Ubuntu has a checksum, that would help you know if there was an error in the download.

---

### Post by tommycai on 2006-09-24
I'm getting the same add live cd installation problem.  I ran some kind of program that is supposed to test programs and it said that mineis fine and then I burnt the iso using nero 3 times and roxio 3 times to make sure then I downloaded another one not even from the same mirror but from torrentz to get it and figured that might work but still I run into the same problem??

---

### Post by tommycai on 2006-09-25
i'm still working on this problem mine boots up and says "adding live cd user" and stops there and now I tried using kubuntu and still the same exact thing? If someone figures it out please e-mail me [email]tommycai22@yahoo.com[/email] or please someone post a reply I think i'm the only one still working on this.

---

### Post by maaronB on 2006-09-26
It is hard to tell.
I don't think that the RAM is the problem, even if it is not enough to actually install Ubuntu, it should still get further than that.

Are you saying you have test 8 different CD's, if so we can saftely rule that out.

So that leaves your CDPlayer.  I am guessing that over the last few weeks that you have used it for something, and that it worked so I am going to assume that is not the problem.

I don't know.  Maybe it is your processor, what are it's specs?
Try Xubuntu that should work better on an older machine.

---

### Post by tommycai on 2006-09-26
64bit 754 amd cpu
kingston 1gb ram ddr2
370gb
9700pro ati card 
two different dvd and cd writers one sony the other one some bec or some kind of company like that
moatherboard is an msi platnium k8n neo I believe
and 500w power supply

I read somewhere that you add something to the string? how do you do this? I forgot where it was at, I was running firefox and then vb said do you want to debug and I click no and then everything closed so now i'm looking for it again.

---

### Post by saule on 2006-09-26
I had the same problem (live CD hanging forever) : then I added more RAM (I had only 128M) and it worked.

---

### Post by tommycai on 2006-09-26
i've got 1gb of ram though?

---

### Post by tommycai on 2006-09-26
> **maaronB said:**
> It is hard to tell.
I don't think that the RAM is the problem, even if it is not enough to actually install Ubuntu, it should still get further than that.

Are you saying you have test 8 different CD's, if so we can saftely rule that out.

So that leaves your CDPlayer.  I am guessing that over the last few weeks that you have used it for something, and that it worked so I am going to assume that is not the problem.

I don't know.  Maybe it is your processor, what are it's specs?
Try Xubuntu that should work better on an older machine.

no i've tried it on the same cd 8 different times and the cd works when you install the cd in the drive after windows boots up it shows the ubuntu program and says that it should look like this when booting up with the cd in the drive and I can install programs off of the cd 

8 times includes in this way
3 times iso burned using nero with download from ubuntu itselft then 3 times with same download using roxio and then using torrent form torrentz of ubuntu using once nero and once agian using roxio still I have the same problem 

when it loads it stalls at "adding live cd user" and does not move any further from that. it said one time error and then goes into a command promt, but I can type words but nothing happpens ??

---

