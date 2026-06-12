---
title: "All disks failing disk check?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by wilsonisme on 2006-02-03
Quick question:
I have downloaded ubuntu/kubuntu numerous times and installed on numerous machienes (I have having a problem installing it on my most powerfull one but that is a whole different story and a whole different thread)

Anyway, I have NEVER had a ubuntu disk I have burned pass the disk check utility. Is this possible? Should I keep downloading/burning until I get one to pass, or does it matter, or will it never pass unless I buy a pre made CD?

Btw, I have used different computers, ISP's, and burners..

I also have had disks that do not "pass" install ubuntu fine, so im at a loss. I dont want to keep wasting disks if I don't have to.

---

### Post by o_fortuna on 2006-02-03
[QUOTE=wilsonisme]Quick question:
I have downloaded ubuntu/kubuntu numerous times and installed on numerous machienes (I have having a problem installing it on my most powerfull one but that is a whole different story and a whole different thread)

Anyway, I have NEVER had a ubuntu disk I have burned pass the disk check utility. Is this possible? Should I keep downloading/burning until I get one to pass, or does it matter, or will it never pass unless I buy a pre made CD?

Btw, I have used different computers, ISP's, and burners..

I also have had disks that do not "pass" install ubuntu fine, so im at a loss. I dont want to keep wasting disks if I don't have to.[/QUOTE]
If they don't "pass" the disk check utility, it may not even be anything to worry about as long as the install goes ok. You could try burning at a lower speed, and try downloading the ISO files with bittorrent (which automatically checks the MD5 sum on the downloaded ISO image to make sure it's ok). But like I said, if it installs, you're fine. I had a live CD that worked only 50% of the time, and it failed the disk check utility. I never checked my other CDs though, so I'm not sure exactly how accurate the disk-check is.

---

### Post by Herman on 2006-02-03
> Anyway, I have NEVER had a ubuntu disk I have burned pass the disk check utility. Is this possible? Should I keep downloading/burning until I get one to pass, or does it matter, or will it never pass unless I buy a pre made CD?
Btw, I have used different computers, ISP's, and burners..
I also have had disks that do not "pass" install ubuntu fine, so im at a loss. I dont want to keep wasting disks if I don't have to. [This thread ]("http://ubuntuforums.org/showthread.php?t=100657&highlight=md5+check+iso")is my favorite one on this subject. Everyone should be doing what fourchannel explained there.
I think it is important since I recently noticed some odd behavior myself caused by (I suspect) a small scratch on my trusty old home-burned 'Breezy' install disk. It caused some strange things to happen when installing.
I wonder now what percentage of the problems people have installing Ubuntu are due to 
1. bad .iso downloads
2. badly (to fast) burned CD-ROMs
3. the use of the cheapest CD-ROMs money can buy (poor quality, ok for audio but not for software)
4. CD-ROM drives not performing as well as they should (both during reading and burning) 
5. Dirt, fingerprints and scratches on CD-ROMs.

We may never know for sure, one can only imagine. :-D (Herman)

---

### Post by Bartender on 2006-02-11
Herman -
Can you elucidate some more on md5's?  I want to to get a handle on how Windows users can check their CD's BEFORE wasting time trying to install.  The .iso download's have one checksum.  This is easy enuf to verify.  The numbers are right there on the download website and there are dozens of checksum utilities for Windows users to download (I like md5Summer because it's pretty darn easy).  I d'loaded the Kubuntu i-386 .iso a coupla weeks ago and was able to verify.

Where I start getting into trouble is with the CD that results from burning the .iso.  I know my burn utility chose the correct method so I don't want to veer off into that discussion.  
The resulting CD has 8 folders & 2 files.  One of the 2 files (README.diskdefines) is a short read-me that I didn't understand and the other (md5sum.txt) is a list with HUNDREDS of md5 checksums.
  
I figure a Windows user getting ready to do something with his burned disc (burned at 1X or 2X speed of course) needs to be able to check those 8 folders.  He can run the CD thru a checksummer but where does he turn to verify the numbers are correct?  The huge list of md5's appears to contain checksums for every single file within those folders - there's gotta be a way for a Windows user to just check the eight folders.

I have to explain something.  I have 2 computers, one is strictly W2K (PC1), the other (in sig) is dual-boot W2K/ubuntu.  We'll call that PC2.

I'm just getting my toes wet w/ Ubuntu.  Found directions for checking md5's. I dropped a stamped Ubuntu i-386 install CD into PC2 and entered "sudo md5sum /dev/cdrom".  Was expecting ten but only got one checksum back.  Read somewhere that Ubuntu will look at the root of the CD while Windows won't (or something like that).  Maybe that's what happened here.  

However, the single checksum that Ubuntu generated -
0e9b08403c25e70e09880fb49726f551
doesn't match the original checksum listed on the download site!  Shouldn't the stamped CD - if reduced to just one sum by Ubuntu - match the .iso checksum?

I can't double-check this on PC1 because I haven't been able to get it to recognize any of the 10 stamped CD's - install or LiveCD - I received.  Weird.

OK, let's try this - I'll take the Kubuntu CD that I burned from the .iso download on PC1 and run it on PC2.  I installed Kubuntu from that CD to PC2 a few weeks ago before re-formatting & going back to Ubuntu.  On PC1 md5Summer gave me a checksum for the download that matched the website's.  

I just can't catch a break here...PC2 failed to verify the Kubuntu CD.  It spun the CD for a few minutes like it did with the stamped Ubuntu CD, then reports, "md5sum: /dev/cdrom: Input/output error"  PC1 can read the burned Kubuntu CD but not the stamped Ubuntu CD's, and PC2 can read the stamped Ubuntu CD's but not the burned Kubuntu CD.  Story of my life

So, questions...

#1 Where does a Windows user go to verify the 8 folders on a burned CD?
#2 The md5 that Ubuntu generated from the i-386 install CD - it doesn't match the .iso.  Is that the way it's sposed to be?
#3 What does "input/output error" mean in this context?

---

### Post by Herman on 2006-02-12
>  #1 Where does a Windows user go to verify the 8 folders on a burned CD?
#2 The md5 that Ubuntu generated from the i-386 install CD - it doesn't match the .iso.  Is that the way it's sposed to be?
#3 What does "input/output error" mean in this context?                                          
Bartender, you are asking some very interesting questions and I am still looking for some better answers, but it might take a while, so here's what I know so far.

For #1 and #2, from what I can find out, the correct md5sum for the ubuntu-5.10-install-i386.iso for a few sites where I looked it up around the world
is > 126751a2dc5528c2f9044d9e4ee36d61 That's what the md5sum is supposed to be from the download site I use, Telstra Bigpond here in Australia too.
Most of the when I md5sum a downloaded .iso from Bigpond it matches their  md5sum for that file shown on thier website.
Once or twice it hasn't, but deleting the file and downloading it again normally works. I don't know why I don't get the perfect file download 100% every time, but that I guess indicates we don't have to have a very big error in the lines or in the copying to put the md5sum out.

Okay then, so I verified the md5 for the downloaded .iso. I and I'm happy I have a good .iso to begin with. Now I burn it to a disk, and then dd the .iso back off the disk with this, like fourchannel suggested: ```
dd if=/dev/hdc of=ubuntu.iso_after_burn.iso
``` Then I do: ```
md5sum ubuntu.iso_after_burn.iso
``` And the result of that is this:> 952a0c6be78928199c1a1517d7b511f2 ubuntu.iso_after_burn.iso
 Notice it is not the same number as I had when I checksummed the original .iso.
I know, (or think I know), it is the correct md5 number for the CD once it has been burnt to a CD and then copied back to disk using the 'dd' command only because I have done this a few times already and recorded the results. Nine times out of ten when I burn a CD from the same .iso I get this checksum and I know from experience that it will produce a normal install.

I don't know where you would find that information if you were a Windows user doing a first time install, but here it is if anyone wants to know.

About one in ten or even maybe more CDs I burn get a different md5sum returned by the afterburn test. Some will still produce what seems to be a relatively normal install, but obviously I would expect it to be flawed in some way that might show up later on.
Other times the CD will cause the install to vary from a regular install in ways that are more obvious and erratic, as you may expect. 
I'm not sure why my CD burner doesn't always burn the .iso file and read it back perfectly. It could be faults and imperfections in my hardware or in the media or even maybe environmental factors. 

I had 'shipit cds' once too (for Hoary), and some of those didn't perform well, but I guess they are free, and they gave me ten, so if one didn't work I just tried another. I didn't know how to md5sum them at that time.

As for #3, I don't know, I tried it too and got the same error.

---

### Post by Bartender on 2006-02-13
Herman -
I really appreciate your experiments to see if you get the same results or not.  Interesting about the "input/output error".
If you've got a few minutes maybe you could check this thread, where I babbled on about md5's yet again.

[http://www.ubuntuforums.org/showthread.php?t=128673](http://www.ubuntuforums.org/showthread.php?t=128673)

Would like to come up with a rock-solid method to help Windows users make a viable CD.  Checking the download is easy but checking the burn isn't.  Well, maybe it is but I haven't gotten there yet.  Apparently Dapper will include some sort of checking utility for the burn and that would be super.  
But what do we do for all the folks trying Breezy right now?
Wonder if someone could post a list of "The Top Ten Questions Asked This Month" and we could put some heads together?  I'd like to help but would probly just get in the way :-D

---

### Post by Herman on 2006-02-13
Bartender, I think you are doing everyone a big favor by raising everyone's awareness of this. To my way of thinking it's a very important issue, and one that needs more work for sure!
 I think if people just check the whole burned CD by fourchannels or stuporglue's method, (whichever works for them), it will be easier than checking the the eight folders though. The md5sum is a good strict quality control test and even if there was one byte of difference in the whole CD it would show up as a very different md5sum output. (Most people won't do things they are supposed to do already so they will probably want to do something in fewer steps, or they'll skip the whole issue and leave it in the 'too hard basket').

EDIT: Oops! I keep frogetting they are still in WIndows and can't do all the things we can do when we have Ubuntu installed already, (it's a little early in the morning for me right now-sorry). Well I think probably your eight directories method might be the way to use then, I'll look into it more when I get home from work.
 
You did a good job finding out the right md5sums for the downloaded .iso 's and listing those in your post you linked to. We should get a corresponding list together for verifying the CDs after they are burned, because I haven't seen one of those around anywhere.

If people are starting off with bad .iso's or burnt CD that are corrupt, no wonder they have problems surfacing sooner or later, either as major install headaches, or minor hiccups and hassles further into the future. 

Actually though, we should also be editing their /etc/apt/sources.list and updating their repositories in synaptic right after we install too, and using the 'fix broken packages' function. I think once people get to that stage they would be okay. The 'fix broken packages' thing should rectify any problems as long as they reach that stage. Then again, there are those who don't know they should do that. It's very easy, people need to be reminded to do it though.

I will for sure include more information emphasising on these two subjects in the dual boot website next time I update it. Thanks for bringing this subject up, I think you are doing a great job, and I think it's an important issue, regards, :-D (Herman)

---

### Post by sparhawk on 2006-02-14
[QUOTE=Herman]The md5sum is a good strict quality control test and even if there was one byte of difference in the whole CD it would show up as a very different md5sum output. (Most people won't do things they are supposed to do already so they will probably want to do something in fewer steps, or they'll skip the whole issue and leave it in the 'too hard basket').[/QUOTE]


Well actually md5 is not all its cracked up to be. Here is an artical about its flaws
[http://www.internetnews.com/security/article.php/3446071](http://www.internetnews.com/security/article.php/3446071)

I also watched a guy generate a md5 hash from 2 completely different websites last year at defcon and it generated the same exact hash.

Even on my crypto tunnels I have switch from md5 to sha-1

Just something to think about...:-k

---

### Post by Bartender on 2006-02-14
Geez, sparhawk -
I thought that in all this confusion at least the md5 checksum was the one absolute truth, and all I had to do was find a clear path from download website to a burned CD that anyone could prove to their own satisfaction was good.  Now you throw even that into question!

---

### Post by Herman on 2006-02-15
>  Well actually md5 is not all its cracked up to be. Here is an artical about its flaws
[http://www.internetnews.com/security...le.php/3446071]("http://www.internetnews.com/security/article.php/3446071")
I also watched a guy generate a md5 hash from 2 completely different websites last year at defcon and it generated the same exact hash.
Even on my crypto tunnels I have switch from md5 to sha-1
Just something to think about...:-kThanks, sparhawk, okay so fortunately Telstra Bigpond also has the sha1 sum posted there for us near where we click to download our 'Breezy' .iso.  I don't know if all download sites do or not, so here it is:> **SHA1 Sum:** 01e7e5f6142f6e5b1f1f5581aac53dc30fcc5d65 So now I have done:```
sha1sum ubuntu-5.10-install-i386.iso
```and, for mine at least, I have had the correct hash returned, so I guess that means now I am twice as safe, my 'Breezy' .iso *just can't possibly be corrupt* if it passes *both* of these strict tests.
Thanks, I will add this advice to the /hermanzone website the next time I update it. :-D (Herman)

---

### Post by sparhawk on 2006-02-15
[QUOTE=Herman]Thanks, sparhawk, okay so fortunately Telstra Bigpond also has the sha1 sum posted there for us near where we click to download our 'Breezy' .iso.  [/QUOTE]

Sorry to be the bearer of bad news but sha1 was broken also...
[http://it.slashdot.org/article.pl?sid=05/02/16/0146218](http://it.slashdot.org/article.pl?sid=05/02/16/0146218)

and then again only faster and more efficient...
[http://www.schneier.com/blog/archives/2005/08/new_cryptanalyt.html](http://www.schneier.com/blog/archives/2005/08/new_cryptanalyt.html)

Come to think of it... what the hell is secure these days?

---

