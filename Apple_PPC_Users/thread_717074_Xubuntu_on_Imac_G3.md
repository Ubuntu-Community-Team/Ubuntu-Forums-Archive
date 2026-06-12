---
title: "Xubuntu on Imac G3"
date: 2008-03-06
forum: Apple PPC Users
---

### Post by macdumb on 2008-03-06
I'm trying to install xubuntu on my imac g3 333mhz 64mb ram computer.  I know that 64mb is low, and not recommended, but the alternate cd says it should install and run, I don't want to pay to upgrade my ram until I know I'll be able to get Linux up and running.  I am new to linux.
The problem I have is when I download the image file, my macbook pro intel based, running os X says the image file is corrupt.  I burned it anyway, and it booted up and started the install no problem on my Imac, it makes it through some of the setup, and gets stuck at 6% installed and says the files are corrupt, I've tried skipping over the corrupt files, but at least twenty or so files were corrupt in a row.  Any tips on how to get an uncorrupt copy of the alternate install disk?

Thanks.

---

### Post by PaganHippie on 2008-03-07
Throw out the corrupted image file, and download it again.

---

### Post by stream303 on 2008-03-07
Welcome to Linux!  That is an older machine that needs some TLC to get it going, but it can be done - just don't let the following info look too intimidating.  I'm throwing everything at you at once just to get you informed, and many here can help walk you through it.

Sounds like you may have burned at too fast a speed for the iMac, or the download for Power-PC version was corrupt.  Try again, but burn at something ridiculously slow, like 2X speed.  Be sure to burn the "ALTERNATE" ppc image.  It won't be a live-cd, but a direct install disk.

Here is some info on disk burning, although it looks like you got it right, there is a nice link on how to do an md5sum to check that the iso file is correct before you burn:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It is possible that you'll need to upgrade your firmware from an existing mac-os install on a hard drive.  I haven't been able to confirm that this is mandatory for Ubuntu, but I do know you need to do it to run OSX 10.2 +.  If you have your original mac-os install disks, so much the better as there is always some risk.

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

If the hard drive has been upgraded, just be aware that there is an 8gb partition limit, and for most newcomers, the best thing to do is partition it well under 8gb, say at 7 or 7.25 gb.  There are ways to expand this via manual partitioning, but maybe it is best to leave that for later.  If you have the original hard drive, no worries.

I don't know anyone who has run Xubuntu with 64mb ram, but there is an alternative if that doesn't work, especially if you just want to verify that you can get to a an xorg gui screen before spending anything on extra ram.  

I have outlined my experiences with the "old school" way of installing Ubuntu linux, using a server image install, and then adding just enough of X to get you going with simple programs or the commandline:

[http://ubuntuforums.org/showthread.php?t=685324](http://ubuntuforums.org/showthread.php?t=685324)

In either case, we are probably going to have to edit /etc/X11/xorg.conf and change the horizontal freq to 58-62, and the vertical freq to 43-117. In addition, you may have to disable DRI by #commenting it out if the system is unusably sluggish. See [https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

If things are still too slow, we can drop the bit-depth of the graphics down a notch as well.

Fortunately, you can run a simple editor on OSX that is also found in Ubuntu when you fire up the terminal and use the "nano" editor to do this.

It may look like a lot, but once you do it, it won't seem so bad. :)  Look forward to seeing your G3 iMac on-the-air !

---

### Post by Midwest-Linux on 2008-03-07
Replacing the ram need not be expensive. There are two different Ram types for the G3.  SODIMM which is the same type as used in PC  laptops . The Ram is located internally, and the case has to be taken apart. I have done it and it is not easy and not impossible either.

If you have the slotloader type of G3, then the Ram is the common PC 100 SDRAM type and easily replaceable on the bottom of the case of the G3. 

In both cases, Ram for this machine is found on E-bay fairly inexpensive. I highly suggest upgrading your RAM, it will make things run much better in the long run.

Always use the slowest burn setting when burning a ISO disc. Always use the alternate text installer version. Make sure you are using high quality CD blanks. 

 More information on RAM can be found at 

For the older tray loader

[http://www.macworld.com/article/2496/2001/10/howtoimac.html](http://www.macworld.com/article/2496/2001/10/howtoimac.html)


About slot loaders

[http://lowendmac.com/imacs/slot-loading-imacs.html](http://lowendmac.com/imacs/slot-loading-imacs.html)

---

### Post by stream303 on 2008-03-08
A friend of mine is thinking about digging his old G3 iMac out of the garage and letting me have it.  In addition to those very helpful pages, I also found this one which is right up my alley with pictures (!) about how to upgrade almost everything on it:

[http://www.djonmac.com/index.html](http://www.djonmac.com/index.html)

I can't believe I'm getting excited about possibly receiving an older iMac to get Ubuntu on.

---

### Post by 3rdalbum on 2008-03-08
Don't worry about the difficulty of installing new RAM in those iMacs. The top RAM slot is easily accessible. The first time I opened a computer, it was that particular iMac, and in a couple of minutes I'd installed new RAM.

As for your image file problem, DO NOT allow the Mac OS to open or attempt to open the image file. Just burn it like you have been doing. Burn it onto reliable CD-R (i.e. strongly-coloured on the underside) at 8x. Let the disc cool down outside your computer before putting it into your iMac.

You can verify whether the image has transmitted successfully by generating an MD5 checksum of the image file, and comparing it against the checksum from Ubuntu's servers. If they match, you've got a perfect download. I don't use OS X so I don't know how you go about generating an MD5 on OS X unfortunately.

---

### Post by macdumb on 2008-03-08
Thanks everyone for the great tips.  I was just curious, so I downloaded several other linux image files, not intending to run them. I downloaded debian, and unbuntu, and DSL.  OS X tells me they are all corrupt.  

I'm going to try and get a better quality CD, maybe that will help, as it seems half of the disks I have tried won't even boot.  I picked up the computer for free, but I don't have the install disks for OS 9.1 which was on the computer originally.  And I have removed that, because I was planning on only running linux and the install was going so well at the start.

I may try to burn the images from a different computer, one running linux, is there a possibility that OS X is corrupting the image files, or is it a coincidence?  

The ram is something I think I'll just have to upgrade.

I'll try and download and burn the image files off a computer running ubuntu.  Has anyone heard of OS X reading linux image files incorrectly?

---

### Post by stream303 on 2008-03-08
> **macdumb said:**
>  Has anyone heard of OS X reading linux image files incorrectly?

Yes!  Although don't pin me down on where I read about it - it might have been right here.  From memory, I recall there being a bug in early versions of disk-utility where it claims that the file is corrupt when it does the final check, when in fact they are not.  The best bet is to just burn at a low speed, and try it even though disk-utility complains.

I'm going to try and hunt down that reference...

---

### Post by stream303 on 2008-03-08
> **Midwest-Linux said:**
> More information on RAM can be found at 

Nice!  I'm hoping to pick one up soon so this info came just in time.

I'm also wondering about bringing up a 333 to 768 mb!  It appears that it can be done if you update the firmware, get ram that has a CL2 rating, and cross your fingers. :)

I did a quick check on crucial and saw that they offer only 256mb modules with a CL2 rating, but if you have some 512's laying around that are compatible, it might be worth a try...

This got me interested on the lowendmac site

[http://lowendmac.com/imac/guide.html](http://lowendmac.com/imac/guide.html)

.

---

### Post by ppcuser on 2008-03-09
Hello,
I´d like some help to check the hash number for the following file:
xubuntu-7.04-desktop-powerpc.iso

I want to try out this OS on an old imac with 350MHz processor, 256Mb ram, 20Gb HD and OS9.2.2 (looks like a suitable candidate)

1) Tried a search for Ubuntu + hash and found a promising link:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Unfortunately there´s no listing here of "xubuntu-7.04-desktop-powerpc.iso"

2) Tried a search on Google (xubuntu-7.04-desktop-powerpc + hash)
which gives me 1 result: [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

3) Ran winMD5Sum as suggested and compared iso with Google hash above - this gives me a diferent hash number. 

Question: Does this mean that the ISO file is corrupt?

Do i have to download the same file again (about 7-8 hours on a slow internet connection)?

Maybe i shud try downloading a diferent version of (x)ubuntu ?

Advice very much appreciated.
thanks!

---

### Post by stream303 on 2008-03-09
The MD5SUMS file can be found at the top of the directory:

For Xubuntu 7.04, look here:  (The "alternate" install is recommended, burnt at a very low speed for older cd drives)

[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)

It should look like this:
```
f7f9df9e59070bac61c8896ed31705eb *xubuntu-7.04-alternate-ia64.iso
38af519c92f1d18f9f41bba325d482f7 *xubuntu-7.04-alternate-powerpc+ps3.iso
84481b6c081666a1b17a1675ec019116 *xubuntu-7.04-alternate-powerpc.iso
974de7b53fa4da36d6bc80f430e29ca5 *xubuntu-7.04-alternate-sparc.iso
a344b4c45aabadd052c91665c1b3828a *xubuntu-7.04-desktop-powerpc+ps3.iso
c16b9c2eb035ec99fdfc6cfaf9bc0a56 *xubuntu-7.04-desktop-powerpc.iso

```

Here's a easy way to check depending on what machine you are using to do the calculation with:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Looks like the "unofficially supported" distro md5sums only appear in the their own download port directories and not the hash-webpage.

---

### Post by Midwest-Linux on 2008-03-09
> **macdumb said:**
> Thanks everyone for the great tips.  I was just curious, so I downloaded several other linux image files, not intending to run them. I downloaded debian, and unbuntu, and DSL.  OS X tells me they are all corrupt.  


I'll try and download and burn the image files off a computer running ubuntu.  Has anyone heard of OS X reading linux image files incorrectly?

 Just make sure they are the PPC version, preferably the alternate text version.

---

### Post by Phonan on 2008-03-09
Sorry, don't know what's been said before entirely- you may want to try a different server for the image, and btw if it helps I believe the command to do an md5sum on Mac is just "md5." Good luck!

---

