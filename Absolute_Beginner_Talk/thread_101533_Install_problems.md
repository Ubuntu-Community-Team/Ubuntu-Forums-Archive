---
title: "Install problems"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by boomerian on 2005-12-10
I can't believe I have two bad CDs (Ubuntu and Kubuntu 5.10) but neither will complete an install.
I have tried both 'normal' (full) and 'server' (minimal). It is not a dual boot, I am installing on a Celeron 400MHZ machine with 6.4 GB HDD and 192MB RAM. (Admittedly an older, slower machine but should handle Ubuntu, no?)
I get 71% through the 'Install the base system' portion and get stopped with the error:
 
[!!] Install the base system
Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
Check /target/var/log/bootstrap.log for the details
<Go back>               <Continue>

Whne I tried the 'server' install with the Ubuntu CD, I reached roughly the same point and was stopped with another error but it was 'trying to install the kernel-386' package.

I am a complete newbie but willing to learn, and this has me stumped. I can't continue with any other installs and the machine will not boot without one of the CDs in the drive (GRUB did not install, not would either CD allow me to install LILO).

Can someone walk me through the resolution of this? What have I done wrong? Very discouraging, and I've invested about 3 1/2 hours so far...
Thanks for any help/encouragement:confused:

Seems pretty quiet - no readers or responders. I'm off to bed now and I'll check in the a.m. here.
My goals are modest - get up and running with Ubuntu (or Kubuntu) as the only OS on an old machine, lean and as fast as it can run for browsing and limited other packages to learn about Linux.
I'm sure I'll have numerous other questions when I can get something loaded and going. (If you can't get it loaded, is it still an 'operating system'???? Cheers, and good night...

---

### Post by davmac on 2005-12-10
I agree, it seems unlikely to have two duff CDs, but then again, it is not impossible and the only time I've seen these sort of problems have been when there's a problem with the CD.

Dave Mac

---

### Post by darrenn on 2005-12-10
My advice is to download the live cd version of ubuntu.

---

### Post by Rackerz on 2005-12-10
I'd try downloading the ISO, then burning the ISO yourself in Windows. It's a good way to make sure you wont have any problems.

---

### Post by davmac on 2005-12-10
Before burning the ISO to a CD make sure the checksums match - so you can confirm that the image has downloaded correctly.

Have a look at [http://lists.debian.org/debian-user/2003/03/thrd2.html#00756](http://lists.debian.org/debian-user/2003/03/thrd2.html#00756) for a good thread on how to verify your CD or ISO image.

Hope this helps,

Dave Mac

---

### Post by Rackerz on 2005-12-10
[QUOTE=davmac]Before burning the ISO to a CD make sure the checksums match - so you can confirm that the image has downloaded correctly.

Have a look at [http://lists.debian.org/debian-user/2003/03/thrd2.html#00756](http://lists.debian.org/debian-user/2003/03/thrd2.html#00756) for a good thread on how to verify your CD or ISO image.

Hope this helps,

Dave Mac[/QUOTE]

Yeah that's a good idea. I always burn things in Windows, it's about the only time in Windows i have some re-assurance.

---

### Post by routerstu on 2005-12-10
i had the same thing but found out it was a bad download.  you can verify this with the md5.  there is a free windows checksum tool command like tool called fastsum, google it up.  i downloaded another image, ran it, matched and the install went flawless.

---

### Post by mcduck on 2005-12-11
It's also a good idea to use the torrents instead of normal downloads, as bittorrent automaticly checks files for errors. It's also faster. Then burn the disk at max 4x, it takes a bit longer but it's still faster than burning and trying couple of disks ;)

---

### Post by Ruddog on 2005-12-11
Umm, I had some disc's sent to me via the official distrobution by mail. I am trying this out on my amd64 laptop with the 64 bit CD. So, this kind of throws out the bad download theory others are citing. I am going to try out another 64 bit disc and if it does it again, I am going to try the regular version of 5.10 from yet another mailed CD. 

I should add, I have had both the 64 bit and regular install versions of pre-release and they both ran the install without a hitch. 

Possibly a release problem?

---

### Post by Ruddog on 2005-12-11
Well, I digress. It seems the CD that I received was bad. Luckily, I ordered a few extras as the second CD worked.

---

### Post by unisol on 2005-12-13
run livecd version first to see if you system is compatible if it is then d/l and burn to a cd and do the install

---

### Post by marcris on 2005-12-13
Just to let you know you're not alone. I had the same error on installing on my Sony Vaio  laptop. The disk was the official distribution by mail. I'll have to try and get one of the other disks back from the friends I gave them to, and try that. But maybe not now, cos I just successfully upgraded from Hoary over the net.

---

### Post by frootstripe on 2005-12-13
I can second that ubuntu.org cds have problems, I tried twice with 2 different cds (ubuntu 3.10, both), and both aborted at base install with different issues - debootstap, kernel failure.

Luckily, a third party 3.4 Kubuntu installed w/o problems on other partitions.

Sounds like the best bet is going with a  bittorrent iso.

---

### Post by apletosu on 2005-12-14
I just had the same problem - always stopping in the same place - initrd-tools. I re-burned the CD image at 4x (was at 10x before) and it installed like a charmed. I was using a CD-RW but I don't think it make a difference.

Conclusion: slower is better :) There was no problem with the image per se - just with the CD writing speed

---

### Post by boomerian on 2005-12-16
Thanks to all for the various suggestions.
I have a growing collection of 'coasters' (or as some would day "coffee mats"), and I have been burning at lowest possible speed, using Nero.
I haven't been able to figure out how to validate the burned CD via checksum.
I have ordered the CDs from Ubuntu, but am eager and don't want to wait for the mail.
Now I have the partial install on my tired old machine, and it seems futile to try yet again. I think I will try to burn a live CD and see what happens...
Cheers

---

