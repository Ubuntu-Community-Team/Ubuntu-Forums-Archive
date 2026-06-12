---
title: "Very green &amp; need network-manager"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Chrimson Scorpion on 2007-06-12
Hi
I am still trying to get to grips with Lilux & have Mandriva 2007 & just got a disk for Linux Mint Bianca.
The former newly installed on my daughters P4 the latter I want to use on an old P3 as a firewall. I also have 2 XP P4's & a lap top (one runs XP Pro!!! - no comments please others XP Home).

Thing is, I need to set up my home network (want to use P3 as firewall linked to network via 3Com switch) and i really have not got a clue where to start.:(

All the forums I have found up to now, with the exception of this one, seem to involve coding, ISO images and so on.:p

Is there an easy way to do this? I am fed up with XP changing IP addresses & resetting my network when XP Pro decides it does not want to play (it hates my 3Com switch!). Am I trying to run before I can walk? I surely do not simply want the click - install inflexibility of XP (or the costs) but my daughter has threatened to buy her own XP install disk if I cannot get this working.

Just as an aside, I use firefox, thunderbird & various other open source installs as microsoft does my head in.

Pleas ehelp or point me to somewhere else that will talk to me in plain non-I-have-been-doing-this-for-years-so-don't-care-if-you-understand-speak

My thanks in advance

P.S. did have a look round but could not find anything I could follow.

---

### Post by KCormier on 2007-06-12
since you're new, I recommend a system like ipcop for your firewall.  That's going to be much easier for you to set up.  As for the other systems, this here is an ubuntu forum (another version of linux).  I'm pretty green with linux but I've tried a few different distros over the last 3 or 4 years and this is by far the best I've tried yet!  I strongly recommend downloading ubuntu and installing that in replace of the other distros.  It includes all the networking tools by default :)  This does involve burning an iso to a disk but this isn't coding at all!  It's just picking the right option when going to burn the disk.  If you're interested we can help walk you through it step by step.

---

### Post by Chrimson Scorpion on 2007-06-14
My apologies for the delay in replying to you but I have had to dig up an old laptop to get online.
I have tried burning linux to dik but it never seems to work. problem is now that this laptop has no CDRW on it  (so old it has an integrated floppy drive). Can the ISO be done via a flash disk?

The Linux Mint is doing my head in. To get on line & set up the network I need to install network files. to install the network files I need to be online. Did no one think of this before creating a disk for complete novices like me?

I would very much appreciate it if you could lead me by the hand. I really want to give linux a fair try and hopefully these problems are just me.

---

### Post by ba_shef on 2007-06-14
Hi,

Since you're in the Ubuntu forms, I will tell you what is available for Ubuntu -- since I'm relatively new to the Linux world myself, I couldn't guarantee that this is true for other verisons of Linux.

Ubuntu is desgined to be installed from a CD; the reason for this (and this is something it shares with all OSs) is that they should not be installed from another OS, because that OS will interfere with what the install wants to do. Instead, they want to load themselves into the computer's memory before anything else can when you switch on the power -- so the CDs specify this behaviour before the OS on the hard drive can get involved, and allow you to change what's on the hard drive for the future if you so desire.

Anyway, Ubuntu cannot be installed from a flash drive -- however, if you download the ISO and store it on the flash drive (it'll need to be a pretty big flash drive, as the installation is about 700mb), you can take this to one of the computers you own with a CD writer and create yourself an Ubuntu installation disk.

What you do with the ISO depends on whether the other computers are running Windows or some version of Linux: either is fine, but the instructions are different. If you post back and let us know, it's very easy to sort out in either case.

B

---

### Post by Chrimson Scorpion on 2007-06-14
Hi :p
I am busy downloading ubuntu 7.04 to my flash now(at 83% as I type)
As suggested I will burn this to disk on another PC.
Trouble is, I have yet to manage to create a bootable disk. not sure why but even following the instructions, cd does not boot.

---

### Post by ba_shef on 2007-06-14
It could be that your computer's BIOS (the thing that runs when you switch on the power and decides what to do) is set to follow the instructions on the hard disk in preference to the CD. When you first switch on the PC, you should see a screen on which there is a message saying something like "Press Del to enter setup" (although the key may be different -- it's usually Del or one of the F keys -- and it might say BIOS setup or something like that). With that screen visible, press the indicated key.

You should be taken to a screen with lots of text options -- this is your BIOS setup. Look for a menu which is called something like "Boot options", "boot preference", "boot order", or something like that. You may have to search through several menus before you find it. What your looking for is a list which has at least "Hard Disk" and "CD-ROM" and possibly contains other options (floppy, USB, depending upon your specific setup). The important thing to to is ensure that the "CD-ROM" gets higher priority than the Hard Disk. When you have accomplished this, save and exit the BIOS. Make sure your Ubuntu CD is in the drive, and that should work.

If it doesn't (and assuming that your boot order is correct; you can test this by trying a different bootable CD, i.e. your old Windows disk), post a link to the instructions you're following, and someone can check that what you're dooing looks OK.

---

### Post by Chrimson Scorpion on 2007-06-14
Hi again
Sorry you misunderstood.
I download the linux as an ISO file (Is this where I am going wrong?), use record now to create a bootable disk & it does not identify the ISO image as s bootable file!!! If I save just as ISO, no boot (I am okay at setting bios to boot from cdrom etc).
I have a feeling this might be the application I am using & am trying another one now. will let you know ASAP if it works.
Must admit, am finding this a little fraustrating & am hoping linux is worht the effort.

---

### Post by Chrimson Scorpion on 2007-06-14
Just to let you know, new cd writer has worked (god I hate XP intallations!!!!!!!!)
Am installing ubunutu now

---

### Post by ba_shef on 2007-06-14
If you're using Windows, use InfraRecorder (it's the program that's recommended when you download Ubuntu). The reason I suggested the other stuff was because it may be that your bootble CD is fine, but your computer is set up in such a way to boot from the hard drive regardles of what's in the CD drive.

---

### Post by Chrimson Scorpion on 2007-06-14
have just successfully created ISO & am busy installing to PC now.
as you suggest, I used InfraRecorder without any problems,
at stage 6 of 7 on the install.
Next thing is to get the network up again.
do you need some details of my set up to assist?

---

### Post by ba_shef on 2007-06-14
As far as your network goes, in my experience Ubuntu is exceptionally good at network detection and so on. Unless you have unusual requirements, you will likely be OK as is.  As for the firewall you wanted to create from your old PC, I would suggest you go with the earlier suggestion of the IPcop distribution of Linux, which is specially customised to do exactly that job and is also very easy to set up.

---

### Post by Chrimson Scorpion on 2007-06-14
Do you know if ubuntu will work with a sagemf@st 800 E3 broadband modem or do I need to download some drivers?

---

### Post by Chrimson Scorpion on 2007-06-15
:frown:
Hello again & thanks for the help so far.
unfortunately I am on the verge of giving up on Linux & maxing my credit card out on Windows licenses.

This is my set up:-
Sagem f@st 800 E3 broadband modem via Tiscali 8mb
Old PIII as internet gateway / firewall (currently with IPCop installed)
3COM 24 port switch all pots enabled & running
1 x storage PC still running Mandriva (Ubuntu keeps failing to install!)
2 x XP home PC's
1 x XP Pro PC
1 x laptop
All connections Cat5e wired, tested & working

This is where I am now.
Unable to access the admin screen via web browser for IPCop
Unable to install Ubuntu on storage PC with Mandriva on it (video kicks out as soon as the 'install' option is selected & fails to return)
Unable to access any internet from any PC (have had to connect laptop direct to modem to get on line)
Unable to connect to any other PC in LAN (Ip's have been set manually and auto - on auto IP, windows PC's lose connetion to LAN)

I have downloaded all install / config files and followed instructions to the letter but still cannot use network in any shape or form.

PLEASE, PLEASE help me get this running.

---

### Post by Chrimson Scorpion on 2007-06-15
Please my time is running out & I need help.
Surely Linux cannot be this difficult for first time users to get to grips with?
Let me know how to get this working.
Cheers:(

---

