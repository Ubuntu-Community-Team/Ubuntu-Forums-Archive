---
title: "Can't read DVD's"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Smashed_187 on 2007-04-19
I seem to be having issues reading DVD's.

After having to reinstall windows for the 8th time in a few weeks I decided to go to Ubuntu, and just in time for the 7.04 release :-)

Unfortunately, when I insert a DVD into the DVD drive, instead of letting me access it, the CD/DVD R/W drive disappears from the file browser page! I can handle basic linux functions, and installing from terminal and what not isn't too daunting, but when it comes to hardware, I tend to break down.

If anyone can be of help to me, it would be greatly appreciated.

Oh, and also, my Radeon 9250 doesn't seem to be able to use 1600 x 1280 under Ubuntu, where it could under windows...any quick solutions for that?

Many Thanks. 

Ben.

---

### Post by pppetter on 2007-04-19
Hi there!

I can't help you with your dvd drive...

But...Have you installed the binary driver for your graphics card?
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

If not, then do so. If you have, then I would say; go ahead and [look here]("https://help.ubuntu.com/community/FixVideoResolutionHowto"). My tip is that you look into the first option([Run the Autodetect Script Again]("https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29#head-c7979448ab81077f16349d3ca4be7aa5a5a52de2")) and maybe [ATI - Refresh Rate & Resolution QuickFix]("https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29#head-42bafbcee7a10ed50f2d9016555557b9874be252"), Becouse Radeon is ATI, right?

---

### Post by Smashed_187 on 2007-04-19
I have looked around, but no one has any suggestions or links to a Feisty repository. Yeah, I know, it was released earlier today and I'm asking a bit too much for someone to have already written up a how-to.

Anywho, does anyone know the Feisty repository for the fglrx drivers?

Thanks, 

Ben.

Edit - And WOW at the fast response time! Thanks very much pppeter!

---

### Post by Smashed_187 on 2007-04-19
As much as this goes against the grain of every other forum I've been a member of: Bump.

---

### Post by halitech on 2007-04-19
> **Smashed_187 said:**
> I have looked around, but no one has any suggestions or links to a Feisty repository. Yeah, I know, it was released earlier today and I'm asking a bit too much for someone to have already written up a how-to.

Anywho, does anyone know the Feisty repository for the fglrx drivers?

Thanks, 

Ben.

Edit - And WOW at the fast response time! Thanks very much pppeter!

never mind, realised you were looking for a fiesty how to on ATI stuff, not finding the fiesty download :(

---

### Post by Smashed_187 on 2007-04-19
I'm sure I can install them, so long as someone knows a repository I can get them from.

Thanks anywho,

Ben.:)

---

### Post by houstonbofh on 2007-04-19
There is no new Feisty method.  The old Edgy method of getting binary video drivers works fine.

You need the basic dvd stuff.  You should add Medibuntu.
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```
Now you need all the dvd stuff...  If you have the Universe and Multiverse,
```

sudo apt-get install libdvdread3 libdvdcss2 ogle-mmx ogle-gui

```

Try that and get back to us.

---

### Post by Smashed_187 on 2007-04-19
Sorry, I wasn't clear enough.

What I meant was that it seems when I insert ANY CD/DVD my DVD RW drive is unmounted and not remounted.

Of course, that's just guessing, seeing as I have next to no practical linux experience.

But I did try that and it said all are the newest version, thanks for the suggestion!

---

### Post by Smashed_187 on 2007-04-19
If this helps at all, when I insert the original Ubuntu 7.04 disc that I used to install, I receive the error:

"Unable to mount the volume 'Ubuntu 7.04 i386'."

And when I click the Details tab I get: 

"mount: Not a directory"

Frustration! What is going on here? I have fixed my ATI driver issue, I've fixed everything except this one thing! I don't have a windows partition anymore, so I'm really hanging for a solution here.

Cheers guys, 

Ben.

---

### Post by Smashed_187 on 2007-04-19
It's past 1am here, so I'm going to hit the sack, but I thought I'd wrap this all up with a brief over view of what's still wrong, plus some bits and pieces that I've figured out since then. Well, to be fair, they're just more error messages :-(

Upon inserting the majority of DVD's and CD's into the drive, the drive seems to dissapear from the "Computer" section of Ubuntu.

On the odd occasion that it actually reads (About 1 in 10 disc's, also one's that haven't previously been read before will be read if you open and close the tray enough) the disc, when I attempt to copy or play any media file off it, I'm presented with this error: "Error "I/O error" while copying "/media/My D... Party.zip"."

I haven't successfully copied a single file since I used the Live CD to do an Install of Ubuntu onto the hard drive. There must be people out there who have experienced these issues, any help or insight is really appreciated.

Thanks.

Edit: Even more errors now! Here's one: 

"Unable to mount the volume "NEW""

Details:

"mount:block device dev/scd0/ is write protected.  mounting read-only mount: Not a directory"

And I don't even get read only access. Which is a stupid thing to say, because all CD's or DVD's are read only :-S I'm terminally confused here.

---

### Post by beatman on 2007-04-19
Hi there Re the instruction 
sudo apt-get install libdvdread3 libdvdcss2 ogle-mmx ogle-gui 

I receive the following information:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Can anyone help me det my DVDs to run... they worked fin in the earlier version, with Automatix.

Many thanks in advance

---

### Post by houstonbofh on 2007-04-19
libdvdcss2 is in the medibuntu repository.  Without adding it, you will not find it.

To the OP, can the cd player read?  Boot a live cd, and test read the cd media.  If that works, what drive and motherboard?

---

### Post by Smashed_187 on 2007-04-19
Yes, it can. I burnt all the backup discs from XP, and they play happily in my xbox so there's nothing wrong with the burn. And I installed from the live CD, so it can certainly read it fine.

The drive is a LiteOn CD-RW/DVD±RW Drive, but for some reason in the properties it's saying it's a SCSI drive? I know that's not true, it's IDE, on the 2nd bus.

The mobo is an Asus PSS800 - VM

---

### Post by Smashed_187 on 2007-04-19
More headway, I tried to manually mount the drive in terminal and I received this error:

mount: block device /dev/dvd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/dvd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I know this will occur with a blank disc, but brand new DVD Movies, DVD-ISO and DVD-UDF discs can't read, as long as any kind of Data/Audio CD.

---

### Post by Smashed_187 on 2007-04-19
Frustration Bump

---

### Post by houstonbofh on 2007-04-19
That is not the Asus Commando (or similar) is it?  A lot of SATA and an odd J(something) IDE interface?  I have a friend with that system, and it is a real serious bug in Linux.  What version of Ubuntu, and installed when?

---

### Post by Smashed_187 on 2007-04-20
This is an older board, not that I know too much about chipset's and IDE channels, they may be similar.

I'm using Feisty 7.04 and I downloaded it yesterday on release, so I'm not using the Beta.

[Asus Commando]("http://www.asus.com/products4.aspx?l1=3&l2=11&l3=307&model=1480&modelmenu=1") Motherboard specs.

[P5S800-VM]("http://www.klondike.ru/spec/MotherBoards/ASUSTeK/Socket775/P5S800_VM.htm")

I don't THINK they're that similar, but I may be wrong.

Edit - I just read your post again, and it's just an IDE channel. I'm at work right now, but would swapping the channel from secondary master to primary slave be of any use? :-S So no SATA or anything along those lines.

---

### Post by Smashed_187 on 2007-04-20
Bump?

---

### Post by houstonbofh on 2007-04-22
I am stumped.  Can you swap out a different DVD player and see?  Can you boot a Live-CD and access data on the CD?

---

