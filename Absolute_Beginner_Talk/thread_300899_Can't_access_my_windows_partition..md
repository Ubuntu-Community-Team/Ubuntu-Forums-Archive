---
title: "Can't access my windows partition."
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Noobster on 2006-11-16
I have a dual boot system with Ubuntu and Windows.  Yesterday my Windows partition got a virus and I can't boot to it now.  I have 2 or 3 files I need to get off the windows partition, but going through the steps to mount my windows partition doesn't work.  

I've edited the fstab file as needed and then go to terminal and type:

"sudo mount -a" and get the following

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I edited the fstab for NTFS which is what I have, so I'm not sure why I'm getting this.  Somebody please help me.

---

### Post by dillbertdabomb on 2006-11-16
you can't edit windows partitions with ubuntu, you'll destroy windows completely, you should just reinstall it....

---

### Post by podunk on 2006-11-16
It would be helpful if you posted your fstab file here so folks can look it over. Also the results of
sudo fdisk -l

Also - enter 
dmesg | tail

and see what kind of error you get.

---

### Post by Noobster on 2006-11-16
I don't need to edit it and it's already going to have to be reinstalled.  I just need to access the windows partition so I can copy 2 or 3 files over and then I'll reinstall windows.  I make/sell abstract digital art and I have a couple that I did yesterday and got the virus before burning them to CD.  I really don't want to lose the 2 pictures I did yesterday.

---

### Post by Noobster on 2006-11-16
Here's my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /windows ntfs nls=utf8,unmask=0222 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by podunk on 2006-11-16
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by taurus on 2006-11-16
What are the output of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```
Otherwise, read this then.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2006-11-16
> **Noobster said:**
> Here's my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /windows ntfs nls=utf8,unmask=0222 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
It should be umask, not u**[SIZE="4"]n[/SIZE]**mask...

---

### Post by Noobster on 2006-11-16
sudo fdisk -l gives the following:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1355    10243768+   7  HPFS/NTFS
/dev/hda2            1356        7751    48353729    f  W95 Ext'd (LBA)
/dev/hda5            1356        2710    10243768+   e  W95 FAT16 (LBA)
/dev/hda6            2711        7751    38109928+  83  Linux

Man this forum is fast....I can't keep up :)

---

### Post by taurus on 2006-11-16
> **Noobster said:**
> sudo fdisk -l gives the following:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1355    10243768+   7  HPFS/NTFS
/dev/hda2            1356        7751    48353729    f  W95 Ext'd (LBA)
/dev/hda5            1356        2710    10243768+   e  W95 FAT16 (LBA)
/dev/hda6            2711        7751    38109928+  83  Linux

Man this forum is fast....I can't keep up :)

You just have a typo in your /etc/fstab for /dev/hda1...  ;)

---

### Post by Noobster on 2006-11-16
> **taurus said:**
> It should be umask, not u**[SIZE="4"]n[/SIZE]**mask...


Oh.....I think that might be the problem.  I changed that and now when I typed "sudo mount -a" it just went back to prompt.

When I click the drive though it just doesn't open....do I need to reboot before I can access the partition?

---

### Post by podunk on 2006-11-16
I'm using Dapper, and my xp is mounted so:
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

note that in your fstab you have 
unmask
instead of 
umask

also - I'm not sure but I think the value 222 is wrong also?

As a last resort - if you change that last 0 (zero) to a 1 your Ubuntu will very likely run a disk check on it - which maybe good or bad. :-)

---

### Post by taurus on 2006-11-16
No need to reboot!  What is the output of this command then?

```
df -h
```
You should see your /dev/hda1 in /windows...

---

### Post by Noobster on 2006-11-16
This is what I get.  Looks right from what you said it should be.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              36G  6.3G   28G  19% /
varrun                249M   84K  248M   1% /var/run
varlock               249M  4.0K  249M   1% /var/lock
udev                  249M  136K  248M   1% /dev
devshm                249M     0  249M   0% /dev/shm
lrm                   249M   19M  230M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             9.8G  7.4G  2.5G  76% /Windows

---

### Post by taurus on 2006-11-16
> **Noobster said:**
> This is what I get.  Looks right from what you said it should be.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              36G  6.3G   28G  19% /
varrun                249M   84K  248M   1% /var/run
varlock               249M  4.0K  249M   1% /var/lock
udev                  249M  136K  248M   1% /dev
devshm                249M     0  249M   0% /dev/shm
lrm                   249M   19M  230M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             9.8G  7.4G  2.5G  76% /Windows
So your Windows partition is mounted on /Windows!  Now, just browse to that mountpoint and move/copy whatever you want to get off of that drive...

---

### Post by Noobster on 2006-11-16
Except when I try to access it, it's saying

The folder could not be displayed.

Sorry, couldn't display all the contents of "Windows".

---

### Post by Noobster on 2006-11-16
I've got this sick feeling like my windows partition is corrupt and I might be SOL.

---

### Post by taurus on 2006-11-16
What happens when you run this command from a terminal?

```
sudo ls -la /Windows
```

---

### Post by Noobster on 2006-11-16
I get this:

ls: reading directory /Windows: Input/output error
total 0

---

### Post by taurus on 2006-11-16
You might be right about your Windows is so sick that it wouldn't even let you access it in Ubuntu!!!  ](*,)   Didn't you have antivirus running on your XP?

---

### Post by Noobster on 2006-11-16
Yeah.  I was running up-to-date AVG and also etrust.  I got it from another forum I'm on.  The forum got infected and infected anybody that went to the website.  I had about 5 seconds after visiting the forum before my computer was shut down by the virus.   Would I be safe to go to that website under Ubuntu?

Edit:  DO NOT click that link if you are running windows.....actually I'm deleting that just in case.

---

### Post by Gaweph on 2006-11-16
Look on the bright side, at least your stuck with ubuntu, and not the other way around :) 

Seriously, i would suggest trying GNOPPIX, it is a very good live distro specifically for these things, it should automount your ntfs and linux drives, so you should be able to move whatever you wanna save to your linux drives.  Worth a Shot!

Also, you would definatelly be safe going to that website.  When using ubuntu, you are using the strict linux user system.  For example, even if you got a linux virus, it would have to ask you for root password in order to do anything in the root user level (this is the beauty of linux)

---

### Post by podunk on 2006-11-16
The partimage rescue CD can work wonders.

Also -  several folks have had good  luck with this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Noobster on 2006-11-16
Well photoshop is one of the main reasons I still used XP.  I've had some issues with GIMP not releasing memory (or so it seems) which has kept me in XP.  I have other programs for work that need windows but I just connect to one of our Terminal Servers through ubuntu for that.  I'm thinking about forgetting about sucky Windows after this deal.  I just need to search out a solution for my GIMP problems (that sounds so personal).

---

### Post by Noobster on 2006-11-16
> **podunk said:**
> The partimage rescue CD can work wonders.

Also -  several folks have had good  luck with this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I'll give that a shot.  I appreciate all the help from everybody.  This has to be one of the most useful forums I've been on.

---

### Post by Noobster on 2006-11-16
> **podunk said:**
> The partimage rescue CD can work wonders.

Also -  several folks have had good  luck with this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This may be a stupid question but, which version should I use.  I'm trying to access a Windows XP partition, but need to do it from Linux.  Should I download the Linux version or Windows version.

---

### Post by Noobster on 2006-11-16
Nevermind.....figured it out.

---

### Post by taurus on 2006-11-16
> **Noobster said:**
> Well photoshop is one of the main reasons I still used XP.  I've had some issues with GIMP not releasing memory (or so it seems) which has kept me in XP.  I have other programs for work that need windows but I just connect to one of our Terminal Servers through ubuntu for that.  I'm thinking about forgetting about sucky Windows after this deal.  I just need to search out a solution for my GIMP problems (that sounds so personal).
If you need to use Photoshop, try installing it with wine or CrossOver Office.  I know CrossOver Office works with Photoshop 7 although I have seen some threads here that some people got Photoshop 8 to run with wine!

---

### Post by Noobster on 2006-11-16
> **taurus said:**
> If you need to use Photoshop, try installing it with wine or CrossOver Office.  I know CrossOver Office works with Photoshop 7 although I have seen some threads here that some people got Photoshop 8 to run with wine!

I've tried installing photoshop with wine but it wouldn't work.  I've had nothing but headaches with wine, but still trying to sort it out.  It seems like it never does what it's suppossed to.  I also tried to get my Palm Desktop through wine with no luck.  I've never heard of Crossover Office.  I'll have to look into that. Of course I'm running version 8 so that might not work.  It seems like it takes me forever to get something done in Ubuntu, but when it works, it works great.

---

### Post by randyleepublic on 2006-11-16
Just curious.

Why does what appears to be a perfectly good gui based config tool: Disk Manager, basically not work at all??   I have to say this: Linux is not an operating system - it is an operations program and that's it.  If you ever want "System" status for Linux it needs to work systematically.  Hello?

To drill down: I go to disk manager and set access to a partition as "disabled".  IT SHOULD EFFING STAY DISABLED!!!  But it doesn't.  Nope, you have to edit your fstab file if you want that.  So what is the effing point of diskmangyer?  Huh?  Don't effing bother with a gui if you are not going to  make it functional.  You just get people's hopes up.  It's cruel.  

I mean what is the deal.  Is it that the people who made disk manager are stupid?  Or what?  I mean really, what is the gd deal?   It's not just disk manager.  All the gui tools are brain dead one way or another.  I really think that the guys who do the development are code monkeys who are so stuck on the command line that they deliberately hate on us who prefer a graphical interface by sabotaging their work.  Seriously what is the deal?

Can somebody please help me to understand.  Please.  I have to use booboontu at work and it is driving me nuts.  If I hurt anybody's feelings  I apologize, but I am really getting desparate here.

Love, 

Randy

---

### Post by annda on 2006-11-16
> Hello? [...]
IT SHOULD **EFFING** STAY [...]
So what is the **effing** point of diskmangyer?  **Huh?**  Don't **effing** bother [...]

I mean what is the deal.  Is it that the people who made disk manager are **stupid?**  Or what?  I mean really, what is the **gd** deal? [...] All the gui tools are **brain dead** [...] the guys who do the development are **code monkeys** [...]


sorry, Randy, read your post again. do you seriously think people will want to / feel comfortable answering to that?

---

### Post by eppoh on 2006-11-16
> **Noobster said:**
> Yeah.  I was running up-to-date AVG and also etrust.  I got it from another forum I'm on.  The forum got infected and infected anybody that went to the website.  I had about 5 seconds after visiting the forum before my computer was shut down by the virus.   Would I be safe to go to that website under Ubuntu?

Edit:  DO NOT click that link if you are running windows.....actually I'm deleting that just in case.


Try the KNoppix live CD. It's like it was made for rescuing Windoze

---

