---
title: "Need help with Elive install"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-12-17
I'm trying (but failing miserably) to install (stable) Elive 1.0 onto a machnine.  Installer claims that "It's EASY!" to the contraty notwithstanding, the installer LIES!

Note that this is being posted on the Beginners' board.

I don't happen to know how to repartition a HD, so offering me 3 options for doing so in language that's foreign to me doesn't help.

Sad to say I've been 'spoiled' by lead-you-by-your-nose, click, click, click approaches.

Anyone know of an Elive installation tutorial that's written for those of us who are Linux-impared?

---

### Post by CouchMaster on 2007-12-17
Elive is easy - so lets back up a little.
What did you have on the HD before?  If it was linux just tell it to use the existing partitions.
What language are you talking about?
Have you gone to the Elive site and looked around?
I think it uses GParted graphical partition editor so you might want to GOOGLE "How to use gparted"
And you will really like it once it's installed.

---

### Post by bodhi.zazen on 2007-12-17
I think Elive uses gparted for partitioning.

Installing is otherwise similar to most any distro these days.

Not sure where you are, but see if these links help :

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by jimmj43 on 2007-12-17
[COLOR="Red"]Thanks for the quick responses.

Here's an example from one of the help links provided that contribute to my throbbing headache:

> Linux numbers Logical partitions starting with 5: The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be hda1
The entire extended partition (and any logical partition(s) it contains) would be hda2.
The logical partition within the extended partition would be hda5.

Clear as mud ?
[/COLOR]
Naming of partitions.

Windows: Windows uses lettering (c:\ ; e:\ , etc).

Linux: Linux uses /dev/hdxy or /dev/sdxy (see below).

x will be a letter starting with a, then b,c,....
y will be a number starting with 1, then 2,3,....

Thus hda1 = First partition on the master HD.

[COLOR="Red"]GRUB[/COLOR].
Grub numbers drives starting with 0.
Grub also names partitions starting with 0.
Thus grub (hd0,0) = Linux hda1 or sda1 (depending on if you have ATA, SATA, or SCSI drives).

I use grubs as bait for freshwater panfish.

I suppose I should backtrack.

I've weaned myself of the evil MS bonds now for nearly a year. Got an Edgy CD from Ubuntu that refused to install. Waited a couple of weeks for Feisty to become available and tried that - which worked! And I'd probably still be using it except that updates developed a nasty habit of wrecking the update installer, and subsequently, the OS. Stepped up to Gutsy. Right outta the chute, updates and the update installer fell into battle, with the installer and the OS  scored as losers on a TKO.That Macromedia trotted out a new version that didn't play well with the resident repository installer is a whole 'nother story.

I have test driven a number of Linux distros including Sabayon, Mint, Puppy, DSL, TinyMe and Elive. Alas, I have to use what I've got, which is 2 older machines, both with limited resources. I use 1 on a daily basis to get online and the other as a testbed to the future and BEYOND..............!!! 

Everyday machine:

eMachine
566MHzCPU
256M RAM
6.5G HD

Testbed machine:
CompaQ Presario
900MHz CPU
384M RAM
30G HD

Both machines are equipped with CD R/W drives

My goal is to get the CompaQ running, dual-boot, with 2 separate HDs - one exclusively for Elive and the other exclusively for W98se.

Did I mention I own 3 Lexmark printers that have been relegated to doorstops? Hence the apron string to W98se.

I was attracted to Elive at first for its 'Look'. E17 is some pretty neat eye candy. But it also arrives, out-of-the-box with multimedia pre-installed. <--Less drudge work for me.
Also, Elive - just running from the CD drive, performs FASTER than the HD-installed Gutsy.

Sidenote: On this, my 4th clean install of Gutsy, I've had to pull the power cord in order to reboot more in less than 3 weeks than I every did after running w2KPro for 3+ years.
Nope. ZERO Firefox extensions added. Nope. ZERO upgrades downloaded. Bare bones.And still the distro sucks the life outta my RAM. That isn't where I wanna go.

Hence: Elive.It appears that it simply delivers more bang for the buck (so to speak).

Would it help if I listed my pros/cons sorta Jeffersonlike?

Multimedia - including Flash, WMV, MPG, Quicktime, Real, DivX, Etc..
Audio - whatever. I'm not a music nut.
Images - GIMP is probably over my head, but I'll try to muddle my way through. I have yet to learn if Gimp will allow me to D/L & manipulate images from my 2 (cheapie) digital cams. 
Simple text notes - gedit seems suitable
Chat - Doesn't Gaim pretty much rule the roost?
Email - I learned a long time ago to use web-based clients.
Games - I don't waste my time that way.
Web developer, coding and suchlike? You gotta ASK?!?!

---

### Post by jimmj43 on 2007-12-17
Rats!

The only part of the 1st 8 lines that I wanted to have highlighted in red was: "Clear as mud?"

Did I mention that I'm posting on the 'Beginners Board'?

---

### Post by macogw on 2007-12-17
> Linux numbers Logical partitions starting with 5: The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be hda1
The entire extended partition (and any logical partition(s) it contains) would be hda2.
The logical partition within the extended partition would be hda5.
Perfectly clear to Linux geeks.  To people who don't know about partitions...yeah...mud.

OK so first thing's first.  A hard drive can have only 4 main partitions.  It can be less.  You could have 4 primary partitions.  You could have 1.  You can also have 3 primary and 1 extended partition.  

Extended partitions are a neat trick that lets you have more than 4 partitions because they can hold logical partitions.  Logical partitions can only be found inside extended partitions.  So, if you wanted 5 partitions, you'd make 3 primary then make an extended partition to hold 2 more (extended partitions cannot be used by themselves).  

Get it?

As far as the numbering goes, logical partitions always start counting at 5 so that 1, 2, 3, and 4 can be reserved for primary & extended partitions.  So, you might have /dev/sda1 (primary) followed by /dev/sda2 (extended) which contains /dev/sda5 (logical) and /dev/sda6 (logical).  I know it seems silly to partition like that, but consider that someone may have had 3 primary followed by 1 extended that contained 2 logical (as in the previous paragraph) but then deleted the primary partitions and made one big partition where it was but didn't want to change the extended partition because it had a bunch of stuff they didn't want to lose.

If you have 2 physical drives, the first will be named /dev/sda and the 2nd will be /dev/sdb (follow the pattern of letters).  There would be a /dev/sda1 and a /dev/sdb1.  The numbers can repeat as long as they are on different physical disks.

I hope that helps.

EDIT: diagram attached

---

### Post by CouchMaster on 2007-12-17
As long as you're giving yourself headaches download and install the new Elive 1.2.3 unstable - it's realllllly cool.

---

### Post by jimmj43 on 2007-12-18
Couchmaster, you *******!!! You own stock in Excedrin, dont'cha?? #-o

---

