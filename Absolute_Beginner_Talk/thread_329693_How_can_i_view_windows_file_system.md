---
title: "How can i view windows file system?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by cgbcody on 2007-01-02
I want to pull my MP3's off of my Windows File system? Its NTFS, little obvious but just giving more info =] I know that I'll have to convert the MP3's to ogg right? Also, is there a free music converter for this?

---

### Post by aliyanage on 2007-01-02
Hi,

are those mp3 on another windows machine? do you need to get access via remote view or are you on the same network and need to access a windows server?

The ogg part is a bit confusing, for what use do you want to convert it to ogg format?

regards
aliyanage

---

### Post by cgbcody on 2007-01-02
Don't  I need to convert mp3's to OGG before it will play in unbuntu? I'm doing a Dual boot mode.

---

### Post by Sef on 2007-01-02
There is some beta software that can read and write to NTFS.  It is called [ntfs-3g]("http://sourceforge.net/mailarchive/forum.php?forum_id=2697&thread_id=23836054").

---

### Post by aliyanage on 2007-01-02
ah okay, well then just leave it in mp3, there is no such thing that says that you can't play any mp3 on ubuntu :-D

As for exporting your mp3 files from your NTFS part of partition, I never tried or know anything about getting on to the windows partition while being logged in ubuntu. So I would recommend get an external harddrive and just export the whole thing and then copy it again on to your ubuntu or leave it on the external itself :-D

regards
aliyanage

---

### Post by 3rdalbum on 2007-01-02
I know this sounds like a stupid question, but are you trying to just use your files from the NTFS partition, or are you hoping to transfer them from that partition to the Ubuntu one, deleting the originals in the process?

If you don't want to make any changes on the NTFS drive, Ubuntu has built-in support for reading NTFS. Here's how:

1. Go to the terminal and type:

```
sudo fdisk -l
```

2. Something similar to this will appear:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833        5585    35932680    7  HPFS/NTFS
/dev/sda3            5586       10251    35274960   83  Linux
/dev/sda4           10252       10337      650160    5  Extended
/dev/sda5           10252       10337      650128+  82  Linux swap / Solaris

```

3. The command has just shown me what file systems are available on my computer, and what their device file names are. So, my NTFS partition is /dev/sda2.

4. In the terminal window, type:
```
gksudo gedit /etc/fstab
```

5. Type your password when prompted. In the Gedit window that appears, put this in at the bottom (i.e. make a new line for it):

```
/dev/sda2	/media/Windows     ntfs    defaults,nls=utf8,umask=007,gid=46       0       1
```

Those should be tabs, not multiple spaces. Of course, you would change "/dev/sda2" to be whatever you found your NTFS partition to be in Step 2.

6. Save your changes and close the file. In the terminal, type "sudo mkdir /media/Windows".

7. Now you can perform the command "sudo mount -a" to mount your NTFS drive. If you're using Gnome, I recommend a reboot instead.

---

### Post by goodfella on 2007-01-02
If your windows nfts drive is in same computer that linux is installed on then all you have to do is mount the windows ntfs drive and copy over the files using the nautilus file manager i.e. the Places menu on top of your ubuntu desktop.  Mounting ntfs paritions is covered by 3rdalbum's post.  I mount my windows ntfs drive with no problems I just cannot write to the drive which is not neccessary in your case.

Another thing to think of is possibly creating a seperate parition for your mp3's that both windows and linux can access.  I have an ext3 partition on a drive where I keep all my music files.  All you have to do is download a ext3 driver for windows.  If you have a 32 bit windows xp here is one you can use:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

If you have 64 bit windows here is one you can use:
[http://ext2fsd.sourceforge.net/index.htm]("http://ext2fsd.sourceforge.net/index.htm")

Here is a link to the ubuntu wiki that describes mounting windows partitions in linux if you have any more questions.  Hope I was helpfull.
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by Malta paul on 2007-01-02
You can, on a dual boot system, view, access and play your MP3 files using Ubuntu.
You can also use VLC media player which has the codecs to run mp3 formats. This can be down loaded using Applications>Add/remove>search VLC>apply.

The references 'goodfella' gave you should let you access your NTSF partitions, if you have a problem post here again.

Have fun :)

---

### Post by cgbcody on 2007-01-02
Thank you for all of the help guys, but for the life of my i cant figure out hwo to do it wiht VLC, I hope that doesn't sound to noobish lol. Also, I tried doing hte mounting thing and i ended up wiht this 
phatmonkeyslayer@Ubuntu:~$ sudo mount -a
mount: mount point /media/hda2 does not exist

---

### Post by Neural on 2007-01-02
I can provide some input on playing mp3 format in ubuntu from experience.
As a quick fix solution, I did what one other user suggested, which is to use an external drive to copy the files over.
Use the "Add/Remove" feature to select and install "XMMS Player". This player plays the MP3 format by default.
:)
which is good, coz if you also listen to podcasts then the XMMS player is vital..
Thank you,

---

### Post by Duck2006 on 2007-01-02
Once your mounted the windoze drive to ubuntu you don't need to copy them to ubuntu. You can use the files where they are and make a play list and your get to play your mp3's in ubuntu wile they are still on the windoze drive

---

### Post by cgbcody on 2007-01-02
But the problem is i cant figure out how i mount it.

---

### Post by Solver on 2007-01-02
Your problem there was that the /media/hda2 folder doesn't exist. Do
```

sudo mkdir /media/hda2

```

and then try again

```

mount -a

```

---

### Post by Duck2006 on 2007-01-02
This may help

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

this is what i used to mount windoze on my ubuntu drive

---

### Post by paparucino on 2007-01-02
> **Neural said:**
> 
Use the "Add/Remove" feature to select and install "XMMS Player". This player plays the MP3 format by default.

I used xmms for years and it was fabolous, for me,  but now it's no more supported so I decided to use audacious which is a perfect clone and plays all kind of files and uses the same skins as xmms.

---

### Post by Neural on 2007-01-02
> **paparucino said:**
> I used xmms for years and it was fabolous, for me,  but now it's no more supported so I decided to use audacious which is a perfect clone and plays all kind of files and uses the same skins as xmms.

nice!!, thanks for the tip, I shall check it out today :)

---

### Post by goodfella on 2007-01-02
the folder /media/hda2 must exist to mount to it.

---

### Post by 3rdalbum on 2007-01-02
Sorry mate... I forgot to list that last crucial step. Solver's post has it, and I've now updated my post with the right information.

---

### Post by cgbcody on 2007-01-03
Well, not i got this when i do the sudo mount -a command
phatmonkeyslayer@Ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try

---

### Post by Efwis on 2007-01-03
could you please do the following:

in Terminal
```
cd /media
ls

```
and post the output here. 
Also could you please paste your fstab from gedit here.

---

