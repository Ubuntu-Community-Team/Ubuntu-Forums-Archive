---
title: "Cant boot XP after Ubuntu install"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-20
I want to make this clear, first of all.

I HAVE UBUNTU AND WINDOWS XP INSTALLED ON MY COMPUTER.
I am able to boot into ubuntu(this is not my current problem), however, I am unable to boot XP.

I have the GRUB menu. I CAN SEE UBUNTU AND XP.  
When I choose to boot XP, i get the black screen with options (start normal, safe mode with command line. etc.) 
I have tried all of the above options and it still gives me the same error for all of the options.
***********
A problem has been detected amd Windows has been shutdown to prevent damage to your computer.
Check for viruses , remove any newly installed hard drives or hard drive controllers. Check hard drive to make sure it is properly configured and terminated.
Technical information:
***Stop: 0x0000007B

************
My specs:
Computer: Dell Optiplex GX60
Processor: Intel Celeron 1.70GHz
Memory: 256 MB
HDD: 160 GB


```

payton@the-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              64G  2.1G   59G   4% /
varrun                121M   96K  121M   1% /var/run
varlock               121M     0  121M   0% /var/lock
procbususb            121M  100K  121M   1% /proc/bus/usb
udev                  121M  100K  121M   1% /dev
devshm                121M     0  121M   0% /dev/shm
lrm                   121M   33M   88M  28% /lib/modules/2.6.20-15-generic/volatile
payton@the-desktop:~$ 

```


what is **_THE EASIEST_** solution please...?

---

### Post by wolfen69 on 2007-08-20
it is obvious this is an xp problem and not ubuntu related. check this:[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---

### Post by pgar23 on 2007-08-20
I read the info in the provided link and I am almost positive it is something to do with the boot sector. THE LINK PROVIDED ONLY HAS INFO ABOUT BOOT SECTOR VIRUSES. i DONT HAVE ANY VIRUSES BECAUSE THIS IS A FRESH INSTALL. The link did not suggest any method of fixing the error if it is not a boot sector virus. 

Can I use ubuntu and edit the menu.lst or edit the MBR or something relatively simple?

---

### Post by pgar23 on 2007-08-20
my mistake it has:

**Other Issues**

  Other potential causes of a "Stop 0x0000007B" error message include:  &#8226;The boot volume is corrupted and cannot be initiated by Windows XP. If the file system is corrupted and if Windows XP cannot initiate the boot volume during the startup process, either move the drive to another computer that is running Windows XP and run the **chkdsk **command on that drive or try to create a parallel installation of Windows XP on the drive (in a separate folder). The Windows XP Setup program checks the integrity of the volume before it copies files, and it may fix some problems in the process.&#8226; You are installing Windows XP on a mirrored boot partition that was created by Microsoft Windows NT 4.0. Windows XP does not support Windows NT 4.0 Ftdisk volume sets. If you are running Microsoft Windows 2000, you must convert all Ftdisk volume sets to dynamic volumes before you upgrade to Windows XP. If you are running Windows NT 4.0, break any mirrors and back up all the data on the stripe, the RAID5, or the extended volume sets before you upgrade to Windows XP. Ftdisk sets might not be accessible after the upgrade.

---

### Post by fantasyspirit91 on 2007-08-20
This probably doesn't have anything to do with the problem, but I'm just curious.

Do you have XP and Linux installed on the same HD? or different ones?

---

### Post by wolfen69 on 2007-08-20
boot up to the xp cd as if you were going to install. select recovery console. type- fixboot and see if that will help.

---

### Post by pgar23 on 2007-08-20
They are on same HDD.

---

### Post by pgar23 on 2007-08-20
> **wolfen69 said:**
> boot up to the xp cd as if you were going to install. select recovery console. type- fixboot and see if that will help.

where do i type fixboot? in the c:\ command line?

---

### Post by wolfen69 on 2007-08-20
once in recovery console, there will be only 1 place to type it.

---

### Post by pgar23 on 2007-08-20
> **wolfen69 said:**
> once in recovery console, there will be only 1 place to type it.

supposing there is only one place to type this comman wut are the steps after this? or will it be self explanitory?

ok also I am going to try this. I have to reboot and use xp cd now. can u check back in like 5 for additional support if needed PLLEEAASSEE?

---

### Post by pgar23 on 2007-08-20
Wolfen69,
do you know about "chkdsk /x"?
**/x****: **Use with NTFS only. Forces the volume to dismount first, if necessary. All open handles to the drive are invalidated. **/x** also includes the functionality of **/f**.

If I run this command will it destroy the GRUB? I dont want to have to keep installing these OS's the wrong way. lol

---

### Post by pgar23 on 2007-08-20
ok. I tried "fixboot" = cannot find system drive
then "chkdsk" = The volume contains one or more unrecoverable problems (my guess is with the boot sector).
wut command can i run in the terminal to check location of Windows and make sure Ubuntu is not running over this. (i know GRUB installs on hd0, but does that erase Windows boot files?)

---

### Post by plucky on 2007-08-20
```


payton@the-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              64G  2.1G   59G   4% /
varrun                121M   96K  121M   1% /var/run
varlock               121M     0  121M   0% /var/lock
procbususb            121M  100K  121M   1% /proc/bus/usb
udev                  121M  100K  121M   1% /dev
devshm                121M     0  121M   0% /dev/shm
lrm                   121M   33M   88M  28% /lib/modules/2.6.20-15-generic/volatile
payton@the-desktop:~$
```

From this display there seems to be 90G windows patrition missing. Are you sure that windows is still on your drive?

---

### Post by splintercellguy on 2007-08-20
The output of fdisk -l in Linux would help also.

---

### Post by pgar23 on 2007-08-20
I thought it was...how should i check?

---

### Post by pgar23 on 2007-08-20
> **splintercellguy said:**
> The output of fdisk -l in Linux would help also.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10942    87891583+   7  HPFS/NTFS
/dev/sda2           10943       19367    67673812+  83  Linux
/dev/sda3           19368       19457      722925    5  Extended
/dev/sda5           19368       19457      722893+  82  Linux swap / Solaris
payton@the-desktop:~$ 



```

thanks fro the support u guys. some other people were not so "supportive" lol

---

### Post by MQMike on 2007-08-20
The first thing I’d try is

--  Re-install GRUB to the MBR
--  Then check your /boot/grub/menu.lst entry for Windows.

In GRUB terms, XP is on (hd0,0) and Ubuntu is on (hd0,1).
Not difficult, and it often does the trick.
Can be done from Live CD (at a terminal type sudo grub) or from the GRUB menu by pressing “c” to get a GRUB prompt (grub>).

Re-install GRUB:

grub> root (hd0,1)
grub> setup (hd0)
grub> quit
$exit
then re-boot to test it.

Note the space after each command, like root (hd0,1), space after root; etc.

Then check the menu.lst for XP:

title XP or whatever you call it
root (hd0,0)
makeactive
chainloader +1

That’s what it should look like.

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by pgar23 on 2007-08-20
Thanks MQMIKE,

When I do this:
```

Re-install GRUB:

grub> root (hd0,1)
grub> setup (hd0)
grub> quit
$exit
then re-boot to test it.

```


> 
grub> root (hd0,1)

Error 21: Selected disk does not exist

grub> 


---

### Post by MQMike on 2007-08-20
Hmmm.  Very strange.

(hd0,1) is the first hard drive (hd0), the second partition (that's the "1").  (GRUB starts counting at zero.)

According to your sudo fdisk -l, sda1 does exit, and sda2 = (hd0,1).

See if GRUB sees (hd0) with the geometry commnad:

Get a grub prompt again,

grub> geometry (hd0)

and see what comes back for that first HD.

Edited

---

### Post by MQMike on 2007-08-20
I just edited that last post

sda2 = (hd0,1)

---

### Post by pgar23 on 2007-08-20
```

grub> root (hd0,1)
grub> setup (hd0)
grub> quit
$exit
then re-boot to test it.

```

does that code install grub to (hd0)? couldnt i just set the value of the (hd0,1) to (hd0,0) in the menu.lst >?

---

### Post by MQMike on 2007-08-20
Yes, the code installs GRUB to (hd0) which is the MBR of the HD.

No, you can't just set (hd0,1) to (hd0,0) in menu.lst because

XP is on (hd0,0)
Ubuntu is on (hd0,1)

---

### Post by MQMike on 2007-08-20
That's the way it's done -- GRUB will overwrite the XP code in the MBR and GRUB will then control the boot menu and the booting.  Standard stuff -- and very safe.
But you have something going on with your hard drive and/or that second partition (hd0,1).

What about 
grub> geometry (hd0) ?

---

### Post by MQMike on 2007-08-20
Another thing, too, maybe you could copy/paste just the relevant parts of menu.lst -- the stanzas for XP (hd0,0) and Ubuntu (hd0,1), but I wouldn't expect any problems there, but you never know.

---

### Post by pdlethbridge on 2007-08-20
Whenever I've had a problem booting XP, I've used the cd's recovery console and typed fixmbr. this fixes XP's master boot record (mbr) Then do a fresh install of ubuntu and put it on a separate partition

---

### Post by MQMike on 2007-08-21
Yes.
You can do anything you want to do.  Literally.
If you want to fix the XP MBR, you can run the XP CD and fix it.
If you want XP’s NTLDR to run the boot show for XP, then you have to rig something else up to boot Ubuntu.  Some people even boot it from NTLFR.  Some by a separate thumb drive (UFD) where GRUB is installed to.  Some by entering BIOS each time and choosing which HD to boot from (either XP or Linux).  And so on.

Even if you put GRUB in a separate partition with or separate from Ubuntu, if you want GRUB to be the bootloader, you must still install GRUB to the MBR of the BIOS first-bootable drive, in his case, hd0, and when you do that GRUB overwrites the NTLDR code in the MBR with its own 512 Bytes of Stage_1 code.

In his case, a very simple setup, there is nothing wrong with having GRUB installed to the MBR of hd0.  You can always restore, fix, change anything at any time.  No harm done.

Having said all that, it does appear that something is bent on the hd0 drive.  What did the geometry (hd0) command return?

And maybe, somehow, something got goofed up in the boot partition (hd0,0) of XP, too.  If that’s the case, and if the XP CD can also restore that part (along with the MBR), too, then, yes, try:

First run
XP CD to fix mbr.
Then
Install GRUB to (hd0) (overwriting the NTLDR code there).

---

### Post by kyphi on 2007-08-22
As MQMike and pdlethbridge and others have pointed out, first fix the MBR for XP.

After that has been sorted out you need to restore GRUB so that you can get back to Ubuntu.


To restore GRUB in a terminal type

```
sudo grub
``` then type ```
find /boot/grub/stage1
```

That last command will reveal a value such as (hdx,y).  Take note of x and y.
Type
```

 root (hdx,y)
```  substituting the values for x and y.

Type setup (hd0) where 0 is a zero.

Quit and reboot

---

