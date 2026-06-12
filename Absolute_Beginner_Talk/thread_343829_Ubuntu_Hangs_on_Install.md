---
title: "Ubuntu Hangs on Install"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-01-22
Hey all! Complete noob with Linux here!

Trying to install Ubuntu on the server at my work, we had a "linux guy" come out and fiddle with Ubuntu 6.06 and when that didnt work he tried Fedora 6 which still didn't work! So basically we paid him to sit on the internet and "research" and watch countless linux installs for 2-3 days. I can do that just as easy as he can! The main issue he thought was the RAID card we have (PROMISE FASTTRAK TX4310). So when we called up the computer shop who supplied us with the server (we specifically asked it to be usable with Ubuntu) they told us that Ubuntu 6.10 worked! So now I have tried to install ubuntu 6.1 still to no avail!

So thinking it was the RAID card, i pulled it out and tried installing on the IDE hard drive (which might have already had a install of linux on it? Could this be a problem? How can i format it to linux format? Shouldnt the installer do this?)

The problem with Ubuntu 6.06 is that it would decompress linux kernel, say ok, and then hang trying to open it. (Which was what happened before i took the raid card out)
Ubuntu 6.1 will try to install and the progress bar will get most of the way to the end and it will freeze. I let it go for a bit and the cd popped out by itself and it loaded grub upon reset but we had grub working before i installed it and i can't work out if it was installed prior or post 6.1.

I am pretty noob with the command line commands, I understand command line (DOS etc) but i have no idea of the commands i need.  I found a fix for Ubuntu 6.1 which should fix my RAID card, but it was in a different language so I am hoping the translation is good.
I found this: [http://ubuntuforums.org/showthread.php?t=268570&page=2](http://ubuntuforums.org/showthread.php?t=268570&page=2) - But these guys can install AFAIK. And i should be able to install on a IDE hard drive!

Specs:
p4 3.6 Dual Core
ASUS p5b mobo
2 gig 667 Corsair Value Select
Promise Fasttrak 4310 RAID card.
4x 250gig WD SATA hard drives

Any help would be greatly appreciated.
HIS x700-SE 256meg PCI-express

---

### Post by rai4shu2 on 2007-01-22
This is just a guess, but it seems like Fedora probably ran into a dmraid issue and your Dapper/Edgy install more than likely has trouble with the mobo. Linux has issues with certain USB2 controllers prior to 2.6.18 (and Edgy uses 2.6.17), so you may need to either try a distro with the latest kernel or just disable USB2 in the BIOS setup.

---

### Post by renzokuken on 2007-01-22
i had an installation that hung at exactly the same point.

after some "fiddling" with the bios, i disabled the option "support for legacy USB" and enabled SMU, and hey presto it worked.........

i'm not saying it will solve your issue but it may be related

---

### Post by mattdwilnew on 2007-01-22
Well I have disabled USB legacy, and it still hangs at the same place. 
I tried a few different boot commands for 6.1 yesterday before trying the USB thing and it gave me an error that said: kernel panic-not syncing VFS Unable to mount root fs on unknown-block (8,1) (numbers im unsure about).

Any idea why?

---

### Post by mattdwilnew on 2007-01-22
I am downloading the custom install cd now, hopefully it will provide some documentation as to what the commands do!

---

### Post by wpshooter on 2007-01-22
Matt:

A few questions.

Are you burning your Ubuntu CDs at 4X or less ?

Are you checking the integrity of your Ubuntu install CD by running the verification function found on the initial Ubuntu boot screen menu ?

Have you run the memtest found on that same menu ?

Is this computer going to be Ubuntu/Linux ONLY machine or is it going to have other operating system(s) on it ?

---

### Post by mattdwilnew on 2007-01-22
Thanks for the response.

No i have not burned it at 4x or less.

When i tried to verify cd it hung at the end, but without the glitchy line through the progress bar.

Ill burn the cds at 4x and give it a go.

I got a 6.06 pressed cd, so ill see if that passes the cd test as well.

Doing memtest now 77% ok so far.

---

