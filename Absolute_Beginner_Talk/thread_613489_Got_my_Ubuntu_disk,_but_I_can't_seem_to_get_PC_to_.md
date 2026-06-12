---
title: "Got my Ubuntu disk, but I can't seem to get PC to boot from it.  Help?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by reubs on 2007-11-15
I got the live CD today in the mail, and I can't find any documentation on how to actually boot from it so that I can see if it is something I'd like to keep on our desktop.  

Anyone have any links or any ideas what I need to do?

Thanks in advance.

---

### Post by mikewhatever on 2007-11-15
Try this [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
You may also find the following handy [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by Scheater5 on 2007-11-15
You need to set your CD drive to be the "primary boot device" - that is, the first thing your computer looks for when booting.  When you first turn on your computer you're probably greeted with the logo of the manufacturer - the BIOS screen.  At the BIOS screen you're probably given some options, most likely involving F keys (F1, F2, etc).  Pressing one of these will get you into a menu where you can change the boot options to make the CD drive the primary device.  If you have trouble doing this, let us know more of what you see and we'll be better able to help you out.

---

### Post by reubs on 2007-11-15
Thanks for the info.  I can occasionally beat Windows to booting and get to the BIOS screen, and I get a few options.  Whenever I highlight the option to boot from CD-ROM IDE device I get the Windows start-up screen.

I haven't tried booting to my Intel Macbook, but I'm hoping that my problem isn't the boot CD.

Thanks for any help.

---

### Post by oilchangeguy on 2007-11-15
> **reubs said:**
> Thanks for the info.  I can occasionally beat Windows to booting and get to the BIOS screen, and I get a few options.  Whenever I highlight the option to boot from CD-ROM IDE device I get the Windows start-up screen.

I haven't tried booting to my Intel Macbook, but I'm hoping that my problem isn't the boot CD.

Thanks for any help.

you've got to save the option, before you exit the bios. after you select your boot option press F10, you'll be asked to confirm you want to save your changes. select yes, the computer will reboot. make sure the cd is already in the cd drive.

---

### Post by mike555 on 2007-11-15
if you try booting the live CD on a Macbook, you need to hold down the " Option " button on the keyboard while booting till it gives you the option to boot from the CD ........

---

### Post by GavinZac on 2007-11-15
it sounds to me like you're expecting the computer to ask you to insert the boot cd, it wont, itll just skip to the next boot option. make sure its in the drive, then reboot

---

### Post by reubs on 2007-11-15
Okay, here's what's happening:

I have the Boot CD inserted into the CD-ROM.
I shut down Windows XP.
I power on the tower, and I hit F2.
I go to the boot menu, and I put a check only next to CD-ROM IDE device.
I save the settings.
I shut down the tower.
I power the tower back on.
I get a message saying, "To retry boot hit F1.  To enter setup hit F2".
I eject the CD and put it in the DVD drive, and I hit F.  I get the same message.

I'm about at wit's end here.  Any help would be appreciated.

---

### Post by seachnasaigh on 2007-11-15
If you boot into Redmond XP, then insert the cd, then use WinExplorer to look at the contents of the CD itself, what do you get?
If the CD itself is corrupted or has something wrong in its fs, you should be able to see that there.
That's a pretty good sanity check for the integrity of the CD.

Sounds also like you've got two optical drives ... try booting from the other? One of them is primary, one is secondary would seem to me. In your BIOS it should identify which is which.

ckr

---

### Post by reubs on 2007-11-15
I've tried both optical drives, and the CD came straight from the mail.  I'll check the other stuff later.  Thanks, though, for the info.

Edit to add:  I verified the CD using my Macbook, and it was free from corruption.  I'm tired of wrestling with it tonight on the PC.  I'll look at it again tomorrow.

---

### Post by seachnasaigh on 2007-11-17
Did you get it to boot your Macbook (holding down the option key whilst booting)?

Typically ambios and phoenixbios, the most common out there for intel chipsets, prompt you after the POST screen (the automatic hardware checks the computer does whilst booting) to "press any key to boot from the CD" ... if you don't press a key, the BIOS chooses the next device in line or goes to the screen you describe, asking you to press F1 or F2.  Could that be the issue?

Something that hasn't been asked: what are the hardware specs on your machine? 

When booting, are you presented (very briefly) with an option to hit F12 to open a one-time boot menu?
If so, that will allow you to select the optical drive to boot from once.

Have you tried booting the computer from another CD? Your recovery CD perhaps? Just to verify that the problem is in the BIOS setup and not in the CD itself. Narrow down your list of potential problems first.

Let us know.

ckr

---

### Post by jaybombalous on 2007-11-17
so when u change the option to always make it boot the cd first does that option stay selected in the bios after u power off and power back on?

Sounds to me like a hardware or firmware problem, honestly. Maybe do a firmware update as a last resort. Beware that updating firmware can potentially destroy the machine permanently.

---

### Post by seachnasaigh on 2007-11-17
> so when u change the option to always make it boot the cd first does that option stay selected in the bios after u power off and power back on?

Yes. IF you saved your changes prior to exiting the BIOS.

ckr

---

### Post by reubs on 2007-11-17
I haven't tried booting from the CD on my Macbook.  I only put it in to see what would happen, and from there I verified the disc.

The PC I'm trying to boot from is a standard Dell Dimension 4600 with 2.80 Ghz Pentium 4 and 512 megs of RAM.  I'm trying out Ubuntu 7.10 on it to see if I want to bother with upgrading the RAM at all.

I haven't tried booting from a recovery disc, but I am pretty sure the drives themselves work because I can read CDs in each of them.  I'll try some of the other suggestions when I have some time later on.

Thanks again to everyone for helping out a newb who wants to learn some new stuff!

---

### Post by mike555 on 2007-11-17
You might try another "live " CD , like Puppy Linux , it's very small download ......... also you might try burning the CD from a different computer to a .ISO file , slowly ...... or using a different burning program ...

---

### Post by Flying caveman on 2007-11-17
I just want to add that a boot menu is not the BIOS, and some BIOS are difficult, on some you may have selected boot from CD/DVD but it still tries to boot from the hard drive unless you disable it.  I remember having to disable all the other boot options except the CD/DVD to get it to boot.  $.02

---

### Post by seachnasaigh on 2007-11-17
> The PC I'm trying to boot from is a standard Dell Dimension 4600 with 2.80 Ghz Pentium 4 and 512 megs of RAM. I'm trying out Ubuntu 7.10 on it to see if I want to bother with upgrading the RAM at all.

That's a pretty standard consumer-grade Dell. It should offer you the F12 option for a one-time boot (yes, that's not an edit to the BIOS). Its behaviour at boot time, prompting you to hit a key to boot from the CD, should follow what I suggested above. 

I wasn't asking about another boot CD to verify the drives so much as the ability of the computer to boot from the optical drive(s). I'd try the F12 key boot menu first; if that doesn't work, ensure that boot from the CD is enabled from the BIOS and then watch the POST screen carefully for the CD prompt. 

Good luck!

ckr

---

### Post by reubs on 2007-11-30
Hey everyone.

I stepped away from trying to install this for a few days just to kind of start fresh, and I'm still having a heck of a time with it.  I wouldn't think it's the live CD because it's one that I registered for and had sent to me.  

However, when I look at it in "My Computer" on the XP I see all kind of files and no indication that there is a single ISO file on there.  Instead, there are a number of folders and various other files.

I just launched the CD w/in Windows and got the "Ubuntu {disc tree)".

Finally, the DVD-ROM drive will not read the disc inside of XP, but the CD-ROM will read it fine.

Thanks again for the help and guidance.

---

### Post by BrendanM on 2007-11-30
Yeah, you're not going to see a single .iso file on the disk. A .iso file is an archive format that contains a lot of files (a whole operating system, in this case). When people talk about burning an iso, they actually mean burning all the files contained in the iso to the disk.

In any case, since you ordered a professional CD from Cannonical, I really doubt the problem is the disc itself. It sounds like you've got a bit of a stubborn bios. To reiterate (and possibly clarify) suggestions others have given, I think you should try the following, in this order:

1) With the Ubuntu CD in the CD-ROM drive (you said the DVD-ROM wouldn't read it, yes?) At startup press F12 to get to a one-time boot menu, and select "Boot from CD-ROM device" or whatever.

2) Try disabling all other boot options in the BIOS. Don't just move them lower on the list, actually uncheck/disable them.

3) As a last resort, you could check Dell's website to see if there's a BIOS update available for your machine. Be aware that flashing the BIOS comes with a small (but non-zero) risk of permanently wrecking your computer.

---

### Post by reubs on 2007-11-30
I've done everything suggested, and I'm wondering I should just flash the BIOS.  My question, though, is about it permanently frying my system.  Does that mean the system I currently have and I'll have to replace a few components, or does that mean that the whole tower and everything will have to be tossed?

If the latter, I'm not sure it's even worth the risk to try it out...

---

### Post by seachnasaigh on 2007-12-02
Hmmmm. Your DVD-ROM won't read the disk (*odd, but OK let's come back to that in a moment*) ... and going into the BIOS to disable all start options except the optical drive results in not booting from the CD-ROM you got? Have I got that right?

If so, I guess before you go muckering with your BIOS, I'd want to ask: what is your physical disk arrangement on your machine? If your CD-ROM drive will read the disk, but won't boot it, that might lead me to suspect that your primary optical drive is the DVD-ROM and the CD-ROM is a slave to it. 

Lots of questions arise when you get into the physical makeup of your machine ... are all of your drives IDE, or are some SCSI or SATA? Which are your optical drives? Most modern BIOS's are set up to read "cable select" for IDE devices, rather than the older "master/slave" paradigm, but it is still possible to set your drives up that way on an IDE chain. 

First off, I'd boot the machine and pop into your BIOS with F2 as it's booting, and then see how the BIOS itself reads the drives. I suspect from a standard Dell-built Dimension PC that your hard drive(s) are on IDE channel 1, and your optical on IDE channel 2 (a poor design unless you're going to do IDE RAID, but nevermind all that) and that your CD-ROM is a secondary on that channel. It could also be that your hard drive is primary on channel 1, your CD-ROM is a secondary on that channel, and that your DVD-ROM is a primary on channel 2. IF all that is the case, then to boot from the CD-ROM drive you'd need to have it as a primary on either channel; when you select "boot from CD" on the one-time boot menu, or from selections in the BIOS, you're really telling it to boot from the primary optical drive. 

That information in hand, you'd need to crack the case, unplug all but your CD-ROM drive, make sure it's plugged into the primary cable position (they're normally labelled) on either channel, and then restart the PC and see what happens. <caveat>Be sure to unplug the machine and wait 30 seconds before touching anything, there is some risk of electrical shock working inside your PC</caveat>.

Essentially what we're doing here is ruling out the physical layer in troubleshooting your problem. Once that's done, you can move on to looking at the revision on your BIOS. Dimensions are Dell's basic home PC; they're probably rarely tinkered with by the end-user after being set up at the factory, and Dell makes some assumptions about those end-users that may not include booting to a non-installed OS. That may be the root of this problem. 

I'm still curious as to why the DVD-ROM doesn't read the disk at all ... that's not normal behaviour for any optical drive. Does the DVD-ROM read other CD's? Is it one of the older DVD-R drives or one of the newer +/-R drives? The idea that it won't read the contents of the disk at all is disturbing.

Let us know!

ckr

---

### Post by jdb2 on 2008-01-10
This is a known problem with Dell Dimension 4600i series boxes. I was fixing someone's computer and needed to boot off of a Kanotix LiveCD and encountered the exact same problem. The problem is that the Dell will only boot from an ATAPI drive that is a *master* . To boot off of the CD-ROM drive do this :

  1. Reboot and get into the BIOS setup.
  2. Select "Drive Configuration"
  3. Select "Secondary Master Drive"
  4. Select "Drive Type"
  5. Change it from "AUTO" to "OFF"
  6. Get back to the main BIOS menu and select "Boot Sequence"
  7. Move "1. IDE CD-ROM Device" up to the top and then de-select all the other devices
  8. Put your CD into the CD-ROM drive and reboot.

Should work now. :)

jdb2

---

### Post by reubs on 2008-01-21
> **jdb2 said:**
> This is a known problem with Dell Dimension 4600i series boxes. I was fixing someone's computer and needed to boot off of a Kanotix LiveCD and encountered the exact same problem. The problem is that the Dell will only boot from an ATAPI drive that is a *master* . To boot off of the CD-ROM drive do this :

  1. Reboot and get into the BIOS setup.
  2. Select "Drive Configuration"
  3. Select "Secondary Master Drive"
  4. Select "Drive Type"
  5. Change it from "AUTO" to "OFF"
  6. Get back to the main BIOS menu and select "Boot Sequence"
  7. Move "1. IDE CD-ROM Device" up to the top and then de-select all the other devices
  8. Put your CD into the CD-ROM drive and reboot.

Should work now. :)

jdb2

Well, I got to the initial boot screen from there, and now I'm going to see if I can get inside and play around with Ubuntu from there.  Thanks so much to everyone for your help in getting to this point.  I hope it's all worthwhile!

---

### Post by reubs on 2008-01-21
Thanks to everyone, I'm now posting this from the CD running from the CD ROM on our Dell Tower.  Something that is strange, though, is that while running windows I can't get an internet connection, whereas with 7.10 an internet connection is no problem.  I'm wondering if there is a bug in my set-up that has disabled the ethernet port.

Anyway, I'm probably going to find a way to install this on this tower now and get all of the necessary files tucked away for safe keeping.

Thanks again to everyone for your help!

---

