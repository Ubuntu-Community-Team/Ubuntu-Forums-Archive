---
title: "Am I just dumb?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by lckeeper1 on 2006-08-15
Hey all,

I am having great difficultly getting the Dapper 6.06 Live CD to work correctly. The download goes well, no matter which server I choose, and the ISO file checks out ok with MD5 sumchecker. This is where it gets interesting.

I then try to burn it. I've done so on 2 different machines (one WinXP, one Win 2000). I use CDburnerXP Pro for both. I've burned at only 4x. CDburner tells me that everything is ok and verified. I then put the disc in the drive again, and the splash screen pops up. Everything is A-ok so far.

Then I reboot. At the start menu, I check the disc for errors. I have ALWAYS gotten at least 2 checksums failing. One of them always seems to be the following:

./casper/filesystems/squashfs

The others can vary. I have no clue what this file is, or for.

The other times that I've just tried to start Ubuntu, it goes through the load screen ok, albeit it slowly. Then it freezes at a black DOS looking screen saying "Uncompressing Linux...Ok, booting the kernel" and a small cursor blinking beneath it. I can type in there, but nothing happens at all, no matter the command. 

I am completely new to Linux, and am very eager to challenge myself to learn something new, though I can't even get it loaded correctly!

I've downloaded Ubuntu from every United States Server, as well at BitTorrent. This problem ALWAYS happens, and I'm pretty clueless. 

The machine I'm trying to load Ubuntu on is a Dell Dimension from about 4 years ago. P3 ~1 ghz, 512 ram, 18gb HD, ATI Radeon 9200. 

If you guys could help me, I would be forever indebted. Thanks in advance.


EDIT - Forgot to specify which Version of Ubuntu.

---

### Post by avtolle on 2006-08-15
If you are burning as ISO image, then I am sitting here scratching my head. One thought: if you are actually installing, rather than testing, the Alternate Install CD may be the way to go. I know that prior to the .1 release, often there were problems installing from the Desktop or Live CD due to the graphical installer, but installations using the Alternate Install CD (text based) would go well. HTH.

---

### Post by oss_monkey on 2006-08-15
It seems you're doing everything right, but no matter what happens, the error still seems to appear.

Taking everything in consideration, I think (though I have no basis whatsoever for this theory), that either your software (CDBurnerXP), your CD writer, or your CD-R medium are faulty.

Can you try burning the ISO with another program (I use Nero)?
Can you try burning on yet another machine? (preferably with another program)?
Have you tried using another brand of CD-R media?

HTH

---

### Post by Metacarpal on 2006-08-15
Sometimes even a 4x burn can be too fast, depending on your CD-RW drive.  Try backing down to 2x or even 1x.  It's possible that there are some small errors that your burning software isn't noticing, but which cause the MD5sum check to fail.

Your system specs seem fine for the live "desktop-install" CD.  If you still have problems with a slower burn, though, you might give the alternate CD a try.

---

### Post by wpshooter on 2006-08-15
A couple of questions.  Make that 3 questions.

1) Have you tried simply cleaning the CD-Rom drive ?

2) Is the PIII that you are trying to install Ubuntu on, a computer with no other O/S or does it already have some type of M/S windows O/S ?

3) Do you have any good quality/name brand CD-RW media ?

---

### Post by Metacarpal on 2006-08-15
> **wpshooter said:**
> 3) Do you have any good quality/name brand CD-RW media ?

Ooh - that reminds me.  You're better off using a CD+R or CD-R, rather than a CD-RW.  I've heard that the re-writables don't do so well with burning bootable CD ISOs, Ubuntu or otherwise.

---

### Post by jimmygoon on 2006-08-15
Order one from Ship It or burn a CD at a friends house. Try booting from a completely different ISo from like Slackware or something... just so you can test your CD rom drive.

---

### Post by 3rdalbum on 2006-08-16
I agree with the above poster, but try downloading something small like Damn Small Linux, rather than waste a lot of time downloading a big ISO like Slackware.

Burn to a brand-name disc, definately.

The SquashFS file you mention is the file which basically contains the whole Live system (it's over 600 megs), so unfortunately it doesn't narrow down the problem.

---

