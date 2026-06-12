---
title: "Advice before installing Feisty Fawn onto desktop"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Depressed Man on 2007-06-11
Helllo hello, you may have noticed me before in here seeking advice on installing Linux onto my laptop (a real install). In the end I decided it wasn't worth messing around and kept my existing and working Wubi installation (only some problems but I'm willing to just let it be worked out over time).

However I have an itch to install Linux on my desktop. Part of that itch comes from previous failed attempts to get into the Linux world and when I would have HDD space, the HDD wouldn't let me install (another story).

I tried Wubi..and it hasn't worked for me.. and I'm getting fed up with how cluttered my XP Pro install is on the desktop is (I have it split so Windows is on one, and program files is on another partition..but some programs decide to be ***es and install themselves into the small C drive space. So I'm going to format the thing (after saving some stuff to my backup drive). Reconslidate the two partitions, then break off 15-20 GBs for a Linux install.

Now, anyway that's my story. Thanks for listening to it. I need advice..I like to be assured that I won't completly bork or erase the stuff I don't want to. I know messing with partitions is a tricky thing (my roomate freshmen year in college accidently wiped out his laptop's windows install with all of his music and stuff on there when he installed Linux on hda0...haha what a great Aerospace engineer..nice guy though).

I have (using Windows terminlogy). Two physical HDDs, both 300 GB. The first one is the currently partitioned one. It's partitioned into a Windows (C), Program Files (D), and Media (E). With my secondary being just F with its glorious close to 300 GBs space. 

I want to leave E and F alone. Not touch them at all. What would they be named if I was installing Linux so I can make sure not to touch them? Is there any way to make sure? I'd be upset if I lost everything on E and F. I only want to work with C and D, combine them into just C while breaking off some space for Linux. (yes that includes formating C..of course). 

So any advice on how to go about this? Install Linux first and then Windows? (I know Windows hates people messing with the MBR it thinks it deserves). Or the other way around? 

Also I kinda went off a crapshoot installing Linux on my laptop (it was more like crossing my finger and hope everything works). I've poked around and looked at some wikis and I'm pretty sure my wireless card will work, my TV card may work or not (if not, that's ok), and so on. But I've read reports about the fans not turning on, or fan speeds being cut down. Is that something to worry about? Because frankly..I'm not going be happy if my desktop starts melting down lol.

---

### Post by floke on 2007-06-11
* You have to put Windows on first else it will overwrite everything else (has to have the whole drive the greedy POS).

* Run live cd and from the terminal type 'sudo fdisk -l' - this will show you all your partitions and their names - make a note of the one you want to install on - probably sda1, 2, 3 etc. - you should be able to recognise it by size etc.

* Live CD (for me) is crap at partitioning - it resizes, then mounts the partition, then chucks an error saying it can't continue since the drive is mounted (wtf?). Best option IMO is to use the alternative install - just make sure you know the name of the partition its going on first...

* Always back up valuable data before partitioning. I've partitioned more times than I care to remember in the past six months alone, and the only time anything has ever gone wrong was with the LiveCD, when I lost Windows for someone following the above mentioned stupidity of the partitioner and had to reformat the entire drive to get it back.

* Good luck ;)

---

### Post by Nythain on 2007-06-11
ok, if what im reading is what im understanding here's my advice.

A. reinstall windows xp first.
during the installation, delete the partitions C and D, but leave the others alone.
create a new partition, not using the maximum available freespace but that minus what you want to save for linux... so say you have a totall of 40 gigs (imaginary numbers) of free unpartitioned space available after deleting the c and d partitions, and you want 15 for linux, then create a 25 gig partition, format it ntfs and continue installing windows operating system on it... leaving the remaining 15gigs free and UNPARTITIONED.

B. after completion of windows install windows should report drives C D and E now... C being the newly created partition, and D and E being your E and F except renamed.

C. start install of ubuntu... when you get to the part asking how you would like to partition you can either let ubuntu automatically partition JUST THE FREE SPACE, or manually set up your partitions (i prefer manual partition, but i have a wee bit o experience in this department)(i would recomend auto FREE for newcomers)

D. make sure you tell it to only format the partitions it has created, should be something like sda4-5 or just sda4 and SWAP... not sure how it will look on your system

E. after your hopefully successfull install of ubuntu it should mount at the ntfs drives in /media (or probably not, who knows, i dont, i manual edit partitions and tell the system where to mount effen everything during the install)

F. install ntfs-3g (i think thats the name of the package, it provides you with ntfs read/write support) and google how to auto mount ntfs drives with write permission using fstab (a similar search on here will return many threads concerning this)

G. next time you reboot you should have a WinXP and an Ubuntu option during the Grub phase of booting to choose from (if you dont edit your /boot/grub/menu.lst you wont have much time, like 3 seconds i believe, to select wich one you want, not sure if grub changes thsi time when it detects an xp option or not)

H. from here hopefully everything works fine

I. i hope i didnt just confuse the living hell out of you

---

### Post by Depressed Man on 2007-06-11
Thank you both of you. Don't worry, I understood the directions. Just need to finish backing up the rest of my files that I want to keep and then let the games begin. :)

---

### Post by steve.horsley on 2007-06-11
I'm with Nythain. Excellent instructions, and saved me a lot of typing.

---

### Post by Depressed Man on 2007-06-11
Argh, windows decided it wanted to be a pain in the ***. After I deleted both the 20 GB Windows install and the 150 GB Program Files partition. I decided I rather just leave it like that (the 20 GB space would be perfect for Linux anyway). But it won't let me install on the 150 GB partition. It keeps saying it's not suitable for Windows XP and to choose another partition. And the only one it seems to work on is the 20 GB one. -_-.

Interestingly here's what Windows' Setup lists..

Unpartitioned Space - 8 MB
Partition 1 [unknown] 5122 MB (5122 MB free) - I was going use this in case I needed to swap files back and forth without risking my NTFS drives.
Unpartitioned space - 144883 MB 
Partition2 (Media) [NTFS] 11544 MB (32569 Free)
Unpartitioned Space 20742 MB

...

Ok why is it listening unpartitioned space three times? I can't delete those three unpartitioned spaces either to consolidate them. Is it because I used a 3rd party partition manager when Windows was still alive?

Edit: Found some answers thru google. Windows isn't considering the 150 GB one active (it considers the 20 GB one the active one) which is why I can only install on the 20 GB one. Most answers involved fdisk or a partition program that makes the other partition the active one. Anyone know how to do it with Linux?

---

### Post by pppetter on 2007-06-11
windows MUST be in the FIRST partition.

Donno why. That's just the way windows wants it :P

---

### Post by Depressed Man on 2007-06-11
It won't install on the first partition. I think I need to make the 150 GB one main active one. But I can't get back to the partition program. So is there anyway to do it? There was a command line way with the recovery console but it looks from the command and from the response of the guy who used it soon after that it erased all of his partitions... which I clearly don't want. >.>

---

### Post by pppetter on 2007-06-11
have you deleted the ~5gb partition then? becouse right know that's the first partition on the disk - and that's the one that windows wants.

---

### Post by Depressed Man on 2007-06-11
It still lets me install to the last option (unpartitioned space 20742 MB) even if it considers Partition 1 [unknown] 5122 MB "C". But if I delete it, it just considers my media partition "C". 

Could it be my MBR?

---

### Post by Depressed Man on 2007-06-11
2I think I've fixed it. Just installed Windows on the 20 GB drive, then installed Partition Magic, made the 150 GB primary and then deleted Windows on the 20 GB one then installed Windows on the 150 GB one.

Well Windows is on the F drive..and there's no C drive but at this point I no longer care..

Got ubuntu working and updating and setting it up now. Once again, thanks everyone!

---

