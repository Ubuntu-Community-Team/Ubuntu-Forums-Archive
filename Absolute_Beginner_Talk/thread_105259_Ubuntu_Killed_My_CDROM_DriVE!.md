---
title: "Ubuntu Killed My CDROM DriVE?!?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-18
I have had Ubuntu install on my computer for about 3 or 4 months now and just recently trying to mount a CD I was constantly getting stuck with the same error.

(Something about No medium in drive and couldn't execute pmount.)

Well after trying to boot a CD from start up I noticed that my CD Drive wasn't reading at all, infact there was a loud hiss and wirrling sound.

After Buying a New CD drive and placing it into my LinuxBoX everything is back to normal and I can now enjoy my CDs again.

So my question is...
Has anyone else had this experiance happen to them?

---

### Post by bscbrit on 2005-12-18
It is most unlikely that Ubuntu killed your CDROM drive. Your drive might have failed while ubuntu was installed - but it would have failed anyway regardless of which OS was on your computer.  How old is the drive?  Don't worry, with the number of Ubuntu users, or even Linux users, we can assume that there is nothing out there damaging your hardware.

---

### Post by snellgrove on 2005-12-18
Yeah, I dont think its possible for software to actually kill a piece of hardware :D just an unfortunate coincedence!

Still, a dead piece of hardware gives you the excuse to splash out on something better, eh :D

---

### Post by nitricacid on 2005-12-18
[QUOTE=bscbrit]How old is the drive?[/QUOTE]

The Drive came with the computer. so it might only be about a Year and a half old.
I got the computer brand new from D][=][eLL.

[QUOTE=snellgrove]Yeah, I dont think its possible for software to actually kill a piece of hardware :D just an unfortunate coincedence!

Still, a dead piece of hardware gives you the excuse to splash out on something better, eh :D[/QUOTE]


Actually along time ago I used WIN-NUKE to completey blow up some1's computer, That was software destroying hardware.

---

### Post by Leif on 2005-12-18
[QUOTE=nitricacid]Actually along time ago I used WIN-NUKE to completey blow up some1's computer, That was software destroying hardware.[/QUOTE]

I'm not sure how causing a bsod equates to "completey blow up some1's computer". no hardware is affected by this

---

### Post by bscbrit on 2005-12-18
Actually, there is no minimum period before a component fails.  The figure of Mean Time Between Failures (MTBF) is a mean or average time. (Yes, I know that they are not the same statistically - but that is irrelevant for this point).  So some components may last years but some, only a small percentage it is true, may fail in a matter of days or weeks.  My own experience is of a CDROM drive that only lasted a little over 1 month from time of purchase. It wasn't abused, subjected to unusual voltages or asked to operate 24hrs a day.  It just died.  So the fact that yours lasted say 18 months is nothing to complain about - although I'm sure that you wish that it was still covered by some kind of warranty!

---

### Post by estel on 2005-12-18
After installing libdvdcss2, but DVD drive failed to read DVDs. Hard to convince myself it wasn't the program, but I did in the end (and got a replacement drive - it was still under Warranty)

---

### Post by xchrisday on 2006-05-17
Hi all

I basically had a similar problem with fedora core under a gnome setup.

It appears under various linux distro's once media is inserted into the drive the read light is constantly illuminated which i can only assume means the laser is constantly firing.

My sony dru530 drive which had worked fine under windows died after 3 days of fedora core leaving me without a dvdrw/cdrw drive. I have since purcahsed a benq dw1650 and installed ubuntu but I'm having a similar situation, whenever media is inserted the read light is constantly illuminated regardless of if I'm accessing the drive. Obviously I dont want my new drive to go the way of the sony and would like to know if I can make it so the read light is not constantly illuminated when media is inserted... at a guess I think this would involve only mounting the drive when im reading it, rather then when there is media inside the drive?

Also, the sony drive was three years old and reasonably abused... Im willing to accept it died of its own hand but would like to think linux isnt placing needless stress on the drives?

---

### Post by xchrisday on 2006-05-18
No-one willing to comment on the process by which linux access's and controls the cdrom drive?

Like i said Im concerned mainly with the amount of time the laser is firing while the drive is mounted but not not reading.

edit: spelling

---

### Post by macdo on 2006-05-18
I don't think that because the read light is on, the laser is. If it is, it's always reading the same point on the disc. 
And how do I know this? Well, when I read this thread, I decided to check it out. My DVD drive is **very** noisy (in its defence, it's getting on for seven years old, and is the only part of my PC that hasn't been replaced at least once...) and so I can hear it as soon as it spins up. 
So I mounted a random data cd and had a listen.
Conclusion, the disc isn't spinning, which allows me to conclude that the laser is not actually working...

I could be wrong about this, of course, so if you (or anyone else) have any counter-arguments, please do say so!

Macdo

---

### Post by Dr. Nick on 2006-05-18
If anything I think it would be something similar to this, but I would think all this type of stuff has been fixed since then, or you would here alot of talk about it like you did back then

[http://www.theregister.co.uk/2003/10/29/mandrake_linux_ate_my_cd/](http://www.theregister.co.uk/2003/10/29/mandrake_linux_ate_my_cd/)

---

### Post by xchrisday on 2006-05-19
Yeah, this seems to be what has happened to my sony dru530a. The drive was pretty fubar afterwards and yet worked fine before, it also failed during a iso write which sounds like it fits in with this cache clear thing.

Then again it could just be the drive failing of its own accord.

---

### Post by 3rdalbum on 2006-05-19
I had a Sony Discman that failed after trying to play some shoddy CDRs, none of which contained any open-source software.

---

### Post by steve.horsley on 2006-05-19
Mandrake Linux did a similar thing to my floppy drive. One day I went to use it, and there was a horrible noise from the drive. I took it apart only to find inside:

* An allen key
* A used train ticket
* An unused ty-wrap
* A clothing price label 

If I'd been using Windows then I would have blamed my 3-year old boy, but as I was running Linux I just knew it was the fault of the OS. The floppy drive never did work properly again, but the allen key still works fine.

---

### Post by skippy81 on 2006-05-19
There is no way Linux or any other OS could have damaged your hardware. 
 
Also, WinNuke is a denial service attack, it floods the IP stack of older Windows versions - in no way does it damage the hardware, or even the software permanently.  The only way I can see software damaging hardware is with an overclocking utility.  

You should be glad that its only a CDROM which has failed - probably the cheapest component in a modern PC.

---

### Post by macdo on 2006-05-19
steve.horsley: Great reply, thanks. I needed a laugh!

---

### Post by steve.horsley on 2006-05-19
Actually, there was a case a few years ago of a particular version of Mandrake that trashed a particular make (LG) of CD drive. The hardware probing that the installer did triggered a flash firmware update routine in the drive - the drive erased its firmware but never got given the replacement code of course. Return to factory.

The problem was that the hardware probing just happened to use an instruction (flush write buffer IIRC) that LG were (ab)using for an entirely different purpose (to re-flash the drive). 

LG eventually released a program to re-flash the dead drives, Linux changed the way it did hardware probing, and I think LG stopped making that kind of drive. Anyway, it's an old problem - old kernel, old drive type, and doesn't happen any more.

---

### Post by man.vvip on 2008-04-04
Wow, it also happened to me. Kubuntu 7.10 killed my CD-ROM, It was an Asus Burner,
Used to burn real well, before Kubuntu ate it during install, Lol

---

