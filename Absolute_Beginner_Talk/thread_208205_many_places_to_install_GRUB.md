---
title: "many places to install GRUB???"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-03
hello,

i recently got ubuntu installed on a new machine... i specifically chose NOT to install GRUB on the MBR because it kept stuffing up my windows.

anyway... during the installation i chose install on /dev/fd0... now i have only 1 floppy. 

i want grub also to install on my root "/" partition... and i want to duplicate the boot floppy disk. i've be following the instruction below:

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

but to no avail... when i try

setup (fd0) in that HOWTO page i get an error 25...

floppies tend to be perverted in that they stuff up easily... if that happens i will not be able to boot will i? 

one more question was there an option to install GRUB in multiple places? in the linux ROOT as well as floppy during the initial installation??? i must have overlooked something.

thanks

---

### Post by lamego on 2006-07-03
What is the problem on installing it to the MBR ?
You can always select to boot from windows or even set it as your default system.

---

### Post by ProjectGod on 2006-07-03
i've tried a few times... installing into the MBR... it says GRUB error 15 or something or 21 or something... and when i try installing it onto the linux ROOT... the NT loader bypasses everything and loads windows.

---

### Post by molly_001 on 2006-07-03
[quote=ProjectGod]i've tried a few times... installing into the MBR... it says GRUB error 15 or something or 21 or something... and when i try installing it onto the linux ROOT... the NT loader bypasses everything and loads windows.[/quote]  
Since you seem to know a lot about the boot process, probably a better solution for you than GRUB is the GAG Boot Manager (free).  It is truly an impressive piece of software, and will allow you to replace GRUB with a much easier interface.  I encourage you to read more at Herman's site, here:
[http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")
 
Additionally, if this is a Windows Vista dual boot you are attempting (I doubt thought that it is) then you can find a set of instructions for that at my site, commonmancomputing.com
 
Thanks!

---

### Post by ProjectGod on 2006-07-04
thanks for that molly. 

however i have found a way to duplicate my boot floppy... its not a normal straight forward procedure... can't just use the **GUI** or the terminal command **cp** to duplicate this boot floppy... anyway... i'd like to share it with anyone else who is dual booting and has chosen to install GRUB onto a floppy and not the MBR... 

1. whack the GRUB boot floppy (created during installation) into the floppy disk and start up load your linux...

2. log - in as yourself... open up terminal / console

3. **su root** .... enter root password

4. whilst you still have the GRUB boot floppy in your floppy drive... do:

**dd if=/dev/fd0 of=/home/<yourusername>/Desktop/floppy.img**

5. let the command copy all contents of the floppy to the desktop...

6. whack in a [COLOR="Red"]new[/COLOR] blank floppy! format it with the ext2 file system by:

**mke2fs /dev/fd0**

7. copy the image onto the [COLOR="Red"]new[/COLOR] floppy by:

**dd if=/home/<yourusername>/Desktop/floppy.img of=/dev/fd0**

8. after the copy... test it out!... exit out of root... exit out of terminal... shutdown reboot...

have the newly created duplicate on floppy in your floppy drive... and whammy! it works! a duplicate boot disk! if one fails you have this one! if both fail you still have the floppy.img on your desktop? right? haha! :mrgreen:

I actually got this solution from one of the very genorous persons on the #ubuntu IRC they're so helpful it aint funny!

happy hunting!

---

### Post by siccness on 2006-07-04
If it's Error 21, then..

21 : Selected disk does not exist

"This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system."

---

### Post by Apple 101 on 2006-07-04
Another method:

Install GRUB to a floppy disk.
In Windows use *dd* ([DD for Windows]("http://www.chrysocome.net/dd")) from the command prompt to create the GRUB boot file.  Place the file in C:\
Start --> Run --> notepad C:\boot.ini
Add in *C:\<GRUB filename.extension>="Ubuntu Linux 6.06"* under [operating systems] and Save.

That will load Ubuntu from the Windows XP boot loader.

---

### Post by ProjectGod on 2006-07-05
no way! Linux from the good ole NT boot loader??? cool! cheers!!! i'll give it a try!

perhaps i'll start collecting these alternative boot methods and whack it onto wiki.ubuntu.com... cheers for all the help

---

### Post by Thundercat on 2006-07-05
This seems as good a place as any to pose my question:
I have recently re-installed WinXP onto a new drive in my PC. 
Now I have C: = 30GB (NTFS) IDE drive with the MBR etc. on it (where the old windows installation was)
other drives in between...
K: = 500GB (NTFS) SATA with the new windows installation but not any NT loader files.

What I want to do is re-format the C: drive to be my Kubuntu drive, with a few different partitions on it and formatted in ext3.
The question is: If i run the Kubuntu installer and point to the 30Gb drive, will it pick up the Windows XP bits and pieces and give me a dual boot option or will it just wipe them out?

---

### Post by ProjectGod on 2006-07-05
i'm sure someone will supply you with an answer... but as for me i'll do so tomorrow 
as i need my beauty sleep. zzzZZzzZzZZ its 1130 pm!

---

