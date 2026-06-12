---
title: "Need help sharing partitions with XP"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Graybeard on 2006-06-19
I'm migrating from dual-boot XP/Xandros to dual-boot XP/Ubuntu and having trouble accessing the data partition shared by both OSs. I'm ***not*** comfortable with the command-line. 
My previous setup worked well for me and I want to continue it. It consisted of an NTFS partition for XP and WinApps, a FAT32 partition for data, and REISERFS for Xandros.
I now have the original NTFS and FAT32 and EXT3 for Ubuntu. 
I want the FAT32 partition to be available by default when I boot Ubuntu as a user but can only get to  it by changing to root. I'm sure all the tools are right there in front of me but with no confidence in what I'm doing I'm afraid to barge in and try things for fear of screwing up the works. (I've been there and it took days to blunder my way out.) 
Can somebody give me step-by-step instructions that make ***no*** assumptions about my knowing anything? I assume that I need to first give my user account read/write permission on the FAT32 partition and second to set it up to mount by default but don't know how to do either.
BTW, my Ubuntu is a very recent download of Dapper.
Bob

---

### Post by aysiu on 2006-06-19
I know you're not comfortable with the command-line, but you don't have to be--most of the time, copying and pasting commands saves you the trouble of (at least for now) learning the commands and maybe mistakenly typing them incorrectly.

Read this page: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) and post back *any* questions you may have, but please give as much information as possible. I and/or someone else will be more than happy to walk you through the process.

---

### Post by x64Jimbo on 2006-06-19
It's odd that it's not auto-mounting your fat32 partition. That should be default. One thing you should check is if the drive is in your fstab.
cat /etc/fstab should produce a readout that lists what devices are set to mount on boot, and some options about whether they're being mounted as read-only, rw, etc. 
This page in the wiki contains a good deal of information that I think will help you.
[https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

---

### Post by aysiu on 2006-06-19
That *should* be the default--but it isn't, hasn't been ever in Ubuntu.

Ubuntu defaults, since Breezy, to automounting all Windows partitions but in such a way as to allow only root to read them (which is virtually useless).

I don't know why this is. Knoppix has for years had automounting (with correct permissions) of partitions.

---

### Post by x64Jimbo on 2006-06-19
Strange because I don't need root access on my box to change mounted fat32 filesystems. I just installed Dapper 2 weeks ago. Maybe I chowned the partitions to my user while I was sleepwalking or something ;)

---

### Post by Graybeard on 2006-06-19
Many thanks for the prompt advice. Unfortunately the depths of my ignorance are great. I tried my best to follow the referenced instructions, found myself with the terminal window filling the screen and unable to switch to other windows where the instructions were, went back and copied by hand, edited with nano (which has names and shortcuts other than the ones I'm familiar with) and wound up with a message saying I had errors in the fstab file.  From nano it looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /fat32          vfat iocharset=utf8, u mask=000 0 0

Bob

---

### Post by aysiu on 2006-06-19
This would be the error: ```
/dev/hda2 /fat32 vfat iocharset=utf8, u mask=000 0 0
``` It should read: ```
/dev/hda2 /fat32 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by Graybeard on 2006-06-19
Bingo! In fact, the first time I tried to save I had no space between "u" and "mask" and got the error. Realizing I had had trouble determining if spaces existed in some places I added the space there. And, of course as you point out, the problem was an **extra** space.  Now, after rebooting as user, I can access the FAT32 partition.  While I've got somebody's attention, a couple of additional questions. Grub doesn't leave me enough time to make a choice and has choices I don't understand. (My eyesight is poor) Would I be foolish to try to use GAG as my boot manager?  And then, Is there some reason why Ubuntu, unlike Xandros, doesn't center properly on my ViewSonic VP920b monitor? In fact, it not only doesn't center automatically, it's frequently beyond the range of manual adjustment, leaving icons off the edge, etc.
Bob

---

### Post by aysiu on 2006-06-19
You can edit the Grub config file so that it gives you a longer timeout to make a choice.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Very close to the top, you'll see a line that says ```
timeout 5
``` That means you have five seconds to choose an option before the default one boots up. Change that to ```
timeout 15
``` and you'll fifteen seconds.

For your ViewSonic monitor, try this:

Log out.
Press Control-Alt-F1.
Log in.
Type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, just go with the default.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
``` Find the monitor section. There may be two lines there that begin *VertRefresh* and *HorizSync*. If there are, modify them to include these values. If there aren't, add them with these values: ```
HorizSync 24-82
VertRefresh 50-85
``` Where the hell am I getting these numbers? [Here](http://www.viewsonic.com/products/desktopdisplays/lcddisplays/proseries/vp920b/index.htm).
Save out.
Log out.
Press Control-Alt-F7.
Press Control-Alt-Backspace.
Log in again.

---

### Post by Graybeard on 2006-06-19
Not a happy outcome. For reasons that I simply don't understand I wound up with ***neither*** xorg.conf ***or*** xorg.conf_backup resulting in ***no*** output to the monitor and have just now finished reinstalling ubuntu and getting it back to where it was. I would have asked what to do to recover but that's pretty hard with no video:confused:   It would be soooo nice if I could focus on what I'm doing without having to struggle with an unfamiliar editor at the same time. 
Depressed.

---

### Post by aysiu on 2006-06-19
Sorry.

Nano isn't so bad (try Vi for a really confusing editor). I probably should have told you, though, that to save you press Control-X, Y, then Enter.

---

### Post by Graybeard on 2006-06-20
No need to apologize--you're trying to help. Two years ago when I first started with linux and installed Xandros after some experimentation, I learned enough to find my way around on the command line. Then I did the work that ***I*** do, which is ***not*** IT, and forgot it all--that happens when you're closer to 70 than 60. So now I'll try again to fix the video problem, then try to get my backup HDD to hot-swap, and by then I will have encountered other enigmatic problems. :-(

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=Graybeard]Not a happy outcome. For reasons that I simply don't understand I wound up with neither xorg.conf or xorg.conf_backup resulting in no output to the monitor and have just now finished reinstalling ubuntu and getting it back to where it was. I would have asked what to do to recover but that's pretty hard with no video It would be soooo nice if I could focus on what I'm doing without having to struggle with an unfamiliar editor at the same time.
Depressed.[/QUOTE]

I'm the official "King of the Noobs" and have only been using linux for a couple of weeks, but I may be able to offer some small insight (no pun intended for the vision impaired).

aysiu suggested typing this before editing xorg.conf.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```
The point of this was to create a backup in case something went terribly wrong.
It essentially means "copy the file xorg.conf found in /etc/X11/ as xorg.conf_backup in the same directory".
You can then fiddle with xorg.conf and reboot.
If the editing in xorg.conf has undesired results (as it did in your case), you can boot into recovery mode (the second option in GRUB) and at the prompt type...
```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
...which will restore xorg.conf to the state it was in before you edited it.
This will save you having to reinstall because your system is unbootable.

I'm a congenital idiot when it comes to linux and find it essential to make a backup of any important files I intend editing. I know I'll screw it up 5 times before getting it right and have to restore from my backup everytime.

---

### Post by Graybeard on 2006-06-20
Yes, I understood the principle but never thought about how I'd implement it if I ever needed to, and when I did I reached for the biggest stick I could think of.

In any event, the whole exercise seems to have been for naught.  I took a somewhat different approach as follows:
Applications -> System Tools -> Root Terminal
cd /etc/X11
ls
cp xorg.conf xorg.conf_backup
ls (to make sure it worked)
nano xorg.conf
(added the two suggested lines, saved, exited, exited the terminal)
(re-opened the terminal and reopened xorg.conf in nano to make sure the two lines were there--they were)
rebooted
disappointment: Image still off the left even after manually adjusting the monitor as far as it would go to the right.  :confused: 

Some days the only thing I can get right is having another beer.

---

### Post by aysiu on 2006-06-20
You can't just edit the file.

You have to press Control-Alt-Backspace to have the changes take effect.

---

