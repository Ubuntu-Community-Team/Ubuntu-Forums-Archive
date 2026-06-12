---
title: "Triple-boot scenario"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by AlecWest on 2007-04-28
Shortly, I'll be buying a new desktop from a builder ... specifying that all components have drivers that will work in a Win98SE, WinXP, and Linux environment.  The system will have 2 hard drives.  One will be formatted NTFS and left blank, to be used for video capture and editing.  The 2nd hard drive will be partitioned three ways - Win98SE on one partition, WinXP Home on another partition, and Ubuntu on the third partition.

I'm assuming I'd have to install one OS first ... then carve out the other partitions.  Question is, which OS should I install first?  I currently run a Win98SE/XP dual boot system.  And at the time I set it up, I was advised to set up Win98SE first.  Is this still good advice given the triple-boot system I envision ... or would it be better to install Ubuntu first?

I have no experience with Ubuntu.  But I'm somewhat tech-savvy ... and friends tell me I'll pick things up in no time.  Eventually, my goal (if I can find, or write for myself, the appropriate software) is to distance myself from Microsoft as much as possible.  And if the community here is as friendly and helpful as I've heard, I suspect that my goal can be achieved.

Thanks in advance to all who reply.

---

### Post by Nythain on 2007-04-28
98, then xp, then ubuntu... ubuntu's grub works well with other os's... microsofts boot loader doesnt play well with others, and will overwrite, remove or overall jack up grub from what i hear

---

### Post by AlecWest on 2007-04-28
Thanks.  I've heard that about XP's boot-loader.  I guess this is one of those times when it's actually advantageous to have Win98SE (or older).

BTW, for others who will try what I'm going to try, let me pass on a tip.

My current system only has 256MB RAM.  My new system will have 2GB RAM.  It has been said that Win98SE will not work (or be problematic) on systems with more than 512MB RAM.  This is absolutely not true ... as long as the following fix is implemented.

As soon as 98SE is installed on a system with more than 512MB RAM, use a boot disk to get into the WINDOWS directory.  You'll see a file named SYSTEM.INI which is textual in nature.  Open the file with EDIT and you'll notice this control heading with nothing underneath it:

[vcache]

The first thing you must do is add a value underneath this heading, basically to instruct Win98SE to "ignore" any RAM above 512MB.  This is what the heading/instruction should look like:

[vcache]
MaxFileCache=524288

Reboot (without the boot disk) and the problem is solved.

---

### Post by Nythain on 2007-04-28
nifty tip... so why are you sticking with 98 anyways??? xp has an option to run .exe's emulating 98 mode... usefull bit i discovered when trying to get older games to run on my friends xp machine

---

### Post by AlecWest on 2007-04-28
> **Nythain said:**
> nifty tip... so why are you sticking with 98 anyways??? xp has an option to run .exe's emulating 98 mode... usefull bit i discovered when trying to get older games to run on my friends xp machine
Lessee, where to I begin (grin).  First, the ONLY reason I upgraded to XP was because I wanted  to escape the 4GB limitation on filesize inherent in FAT32 systems.  This is because I got a DVD burner, editing tools, and a capture card.  With DVDs being 4.7GB in size, FAT32 won't cut it.  If there had been a "third" edition of Win98 that recognized NTFS, I'd never have upgraded to XP.

However, there are certain older utilities I still use in a 98SE environment whose drivers simply do not function in an XP environment.  That's the primary reason why I keep 98SE around ... though I also appreciate the fact that Win98SE itself (and programs under Win98SE) tend not to "phone home."  Not that I'm doing anything illegal, but I've always been a bit paranoid of programs/OSs that "phone home" - always wondering just what info about my system they're sharing.  I like to be in "control" of the info I share about my computer ... and XP (and now Vista, to which I'll never upgrade) has taken away a lot of that control.

Ultimately, if I can do all the things I want to do in a Linux environment (Ubuntu and possibly other distros), I'd like to abandon ALL Microsoft OS environments altogether ... even if I have to go so far as to write my own software (which I used to do years ago).  We'll see what happens...

---

### Post by rickggreen on 2007-04-28
I did the same thing as you until I tried vmWare, I had a number of progs, that would not run under XP, so I had SE on my machine until I switched to Linux. Since I had originally built this machine for Vista and directX 10, and while waiting for it to be delivered I tried Ubuntu, Mr Bill is not going to get anymore of my money.

---

### Post by Nythain on 2007-04-28
oh man, then you are gonna love linux once you get the hang of it... just stick with it, try and ditch the the microsoft mentality, have a willingness to learn, and ask as many questions as it takes and you will be ditching windows in no time... or at least just emulating or virtualmachining it for what you need it to do that linux cant...

---

### Post by louieb on 2007-04-28
> **AlecWest said:**
> 
I'm assuming I'd have to install one OS first ... then carve out the other partitions. 
You'll find it much easier to get the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and carve out you partitions  before installing anything. Don't worry about what file system to format them in you just let the installer reformat them anyway. Don't know how much space you planed to give Linux.  But put that space in an extended partition  and carve it up into 3 or 4 logical partitions. (I use 4). One for the / (root) base install 10 gig is plenty. One for swap 1 -2 gig is plenty. One for /home (user configuration and data files) or you can use the /home for user files and use a forth for data files.

---

### Post by AlecWest on 2007-04-28
> **louieb said:**
> You'll find it much easier to get the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and carve out you partitions  before installing anything. Don't worry about what file system to format them in you just let the installer reformat them anyway. Don't know how much space you planed to give Linux.  But put that space in an extended partition  and carve it up into 3 or 4 logical partitions. (I use 4). One for the / (root) base install 10 gig is plenty. One for swap 1 -2 gig is plenty. One for /home (user configuration and data files) or you can use the /home for user files and use a forth for data files.
All excellent advice (from everyone).  Thanks.

Insofar as space is concerned, I'm currently giving 98SE 20GB and XP 20GB on a 40GB hard drive.  And, I've never run out of space within those confines.  Even so,  my next hard drive will be apx. 160GB ... with 30GB for 98SE, 30GB for XP, and 100GB for Ubuntu and possibly other distros.  In short, the lion's share of space will be designated for my "sandbox" to play in, hehe.

Right off the bat, I know that 50% of my needs will be met by Linux immediately --- since I spend 50% of my computer time either writing (OpenOffice), browsing, or reading/sending email.  The next 25% of my computer time is spent doing video and/or audio work.  Then the last 25% of my computer time is spent using a variety of small utilities to do this and that.  So basically, I'll start using Linux for a lot of what I do right away  ... then start "tweeking" with the other stuff until I find a way to make the software work or find a straight-Linux alternative to what I currently use.  And, I look forward to a day when I can format those remaining Windows partitions (grin).

---

### Post by AlecWest on 2007-04-30
> **louieb said:**
> You'll find it much easier to get the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and carve out you partitions  before installing anything.
One more question.  I know that with Windows XP, a SATA drive will go unrecognized unless a SATA driver is installed from a floppy during the installation process.  Is this also true with GParted?

---

### Post by louieb on 2007-04-30
> **AlecWest said:**
> .., Windows XP, a SATA drive will go unrecognized unless a SATA driver ...  Is this also true with GParted?
GParted live CD found my SATA drive, no problem.

---

### Post by Nythain on 2007-04-30
yeah, from what i've read gparted has no probs with sata drives really... another bonus of linux... recently updated software = better support for newer hardware...

---

### Post by Najand on 2007-04-30
GNU parted and parted magic can deal SATA hard disks without any problem.

---

