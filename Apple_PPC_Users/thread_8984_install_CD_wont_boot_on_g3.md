---
title: "install CD wont boot on g3"
date: 2004-12-22
forum: Apple PPC Users
---

### Post by questionasker on 2004-12-22
got an old MAC G3 collecting dust. ive heard alot about Ubuntu, so i thought id give it a whirl. saw they had a PPC version, so i thought id use this old comp instead of my regular test comp.
these are the pressed CDs from ShipIt.

its a all-in-one G3, 266Mghz, 32MB RAM, 6Gig HD. i know it can boot from CD-ROM, i just updated to 9.2 with a CD.
also have a regular g3 tower and seperate monitor i might use. i saw something on these forums about wishing for a non-BootX way to install on the beige G3. can someone explain this to me if these two comps arent supported? or tell me what to try to start the Ubuntu install?
thanks for help...

---

### Post by MacAdmin on 2004-12-28
Can you clear how many macs do you have?
As I understood you have iMac G3 and beige G3.
Those computers are "old age"
There are two way to install Linux on PPC one way for "old age" (first iMac's 233MHZ example) you would need to install Boot partion, you can search web for "yaboot" info, I will try to find instructions on my HD.  It been some time when I used last time.

The second way is for "new age" Mac's (iBook G3 dual USB or G4) using CD boot.

---

### Post by MacAdmin on 2004-12-28
I founded some links
[http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/)
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=39948](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=39948)
Let me know if you need more help

---

### Post by questionasker on 2005-01-08
thanks for your help.
ill be trying it out shortly.

---

### Post by ixus_123 on 2005-01-12
MacAdmin:  That 2nd link is a link to this forum?

I have the same problem with my new world G3 indigo 366mhz iBook.

It wont boot the CD or for that matter most PPC linux CDs I try.  Gentoo was the only one that will boot but only into basics graphics mode & not much of a gui

I have tried writing the CDs at different speeds but still nothing, it will however boot off a MAc os 9 / X CD with no problems.  

I am buring the CDs correctly as an image not an iso data file on a CD but no joy.  All the CDs I make to boot a x86 PC work with no problems - it's just this mac I can't figure out

I am glad, at least it's not just me.

---

### Post by DirtDawg on 2005-01-12
I was under the impression that g3 imacs were considered "new world". I've been using Ubuntu on my little red g3 for about a month now. It works great and I had no troubles at all with install. Just popped the disc in and it ran.

---

### Post by ixus_123 on 2005-01-14
They are, he's talking a beige one (I think)

My iBook is new world however but doesn't want to boot a linux CD ;[

---

### Post by ixus_123 on 2005-01-14
does anyone know a way around this?  say a disk image on a partition or something?

---

### Post by chascon on 2005-01-15
have you tried to boot holding option down? Then selecting CD to boot off of (select with mouse then hot the arrow key with mouse)?

Yes G3s are "new world" not "new age".  And the biege I believe is still an old world because of some techical thingy, I believe it was because it booted as the old world macs ("rom" issue?).  There are different ways to categorize New world and old world macs too, and I believe I recall experts such as herrenschmidt telling soemthing when  someone others have posted diverging opinions.  But as far as bootloaders, I think everyone is right, you need bootx.   But what they haven't told you'd is that you to make it work you need a with a small OS 9 partition.

Oh and even the bootx isn't really true because there is a third and I believe a fourth somewhere.
Read about one of them at:
[https://www.ubuntulinux.org/support/documentation/howto/installation-powerpc+mac+bootloaders+ppc&hl=en](https://www.ubuntulinux.org/support/documentation/howto/installation-powerpc+mac+bootloaders+ppc&hl=en)
I believe there is a way to circumsribe the OS 9 requirement with another bootloader I've read about but can't recall it.  Yes this stands in the face of normative conventions but I have read ti somewhere.  Google around.

---

### Post by ChiWai on 2005-01-20
I received the CD-ROM from Canonical.  But my iBook (G3/766MHz/384MB) cannot recognize the CD-ROM.  Open firmware cannot boot from the CD-ROM.  Mac OS X 10.3 cannot recognize the disk.   The CD-ROM is totally ignored.

I think burning the CD-ROM from the ISO will have the same effect as stated by ixus_123.

My iBook is New World.  It can run YellowDogLinux perfectly.  I think there is something wrong with the CD-ROM drive or the way the ISO image is prepared.

Maybe I should stick to YellowDogLinux..

---

### Post by haquila on 2005-01-21
[QUOTE=ChiWai]I received the CD-ROM from Canonical.  But my iBook (G3/766MHz/384MB) cannot recognize the CD-ROM.  Open firmware cannot boot from the CD-ROM.  Mac OS X 10.3 cannot recognize the disk.   The CD-ROM is totally ignored.

I think burning the CD-ROM from the ISO will have the same effect as stated by ixus_123.

My iBook is New World.  It can run YellowDogLinux perfectly.  I think there is something wrong with the CD-ROM drive or the way the ISO image is prepared.

Maybe I should stick to YellowDogLinux..[/QUOTE]
 Sorry this might be the stupidest thing but,,,,.

I just installed Ubuntu on a ibook G3 (ver.33.11)
press power-on
immediately press c (for a looooong time)
and then don't touch:)

sorry if you've all tried this.
ak

---

### Post by betterok5 on 2005-02-04
I think the AIO mac he refers to is pre-imac: an education-mostly model built into one case.  If that is the case it falls into the 'old world' category.
kk

---

### Post by AAM on 2005-02-06
[QUOTE=haquila]Sorry this might be the stupidest thing but,,,,.

I just installed Ubuntu on a ibook G3 (ver.33.11)
press power-on
immediately press c (for a looooong time)
and then don't touch:)

sorry if you've all tried this.
ak[/QUOTE]

You can also hold down the Delete-Shift-Option-[squiggle/Mac] keys simultaneously for a long time, just to prove that you as obsessive-compulsively, anally-retentive geek!

---

### Post by ixus_123 on 2005-03-03
I'm still having no luck booting fro CD if anyone can help?

I just downloaded & burnt the Hoary PPC Live CD.  First try it booted & got 27% of the way through the install, then crashed.  I restarted & tried again & it only got 12% of the way.  Now it wont boot off the CD at all useing C or opt

I did think maybe my CD drive has had it but it will boot & install from both the os X discs.  I filled up a CDrom with a movie & that also played all the way through, so the CD seems to be ok.

Right now I am burning another copy but this time at 4x rather than the 24x I just tried.  Fingers crossed

---

### Post by farruinn on 2005-03-04
Hopefully this provides some clarification:

OldWorld: beige, not colorful
NewWorld: colorful (starting with the B&W G3)
However technically it is based on the version of OpenFirmware.

The alternate bootloader (ie. not bootx) is called quik however it doesn't work well on the beige G3 (is known to work on earlier models) and it's not on the install disc so it would be a real pain to use it I think...

For installing Ubuntu on OldWorld macs see the wiki: [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) as well as the BootX page.

About the iBooks not reading the CD... that sounds very odd and I can think of no explanation... sorry  :/

-Nathan

---

### Post by r1kk1 on 2005-04-10
I believe it's the cd iso image that is at fault.

On my g3 ibook, holding down the c key boots the cd fine, plus in os x 10.3 it will mount and show the different files.

I would download a new cd and burn it as an image.

It worked for me.

take care,

eric

p.s. if you pay for shipping, i'll send you the latest kubuntu or ubuntu.

---

### Post by vrejakti on 2005-04-30
The probelm is simple, and specific.

Specific to Blue and White G3's only, perhaps older iBooks. 

The problem: If you do not have an Apple logo/branded CD-ROM or DVD-ROM drive in your Blue and White G3, you will not be able to boot any CD other than an Apple Mac OS Disk.

That's the problem, and if you don't have a Blue and White G3 yourself, you probably can't offer advice to solve this.

For those trying to solve this, it's not your fault in any way, the ISO burns fine, the C key is trying to boot from the CD, it doesn't matter what speed you burn the ISO at, everything is fine. Just if you do not have an Apple CD-ROM drive it will not work.

All the years I've been looking for a solution, I haven't found one other than buying an expensive Apple CD-ROM drive. 

Speculation: Do you need to burn a header file onto the Linux ISO? Anyone reversed engineered an Apple Mac OS CD/DVD to find out what this code is and hacked together a patch? 

I really hope this clears things up for those who can help.

---

### Post by farruinn on 2005-05-01
[QUOTE=vrejakti]
The problem: If you do not have an Apple logo/branded CD-ROM or DVD-ROM drive in your Blue and White G3, you will not be able to boot any CD other than an Apple Mac OS Disk.
[/QUOTE]
 For the record I have a "non Apple branded" cd-rw in my B&W and it boots the Ubuntu install CD just fine.  The manufacturer is LG and the model is "CD-RW CED8080B".  I got it from a Dell PC that was being thrown away.

---

### Post by vrejakti on 2005-05-01
[QUOTE=farruinn]For the record I have a "non Apple branded" cd-rw in my B&W and it boots the Ubuntu install CD just fine.  The manufacturer is LG and the model is "CD-RW CED8080B".  I got it from a Dell PC that was being thrown away.[/QUOTE]

This is good to know. If hardware can be ruled out, perhaps you can help us get closer to the answer. 

Steps I followed, that resulted in not booting the installer were:
[list=1]
[*]Downloaded and burnt ISO to budget quality CD-R at full speed under Windows XP with CD-Burner-XP-Pro
[*]Placed CD in non-Apple-CD-RW drive (which is on IDE Cable 2 / Master)
[*]Started up the computer while holding "C" key (on MacAlly 1999 or 2000 issue keyboard)
[*]Continued holding "C" key while Mac OS X booted
[*]Looked at Mac OS X Desktop which Ubuntu Live CD was mounted on.
[/list] 

Does anything look wrong or different compared to what you did farruinn?

---

### Post by farruinn on 2005-05-01
It may be something specific to the LiveCD then because the Install cd boots fine for me.  If I get a chance I will test the LiveCD this week.  (Does the Install cd boot for you?)

---

### Post by redneckr1 on 2005-05-16
[QUOTE=questionasker]got an old MAC G3 collecting dust. ive heard alot about Ubuntu, so i thought id give it a whirl. saw they had a PPC version, so i thought id use this old comp instead of my regular test comp.
these are the pressed CDs from ShipIt.

its a all-in-one G3, 266Mghz, 32MB RAM, 6Gig HD. i know it can boot from CD-ROM, i just updated to 9.2 with a CD.
also have a regular g3 tower and seperate monitor i might use. i saw something on these forums about wishing for a non-BootX way to install on the beige G3. can someone explain this to me if these two comps arent supported? or tell me what to try to start the Ubuntu install?
thanks for help...[/QUOTE]
well you turn on the machine, insert the cd, and press c on the boot up sequence. skips straight past the os boot. 


thats how i managed to get my g3 tray loading imac to work.

wish you luck

---

### Post by SuperNintendoChalmers on 2005-05-16
How would I go about installing ubuntu on my dreadfully old, circa 98 bondi blue 233 imac? I've read some posts where people talk about difficulty booting ubuntu on a mac from CD. Will I have this problem on this machine?

 However, there is a chance, that my cd-drive on that imac is toast. It is very picky on which cd it reads. Are there any non-cd ways to install umbutu?

---

### Post by redneckr1 on 2005-05-23
[QUOTE=SuperNintendoChalmers]How would I go about installing ubuntu on my dreadfully old, circa 98 bondi blue 233 imac? I've read some posts where people talk about difficulty booting ubuntu on a mac from CD. Will I have this problem on this machine?

 However, there is a chance, that my cd-drive on that imac is toast. It is very picky on which cd it reads. Are there any non-cd ways to install umbutu?[/QUOTE]
 the only way i know of installing on that is using the cd. i to have a blue imac g3 (tray loading), which i know is a bit tempremental when it comes to installing it from a copied cd, i had to try with two installations (because synaptic broke). 

im shure you could  mount it on a cd imaging thing (maybe alcohol 120% or an equivolent)

if not try using a different cd.

---

### Post by zeroreflex on 2005-05-29
[QUOTE=vrejakti]The probelm is simple, and specific.

Specific to Blue and White G3's only, perhaps older iBooks. 
[/QUOTE]

I have also come to realize this.  I have b/w G3 with a non apple CDROM.  I can't get any linux dristros to boot.  This really sucks.  I boot it and i see a white screen for about a second then it goes to the apple startup.  I wanted to go ahead and see what linux was all about, but unfortunately I have yet to be able to boot off any linux cds.

---

### Post by questionasker on 2005-08-12
the 5.04 CD seems to boot more often... either they fixed something or my mac just is in a mood to run linux now... lol

---

### Post by sbworswick on 2007-04-30
i have a beige g3 233mhz it also came with usb and fire wirei believe it was the top of the line at the time  less speed.i thought old world macs did not come with these features.and is it possibe to install it on a new hard drive all by itself and run it that way       thanks sbw

---

