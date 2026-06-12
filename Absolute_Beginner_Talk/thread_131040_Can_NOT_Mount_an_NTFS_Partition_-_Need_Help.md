---
title: "Can NOT Mount an NTFS Partition - Need Help"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-15
Hello everybody!!!

I have the following problem:

I want to "Mount" an NTFS Partition.

I know that Linux can not Write to an NTFS Partition.

I just want to copy some stuff from it though.

So I launched the "Terminal, typed the command "cat /etc/fstab" & I got this:

root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@ubuntu:/#


The above list shows **ONLY** ONE Hard Drive (a SATA one):

a. The above (SATA) Hard Drive should show TWO more Partitions - one Not Formatted & the other formatted (from a Windows PC) as FAT32.

b. A second (IDE - ATA) Hard Drive should _also_ show on the above list - which is the NTFS Hard Drive I want to get files from.

Why are the above cases "a" & "b" not shown on a "cat /etc/fstab" command?

If "cat" can NOT even see them, how am I supposed to "mount" them?

Please Help...

---

### Post by aysiu on 2006-02-15
See the fourth link of my signature. It explains everything.

---

### Post by Sutekh on 2006-02-15
/etc/fstab does not show the whole story.  

You should have a read of this link, it will run through everthing.

[Mounting Windows Partitions in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by miguelforero on 2006-02-15
In order to see all hard disk, use "fdisk -L" command then use "mount" command to mount a new hd

Example:  my disks

mforero@mforero:~$ sudo fdisk -l
Password:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/hda3            1460        7476    48331552+   5  Extended
/dev/hda5            1460        2067     4883697   83  Linux
/dev/hda6            2068        3040     7815591   83  Linux
/dev/hda7            3041        4256     9767488+   b  W95 FAT32
/dev/hda8            4257        7476    25864618+   b  W95 FAT32

Disk /dev/hdc: 30.0 GB, 30020272640 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hdc2            1276        3648    19061122+   f  W95 Ext'd (LBA)
/dev/hdc5            1276        3648    19061091    c  W95 FAT32 (LBA)
mforero@mforero:~$
mforero@mforero:~$ sudo mount /dev/hda8    /ntfs  <--- whereIWantToMountIt

that's it

PD: sorry by my english, Im from venezuela and don't speak very well english

---

### Post by patrick295767 on 2006-02-15
Hi, 

Before, check this :
```
sudo mkdir /mnt/ntfsshare
sudo mount -t smbfs //pcwinntfsname/share /mnt/ntfsshare -o username=user,password=password
```

If it's not working, there is a problem somewhere ... cable, username, sharing...

Courage !
  
Patrick

---

### Post by dvarsam on 2006-02-15
What about when I "unmount" the NTFS drive?

In the sites you suggested, there is nothing said about what to do to "unmount"...

For Example, after I perform a:

                           "sudo nano /etc/fstab"

And change the line, From:

                           /dev/hda1 /media/hda1 ntfs defaults 0 0

To the following:

                          /dev/hda1 /ntfs_files ntfs nls=utf8,umask=0222 0 0

When I "Unmount", do I have to go back & replace the later line, with the previous line?

---

### Post by aysiu on 2006-02-15
You can unmount it by doing this: ```
sudo umount /media/hda1
``` Why do you want to unmount it?

---

### Post by dvarsam on 2006-02-15
Why should I keep it mounted at all times?

But my question was not that.
My question was whether after I Edit the "/etc/fstab" & make the appropriate changes, whether I should change back to its original format.

At the same time, I realized that the tutorial you suggested was not Good.

Since I do a   "cat /etc/fstab" & the NTFS hard drive is not listed...
Even if I do a "gedit /etc/fstab", it will still NOT get listed...

So, the Tutorial you suggested did NOT Help.

Unless I do a "gedit /etc/fdisk -l" - does such a command exist?

Because using "fdisk -l", shows the following:

root@ubuntu:/# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
/dev/sda5            6080       10011    31583758+   b  W95 FAT32
root@ubuntu:/#


What do I do?

---

### Post by aysiu on 2006-02-15
To explain a bit (as I *wrote* that tutorial).

*df -h* shows what you have mounted and what types they are.
*cat /etc/fstab* shows what you have as to be mounted and with what mount options
*sudo fdisk -l* lists all the partitions and what types they are, regardless of whether they're mounted or not.

If your NTFS drive doesn't appear in your /etc/fstab, you put it in: ```
sudo cp /etc/fstab /etc/fstab_backup
sudo mkdir /windows_ntfs
sudo nano /etc/fstab
``` Add in this line ```
/dev/hdc1 /windows_ntfs ntfs nls=utf8,umask=0222 0 0
``` Save (control-x), confirm (y), and exit (Enter). Then ```
sudo mount -a
``` It's better to just keep it always mounted, as it doesn't reduce performance, and since it's mounted as read-only, you're not in risk of damaging the contents of the NTFS partition. The reason to keep it mounted is that you have to go out of your way to unmount it.

**Edit**: Sorry. You asked whether you need to change the /etc/fstab back: > My question was whether after I Edit the "/etc/fstab" & make the appropriate changes, whether I should change back to its original format. No, you don't. Leave it as is once you've changed it.

I wrote the tutorial the way it is because Breezy defaults to mounting all drives and putting them in the /etc/fstab (of course, they're mounted with "defaults," which doesn't help for Windows partitions). It wouldn't make sense to advise people to **add** a new line, as most people won't have to. It makes more sense to ask people to change the line that already exists, as **most people will already have a line in there with the NTFS partition, just mounted with the wrong options**.

The original option (*defaults*) doesn't mean it's unmounted. It means it's mounted with options that don't really help you (able to be read by only the root user).

The new option (*nls=utf8,umask=0222*) means any user can read the NTFS partition.

Mounting or unmounting is separate from the mounting *options*.

I don't know, frankly, why your NTFS partition isn't in your /etc/fstab. Are you using Hoary, perhaps? Did you do an expert install instead of a regular install?

Let me break down in plain English what the tutorial asks you to do:
1. Find out where your NTFS partition lives.
2. Unmount it.
3. Create a new mount point.
4. Make a backup copy of the /etc/fstab file.
5. Edit the /etc/fstab and change the mount **options** for the previously mounted NTFS partition.
6. Save the changes.
7. Remount it (this time with the proper options).

---

### Post by dvarsam on 2006-02-15
Dear "aysiu",

Thank you for your thorough reply.
I never expected that I would speak to the Author of that specific Internet Address.

I was also surprised with the number of beans you have accumulated!

Bravo!!!

I downloaded the Single CD of Ubuntu 5.10 from Ubuntu's Site.

I would think that this is Breezy (I suppose).
However, I do NOT know the basic differences of all these diff versions I have seen in the Forum so far... like Breezy, Hoary, Kubuntu instead of Ubuntu, and so on... - they seem confusing... (Maybe I will put a post for this).

I do NOT know either, why an NTFS line does NOT show inside my "/etc/fstab" file.

I have understood what I have to do, but I have not yet put it to practice.
I will try what you've suggested & I will write back.

By the way, the ONLY reason why I would want to Unmount, is because I have 4 diff Hard Drives (some with more than 1 partition) & I would NOT want to Boot my Ubuntu with a diff Hard Drive & perform a write command & damage it...

_So my question to you is_:
When I "unmount", should I neutralize that NTFS line with a "##" in front, OR should I delete that line?
OR
I can leave it as is (changed) and NOT "unmount" & there is NO danger in the case that I boot Ubuntu with a diff Hard Drive to DAMAGE it (if I perform a write with wrong options inside the "/etc/fstab" file)?

At the same time, please let me give a few suggestions to your article - if I may:

1. Start with:

     Part 1 – Mounting Window Partitions:

2. When you talk about the "fsudo -l" command, mention what it does:

    The command "sudo fdisk -l", lists ALL Partitions & what Types they are – 
     regardless of whether they are Mounted or NOT.

    Comment:
    I did NOT know what it did - so I really thank you for explaining this to me.

3. Before the "This is what it should look like after we change it:", you should put 
    the following: 

    Note:
    Of course, inside YOUR "/etc/fstab" file, you might probably NOT find a line that 
    recognizes YOUR NTFS Hard Drive. If this is YOUR case, then YOU MUST create 
    a line manually.

    Comment:
    I would have never realized that if I was missing that line, I should have typed it 
    manually. I could understand "correcting it", but NOT in any way I would think to 
    "type it (add it)" by myself! 

4. Right after the changed "/etc/fstab" file, you should put the following:

   Note:
   The new option "nls=utf8,umask=0222" means ANY User can Read the NTFS 
   Partition.

   Comment:
   Here, I did not know why I was to type this - so it would be good to clarify this.

5. When you say: "Then we would Add in a line... .... so that"
     so that the FAT32 Partition is added, you should put a parenthesis in between, 
     and say the following:

    .........a line........ (YOU MUST Manually do this)....... so that...... 

    Comment:
    While reading this, I just passed the word "add", WITHOUT actually realizing that
    I MUST do this by myself MANUALLY.

6. Right after the end of your article, you should write this:

    Part 2 - Unmounting Windows Partitions: 
  
    Now, if you want to Unmount the NTFS Hard Drive:

    Leave the "/etc/fstab" File as is, do NOT remove the (changed) lines for your 
    NTFS or FAT32 Partitions.

    Comment:
    Right before I started suggesting some changes to your article, I asked you a 
    question regarding MY many Hard Drives & whether [U]an attemp to write to 
    them[/U] (if there are the wrong options inserted into the "/etc/fstab" File), [U]could 
    DAMAGE their Partitions[/U].
    If the answer is YES, then you should probably change my last line on the above 
    to the correct one....

Thank you for your time.

Without your valuable help, I would be still struggling on this...

I will be waiting for your response,

Dimitris.

---

### Post by aysiu on 2006-02-15
I think your comments make sense... if I want to make a more verbose version. Honestly, though, you're the first to complain. Most people just want it to work (copy and paste commands). It's only later they want to understand exactly what's going on.

If I decide to make a more thorough version, I'll incorporate your suggestions, and I appreciate you giving them. I would like to keep the brief version as is, though.

I'm still not sure if you fully understand what's going on with /etc/fstab, so I'll try to explain.

First of all, if you mount NTFS the way I described, there's no risk of damaging the drive. It's mounted with read-only privileges--meaning you can **look** at files, but you **can't modify** them.

The /etc/fstab works this way:

When your computer boots up, it checks the /etc/fstab file to see **what** should be mounted (in this case, the partition /dev/hdc1), **where** it should be mounted (the folder /windows_ntfs), and **how** it should be mounted (read-only by all users). At that point, it mounts the partition.

If you decide later on (while using the computer after it boots) to unmount the partition, it won't change the /etc/fstab file. The partition will remain unmounted until you either manually *re-*mount it or reboot your computer again.

If you change your /etc/fstab line, nothing will happen unless you unmount the partition and *re-*mount it again or you reboot your computer.

So once you've changed your /etc/fstab file, there's no reason to modify it again. The partition will mount at boot time. If you want to unmount it during the session, you can ```
sudo umount /windows_ntfs
``` It'll remount again the next time you reboot.

If you don't like it mounting every time at boot time, then don't modify your /etc/fstab at all. Just follow these directions for mounting it manually every time:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by Sutekh on 2006-02-15
> **dvarsam]

I downloaded the Single CD of Ubuntu 5.10 from Ubuntu's Site.

I would think that this is Breezy (I suppose).
However, I do NOT know the basic differences of all these diff versions I have seen in the Forum so far... like Breezy, Hoary, Kubuntu instead of Ubuntu, and so on... - they seem confusing... (Maybe I will put a post for this).[/QUOTE]
**Breezy** refers to the name of the Ubuntu 5.10 release.  **Hoary** refers to the 5.04 release.  In case you are wondering, the release number is found from the date of release.  So Breezy was released in October 2005, thus 5.10.  Hoary was released in April 2005, thus 5.04.

Ubuntu is the basic distribution that uses [GNOME]("http://www.gnome.org/") as its 'Desktop Environment'
Kubuntu uses [KDE]("http://www.kde.org/") as its 'Desktop Environment'

More on Desktop Environments (DE) and other things can be found here [Window Managers for Beginners - by ]("http://ubuntuforums.org/showthread.php?t=87276")[Kyral]("http://ubuntuforums.org/member.php?u=21197")


[QUOTE=dvarsam]
I do NOT know either, why an NTFS line does NOT show inside my "/etc/fstab" file.
[/QUOTE]
/etc/fstab is a file where the mount options are listed.  The basic options, including the Ubuntu filesystem will appear here by default.  If you add more hard drives or create more partitions they *will not* appear there unless you add them.   Thus aysiu's guide.


[QUOTE=dvarsam]
I have understood what I have to do, but I have not yet put it to practice.
I will try what you've suggested & I will write back.

By the way, the ONLY reason why I would want to Unmount, is because I have 4 diff Hard Drives (some with more than 1 partition) & I would NOT want to Boot my Ubuntu with a diff Hard Drive & perform a write command & damage it...[/QUOTE]
If you look agin at the guide, you may have noticed a special flag in the entry for the NTFS mount option
```
umask=0222
```
This option *restricts* access to the partition to **read and execute** only.  

**umask** works by removing permissions from full access. There are three parameters that are represented by a number. Each number corresponds to a level of access said:**
> http://ubuntuforums.org/showpost.php?p=720091&postcount=4[/URL]



[QUOTE=dvarsam]
_So my question to you is_:
When I "unmount", should I neutralize that NTFS line with a "##" in front, OR should I delete that line?
OR
I can leave it as is (changed) and NOT "unmount" & there is NO danger in the case that I boot Ubuntu with a diff Hard Drive to DAMAGE it (if I perform a write with wrong options inside the "/etc/fstab" file)?
If you use the options such as **umask** you can make sure that your partitions are safe from accidental damage.

---

### Post by dvarsam on 2006-02-15
Dear "aysiu",

I added the line you suggested & ALL worked Fine.

Thanks again!

Dimitris

---

### Post by dvarsam on 2006-02-15
Dear "aysiu":

Let me Briefly explain why I would think that the "/etc/fstab" would have a problem with Many diff Hard Drives installed, if I let it "automount" instead of a manual "mount" & "unmount".

As I said before, I have 4 Hard Drives:

1. SATA 80 gig      - 3 partitions:       1 Ubuntu, 1 Unformatted & 1 FAT32 (formatted by Windows) 
2. IDE-ATA 40 gig - 1 partition NTFS
3. SATA 120 gig   - 2 partitions:        1 NTFS & 1 FAT32 (formatted by Windows)
4. SATA 80 gig     - 1 partition NTFS

Now, lets say, my "fstab" is the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1    (My above disk "1")
/dev/sda2          (Linux)
/dev/sda3          (W95 Ext 'd LBA)                                                                  (Partition 2)
/dev/sda5          (W95 FAT32)                                                                         (Partition 3 - FAT32)
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


If I inserted to Ubuntu, My above disk "2", the following line should be added to "fstab":

/dev/hdc1       /ntfs_files     ntfs    nls=utf8,umask=0222  0  0              (My above disk "2")


Now, if I inserted to Ubuntu, instead of My above disk "2", the above disk "3", the following lines should be added to the "fstab":

/dev/hdc1     /ntfs_files       ntfs   nls=utf8,umask=0222  0  0              (My above disk "3")
/dev/hdc2    /fat32_files      vfat   iocharset=utf8,umask=000  0 0     (Partition 2 - FAT32)


Now, suppose the above 2 lines were added by me _permanently_ in the "fstab" file.

Lets say I was then booting the Ubuntu & in some way, my "hdc1" was recognized during the Boot process (by Ubuntu) as FAT32 (which would be in direct CONFLICT with my lines entered in my "fstab" file). In some way, I would be forcing Ubuntu to see it as NTFS...

At the same time, my "hdc2" would be recognized during the Boot process (by Ubuntu) as NTFS (which would again be in direct CONFLICT with my lines entered in my "fstab" file). I would again be forcing Ubuntu to see it as FAT32...

**OR**

For some reason in the Future, by mistake I Format a Hard Disk instead of:

First NTFS & Second FAT32

I Format it:

First FAT32 & Second NTFS


Based on the fact that (according to my "fstab" file), I am forcing Ubuntu to see the Partitions in reversed manner:

If I performed a simple copy & paste, I would be copying a File to an NTFS Partition (thinking that it is a FAT32 one) & I would end up Damaging my NTFS Partition & probably Loosing ALL my Valuable Files....

I hope you got my point.

That is why I am very skeptical about NOT to "unmount" my Partitions & letting Ubuntu  "automount"...

...and since I have many Hard Drivers, If in some time I had 3 Hard Drives connected to Ubuntu (at the same time), an "/etc/fstab" file set in "automount" mode, could cause serious damage to ALL my Hard Drives in the scenario that it recognizes in reverse NTFS & FAT32 Partitions...

_Now my question is_:

Is that a possible scenario?

Is it possible, with an automated "mounting" procedure to end up in a F*ck*p situation?

Cause if it is possible, I prefer to "mount" & "unmount" at all times (I can bear a little self-torture scenario), than to "automount" (& end up loosing it ALL...).

Thanks for your Time,

Waiting for your response.

Dimitris.

---

### Post by Sutekh on 2006-02-15
I think the answer to your question is try it.

Try using the manual **mount** command to mount your FAT32 partition, but use the **ntfs** flag.  
```
sudo mount /dev/hdc2 /fat32_files ntfs nls=utf8,umask=0222 0 0
```
It won't let you do it.  You will get an error about 'wrong filesystem' and the partition won't be mounted.


- In case you think I'm trying to make you a guinea pig, you don't have to try this.  I just did this on my system

---

### Post by aysiu on 2006-02-15
When you say "insert," are you talking about physically opening your computer box up and physically placing a hard drive in and setting it in place with screwdrivers?

See, I never remove my hard drive and replace it with other hard drives. I just leave it in there.

If you're in a situation where you're constantly switching around hardware, then, yes, it's probably better for you to manually mount partitions instead of putting them in your /etc/fstab.

---

### Post by sd2000 on 2006-02-16
Is there a way to use WINE to load up Windows Explorer to view and change or at least retrieve copies of files and save back to the to the linux partition without having to mount and unmount drives?


                                                  Sd2000

---

### Post by aysiu on 2006-02-16
[QUOTE=sd2000]Is there a way to use WINE to load up Windows Explorer to view and change or at least retrieve copies of files and save back to the to the linux partition without having to mount and unmount drives?


                                                  Sd2000[/QUOTE] Believe it or not, it's a lot simpler to type **one** command to mount the NTFS drive and then find the files you want to retrieve than to install Wine and Explorer (I don't even know if this can be done, anyway). Besides, installing Wine and Explorer wouldn't give you access to the other drive, anyway... you need to **mount** the drive in order to access it.

---

### Post by dvarsam on 2006-02-16
[QUOTE=aysiu]When you say "insert," are you talking about physically opening your computer box up and physically placing a hard drive in and setting it in place with screwdrivers?

See, I never remove my hard drive and replace it with other hard drives. I just leave it in there.

If you're in a situation where you're constantly switching around hardware, then, yes, it's probably better for you to manually mount partitions instead of putting them in your /etc/fstab.[/QUOTE]

Answer:
Well, I have bought an enclosure of a Hard Drive (a rack).
That enclosure is put in a 5,25 inch place & then there a little box / enclosure than you put in your 3,5 inch hard drive.

That enclosure has a handle, which works like this:

If you do NOT want you PC to Boot (& include) using that Hard Drive - "pull it" out before you Boot.

If you DO want your PC to Boot (& include) using that Hard Drive - "push it" in before you Boot.


If I did NOT have "a Rack", I would then have to physically open the PC box with a screwdriver, which would be a pain .....
..... instead, I have bought this Rack & I "push in" & "pull out" my Hard Drives according to my needs...

At the same time, the advantage of having a SATA Hard Drive, is that you do NOT have to shutdown & restart to "Add" it - just "plug-in" & "plug-out" according to your needs.

Note:
At least that is what Windows does - I hope Ubuntu does that too!!!


Now, let us say you have a Hacker sneaking into your computer....

If you have ALL your important & Personal Stuff put in a Hard Drive that is NOT plugged-in in your PC, then YOU answer to me what is he going to hack?

He is going to "Hack" the "None Filename" which exists in the "No Hard Drive" in my PC?

OR 

He is goint to "Hack" a "Known Filename" (which you can find from the "Recently used Documents"), which exists in a "No Hard Drive" (because the Hard Drive" is not plugged-in in my PC? 

Now, listen to what I have read in a Newspaper Articles in my Country - its Politics oriented:

You know the recent war in Iraq....

I read in this Newspaper Article, that if you wanted to find the truth about the Iraq war, you could visit internet sites such as "al jazeera", etc. , etc.

You would even find "ugly" pictures from casualties of war....

Now these pictures are pictures that SOME people do NOT want YOU & ME to see!

So, by looking into these sites (for either fun or curiosity), you end up getting an Email from some Country's Intelligence saying to you that you are NOT supposed to DO that...

At the SAME time, ".... that COULD possibly Harm Your "Hard Drive!" - if you know what I mean....

.... so, conclusion: I like my Files in My Computer & I am NOT willing to risk loosing them...

     I hope you like yours too!!!

So, my advice to YOU, is keep away from these Internet Sites & do NOT try to visit them, if you want your computer FILES to be SAFE....

And according to that Newspaper Article, there is some Guy in the Web that posted an article about Intelligence ERASING his Hard Drives, warning messages he got from them, and other stuff....

So, all I am saying is:

Just try to keep YOUR files safe, in ANY way YOU think is Better...

And by the way:

The way things are Right now:

 YOU could NOT Backup let' say 50 Gigs of YOUR files into DVD's!
...cause it is Too much of a Hassle... too many Disks:

- How will you know which disk contains what? &
- How often are YOU willing to do that, to keep your Backups Up-to-Date?
- Etc, etc...

So, we are basically ALL unsafe on this - unless Bigger Media (Like "Blue Ray" comes in the Market)...

I hope I answered your questions.

An advice from Me to You:

"Curiosity killed the Cat!".

Have Fun!!!

---

### Post by Tamacracker on 2006-09-09
OMG I Love you!! That's the site I went to a couple months ago to learn how to properly mount my NTFS HDD and it all went smoothly. But I reformatted last night... and I've been searchin the whole day for this damn webpage!! I'm sendin myself an email with this link lol

---

