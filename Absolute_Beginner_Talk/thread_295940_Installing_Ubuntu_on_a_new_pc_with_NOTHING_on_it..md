---
title: "Installing Ubuntu on a new pc with NOTHING on it."
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by storybookscribe on 2006-11-08
How do you install Ubuntu on a brand new pc with nothing on it?  I have the disk from *The Official Ubuntu Book*, but when I put it in the pc and boot it from the disk, the screen stays blank.

Do I have to first use the Alternate CD or do some drivers need to be installed first?

---

### Post by lazyart on 2006-11-08
The live CD should be all you need.  What are your hardware specs?

---

### Post by storybookscribe on 2006-11-08
It's an elderly friend of mine's pc.  He just brought it home.

H4104 Computer System
AMD Athlon 64 3000+ Socket AM2 64bit CPU
DVD+RW CD-RW DVD Writer
Seagate 80GB Barracuda 7200.9 SATA II 3 Gb/s
7200RPM 8MB Cache Hard Drive
Kingston 512 MB DDR2 PC4200 533Mhz 240Pin Memory

---

### Post by hscottyh on 2006-11-08
Is the BIOS set to boot from a CD?

---

### Post by xlulux on 2006-11-08
Download the newest version of the live cd from the website here if you can and then burn it to a fresh cd. 

That way you know it isn't the cd's fault.

In case the same thing happens, has Windows been on the harddrive at all?

Does the computer POST?

---

### Post by storybookscribe on 2006-11-08
Yes, the BIOS is set to boot from CD first.  The initial screen pops up with the menu.  I'm choosing the install option, but that's when the screen goes blank.  I can get it to boot and install on my pc just fine.

I burned the AMD Alternate CD but it's not bootable.  Must have burned it wrong and don't have time to burn another one.  Flying to Seattle very early in the morning.  I don't have time for this even, but, it's a friend whose addicted to the internet and...

---

### Post by storybookscribe on 2006-11-08
I have it set to boot from the CD/DVD option.

The Ubuntu menu comes up with the following choices:

Start or Install Ubuntu
Start Ubuntu in Safe Mode
Install in Text Mode
Install in OEM Mode
Install Server
Check CD for Defects
Check Memory
Boot from Hard Disk First

I've been choosing the first option.  It's how it works on my pc.

This pc has never had Windows of any kind on it.  Fresh and clean

---

### Post by Bartender on 2006-11-08
The AMD CD you burned - can you Explore it in Windows?  If it just shows one file you copied the .iso instead of converting it to a bootable CD.  A bootable CD will show 7 or 8 folders and a few files.
EDIT: I think the DVD in the Book is i386.  I think you need the AMD CD but not absolutely sure.

---

### Post by storybookscribe on 2006-11-08
I even tried to hit the F11 Boot Menu at startup.  It gave these options to boot from:

1st Floppy Drive
CD/DVD PM-LITE-ON DVDRW SHW-160  (Which I chose)
SATA: 3M-ST 380811AS
Network: NVIDIA Boot Agent 240.0

In the menu in my previous post.  I even tried choosing "Check CD for Defects" and the screen just goes blank.  But, like I said, I know the disk works because I loaded it on my pc.

---

### Post by storybookscribe on 2006-11-08
I have a disk that came with the CD:

nero

CD KIT CONTAINS:

DOS Driver
Nero Express 6.6, INCD 4,
Nerovision Express 3,
Nero Backitup,
MPEG-2 SVCD/DVD Plug-in
DVD-Rewritable Drive Manual
Acrobat Reader

For DVD-Rewriters Only
OEM Suite

I'll put the CD I burned in my pc and see what I can see on it.  My pc isn't an AMD though.  The disk is.

---

### Post by storybookscribe on 2006-11-08
I put the disk in my pc and tried to view it in Windows.  It has the one .iso file.  My understanding from previous advice is that's how I was supposed to download it.  It's how it automatically downloaded and burned it.  The file name is:

Ubuntu-6.06.1-aternate-amd64.iso

---

### Post by Bartender on 2006-11-08
> **storybookscribe said:**
> I'll put the CD I burned in my pc and see what I can see on it.  My pc isn't an AMD though.  The disk is.

Doesn't matter.  I just want to make sure the .iso got converted to a bootable CD.  It's easy to make a copy of the .iso instead of converting it to a bootable CD.  Many folks have done it.  Including me.  If you see one file you copied the .iso.  That's not what you want.  If you see 7 or 8 folders and a handful of files then the .iso was convered to a bootable CD.  Whether it was burned sucessfully is another issue!  What speed did you burn it at?

---

### Post by storybookscribe on 2006-11-08
All I remember is that it burned in 10 minutes very late one night.  Since that disk isn't usable, and I don't have time to create another one, is there a way to get the one from the book to install?

---

### Post by AAM on 2006-11-08
I don't think you can use the ISO file to install. If you have the original file you need to burn it to a CD as a bootable disc. Its one option in most burning programs. Then you'll be right to go.

AAM

---

### Post by storybookscribe on 2006-11-08
Not using the ISO file.  Using the Live CD from the book.

I'm not going to worry about it right now.  I'm installing Windows XP on his pc until I get back from Seattle and have more time to spend on it.  Thanks!

---

### Post by hscottyh on 2006-11-08
You can try typing "acpi=off" without the quotes as a boot option sometimes that works. But I've never had to do that with an AMD.

---

### Post by gn2 on 2006-11-09
> **storybookscribe said:**
> 

Ubuntu-6.06.1-aternate-amd64.iso

And that 64 could very well be the problem.

Have you tried bog standard 32 bit version?

---

### Post by al1b1 on 2006-11-09
when it goes to the options menu select 'options' which should be either F5 or F6, a input box comes up , scroll to the end and input 'acpi=off' see if it works now

---

