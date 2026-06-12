---
title: "Painfully slow install!? What's going on?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by mislav on 2007-05-10
Hi everyone, I'm trying to become a Ubuntu user, but so far this transition has been giving me nothing but grief.

I've tried for the last five hours to install Ubuntu 7.04 from a LiveCD I've downloaded from Ubuntu.com and it is running abnormally slow and only got to the point of 66% of starting partitioner!

This can't be normal! 

I've checked the CD, the computer is otherwise working fine, I've restarted it several times, I've burned the CD at lower speed (4x), I've disconnected Ethernet from it... nothing! Still crawls... :(

We're talking about a two year old desktop with Celeron of some kind... not the powerhorse, but also within requirements for Ubuntu install.

Can anyone help?

---

### Post by BHelts on 2007-05-10
I'd be inclined to have you test the hard drive.  S.M.A.R.T check will let you know the seek error, write error, read error rates and your reallocated sector count.  It could be slow because your hard drive is on the outs.

---

### Post by mislav on 2007-05-10
Thanks, but I really doubt that this is the case. After the first restart, I've booted back into (now probably erased) Windows XP install and checked whether everything was working. No errors reported anywhere... 

Windows run at their normal speed while Ubuntu is running so slow I wouldn't believe this myself have I not seen it with my own eyes.

---

### Post by gohanssjn on 2007-05-10
I hate to say it, but I agree with running the check.  Also, if it is hanging on partitioning, maybe something is wrong with the partition table that needs to be addressed first?

---

### Post by mislav on 2007-05-10
I've ran Scandisk and the disk appears ok. I'm not familiar with S.M.A.R.T. check, I'm a Mac user - Windows are not my forte...

---

### Post by kittyhawk63 on 2007-05-10
An alternate suggestion:
If you are trying to install Linux on a clean hard drive, try either running fdisk or run the CD disk that came with your hard drive. Repartition the drive starting fresh by removing the partitions and then set up the partitions again. With fdisk, I set up a primary partition only since I only run one OS on each of my two hard drives. Afterwards, you "format" the hard drive. That works for me. At least you will know that everything has been cleaned from the hard drive. This has helped me to install a LiveCD when I was having similar problems.
You can get a free copy of fdisk off the Internet. That is where I got mine. Make sure you trust the site. I did a check on what others said about the site. The format command came with my fdisk download.
Hope you get this working soon.
kh

---

### Post by BHelts on 2007-05-10
if you are interested, you can download the Ultimate Boot CD.  it has a s.m.a.r.t program and you can test your hard drive.  i know you don't think that that is what it is, but it will at least help rule that possibility out so we can further troubleshoot.

[UltimateBootCD]("http://www.ultimatebootcd.com")

---

### Post by JOrtiz8612 on 2007-05-10
Maybe the problem is the actual CD itself?

---

### Post by Done_Fishin on 2007-05-10
I actually downloaded the 6.10  CD and installed from there a couple of weeks back. It went without hassle. I downloaded the 7.04 and tried to install to a fresh GOOD disk. I gave up and used the 6.10. I think there's a bug in it somewhere. Instead of getting a graphics window like in 6.10 I was getting a listing of everything on a black screen showing errors of some kind.  Like I said 6.10 was breeze whilst 7.04 was a major headache. I updated to 7.04 on-line since I have a fast broadband link.

---

### Post by BHelts on 2007-05-10
You could also check your RAM.  Bad RAM can cause severe bottlenecks.

---

### Post by ZeroWing on 2007-05-10
You guys are trying to hard. When I had this problem, all I had to do was go into my BIOS and reset it to default. Worked fine then.

---

### Post by nickpaton on 2007-05-10
Hi Mislav and welcome to Ubuntu and the forums!

Sorry to hear of your problems, but we need to check a couple of things:

> **mislav said:**
> I've checked the CD, the computer is otherwise working fine, I've restarted it several times, I've burned the CD at lower speed (4x) 

You've done exactly the right thing in burning the CD at a slower speed, but when the CD first starts the installation, you come to the first 'window' which gives you various choices including installing the OS.  There is another choice which checks the CD to make sure all the programs have been downloaded and burn OK..
If this comes back saying there are errors, then you MUST sort this out first.  It means you have a damaged program(s) on the CD.
Are you using a CD-R to burn onto?  If so is it a good quality CD-R?  If you are using a rewritable CD-RW then it will not burn properly. 
If you are 100% sure that the burning to CD bit is OK, then you need to go back to the site where you downloaded 7.01 and also download the md5 checksum which checks the integrety of the downloaded program.
If you don't know how to do this get back to us.

> **mislav said:**
> I've disconnected Ethernet from it... nothing! Still crawls... :( 

Connecting or disconnecting the Ethernet cable will not usually make any difference to the installation speed, and I don't think this is your problem.  I would recommend leaving it plugged in so that it can go straight into installing upgrades.

> **mislav said:**
> We're talking about a two year old desktop with Celeron of some kind... not the powerhorse, but also within requirements for Ubuntu install.

One of my Ubuntu PC's is very low spec'd indeed, and happily installed 7.01, BUT it did need 512Mb of memory to do it.  This is despite the minimum 'theoretical' memory requirement being 256Mb.
How much memory is installed in your PC?

Also one of the other guys mentioned about checking your memory.  This can be done again at the first 'Window' where you will see another choice to check memory using memtest (or similar title!).  Run this and it will give a basic check as to how good your memory is.

Another alternative if all this fails, is to try 7.01 alternative which is for lower spec'd PC's.

let us know how you get on and good luck!

---

### Post by mislav on 2007-05-10
Thank you everyone for your suggestions, I've learned some new things from your responses.

Anyway, I've tried to install Ubuntu from an alternate CD and the non graphical install went fast and smoothly! I'm actually typing this running Ubuntu! It's my first Linux system ever, so expect to hear a lot more from me in the future... I'm bound to have lots of questions. ;)

I'm not sure why graphical install repeatedly failed, I've checked and rechecked the install CD in every way I could - it appeared ok on all tests. Well, perhaps this experience might help someone else with the same problem... Thanks again everyone!

---

### Post by nickpaton on 2007-05-10
Well done!

keep the question coming.

---

