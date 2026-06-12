---
title: "Strange think.. i think"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by codedmin on 2007-05-30
See this little videos (3mbs)

They are from my computer boot after press enter on grub menu until login screen (both windows and linux)

Is this time difference normal?

[http://rapidshare.com/files/34198058/BootTime-codedmind.tar.bz2](http://rapidshare.com/files/34198058/BootTime-codedmind.tar.bz2)

Cheers

---

### Post by hellmet on 2007-05-30
Hmm.. first time tht I'm seeing the reverse :D. 
I'm guessing that ::
1) There are too many unnecessary programs that are being invoked at startup. 
And/Or
2) There is something that is being checked , maybe a file system, or there is some service thats  taking lots of time to start. 

There are plenty of threads on this forum regarding removal of unncessary startup programs.
For the second one, there is some command , I think its Alt-Tab that shows you whats going on, instead of the splash. Try that and let us know whats getting stuck.

---

### Post by plcdfa on 2007-05-30
> **hellmet said:**
> 
For the second one, there is some command , I think its Alt-Tab that shows you whats going on, instead of the splash. Try that and let us know whats getting stuck.
Or you can press e on the ubuntu line in the boot menu, then again on the line stating with 'kernel' and remove the word 'splash' from it. Then prees enter and then b to boot, and you won't have a splash screen, so can see what is taking most of the time int the background. (You can also remove the word 'quiet' if you want plenty of feedback. ;) ) This change is only temporary, splash will be back next time you boot.

---

### Post by codedmin on 2007-05-30
Ok, now i'm @ work, later on i will try that

Thanks

---

### Post by hellmet on 2007-05-30
> **plcdfa said:**
> Or you can press e on the ubuntu line in the boot menu, then again on the line stating with 'kernel' and remove the word 'splash' from it. Then prees enter and then b to boot, and you won't have a splash screen, so can see what is taking most of the time int the background. (You can also remove the word 'quiet' if you want plenty of feedback. ;) ) This change is only temporary, splash will be back next time you boot.

Thanks for that tip :)

---

### Post by codedmin on 2007-05-30
Back home, [here]("http://rapidshare.com/files/34318003/Linux-2.6.22-NoSplash.mp4.tar.bz2.html") is the video without splash screen

If someone can help :)

Thanks

---

### Post by plcdfa on 2007-05-30
Ok so Ubuntu's  boot time is 40 secs (37 secs on first video - the difference is most likely because one partition is  being thoroughly checked the second time due to Xth mounting.) It's not unacceptable, though if you provide your machine's specs we can tell if it counts as slow or not. As for the difference: don't forget that Windows is Windows  and Linux is Linux, and Ubuntu starts much more services at boot time than XP does. (Half of which you probably don't need, but you can always disable them by hand.) Also Win does a larger percentage of these after the desktop is loaded. Anyway none of your boot-time scripts seemed to took unreasonably long to complete, so I don't think there is one piece of them to blame for the delay. (Your progress bar on the first video don't seem to be very responsive to the events going on behind though.)  The boot process went seemingly without problem. (Not counting some hardware initialization error message I couldn't read perfectly - it's supposed to be an USB device, if all of them are working properly than don't worry about it.) If you still want to decrease this boot time I would recommend removing the symlink S30checkfs.sh from /etc/rcS.d, as checking file systems seems to take the most time on your machine, and this script is not vital to start Ubuntu. Be warned though that in this case your ntfs and fat32 partitions may not get mounted on boot if you fail to properly shut down XP the previous time.

---

### Post by codedmin on 2007-05-30
In my first post, i have one link to another file that have a clip width windows boot time and linux with 2.6.20 kernel and splash...

Thanks

---

### Post by plcdfa on 2007-05-31
> **codedmin said:**
> In my first post, i have one link to another file that have a clip width windows boot time and linux with 2.6.20 kernel and splash...

Thanks
Yes, we saw them. What's the point?

---

### Post by codedmin on 2007-05-31
In that compressed file are two movie clips and one text file with my hardware specs...

But here they go

Board Asus P5b-Plus Vista Edition
CPU Intel core duo E6600 @ 3.600Mhz with Tuniq :D
RAM 2GB Gskill @ 900mhz 4-4-3-5
2x80GB Hitachi Sata II raid0
Graphic Card BFG 8800GTS OC2 320MB

---

### Post by hellmet on 2007-06-01
The non-splash video ain't too clear, but I can see that there are errors regarding RAID.
I'm not an expert regarding RAID, so I advice you to ask someone else regarding it.
Also, I think disallowing the filesystem check may get you quicker to login. I'm not sure on this. But, you might risk a error-full-disk :D .

---

### Post by plcdfa on 2007-06-01
> **codedmin said:**
> In that compressed file are two movie clips and one text file with my hardware specs...

But here they go

Board Asus P5b-Plus Vista Edition
CPU Intel core duo E6600 @ 3.600Mhz with Tuniq :D
RAM 2GB Gskill @ 900mhz 4-4-3-5
2x80GB Hitachi Sata II raid0
Graphic Card BFG 8800GTS OC2 320MB

Oh, I missed it, sorry. :oops:

So your boot takes about 40 secs from the "starting up" message to the nvidia logo. On my machine (AMD Athlon64 3200+, " 2GB DDR1 RAM, Maxtor SATA  hdd) it takes 34 secs. Based on that yours is somewhat on the slow side. I have disabled checkfs on my system, but everything else is on default I think. If you do the same you might get a boot time of approximately 30 secs. With extreme optimization you could reach around 25 secs, but not lower. You'll have to live with it, I don't think this is such a horribly long time.

---

### Post by codedmin on 2007-06-01
No it isn't.

This is more like wooww windows xo is fast!? To be honest i never realised xp is fast... well at least it is in this machine:D

Cheers

---

### Post by plcdfa on 2007-06-01
XP boots faster on my machine too. But on the other hand it's not a bit faster when working with it, and that's what really counts. Also as I wrote above XP "cheats", cause it starts a lot of services after it displays the desktop.

---

