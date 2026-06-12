---
title: "Hard Drive problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by MantinoX on 2008-01-24
Hello I Deleted  my Windows Os System completely. Before that I was running Ubuntu 7.10 Gusty on a separate Hd.  Now It's my Main os. However I have a 3rd Hard Drive that contains Data I want to Access But Ubunut wont let me:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/My Book -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/My Book ntfs-3g defaults,force 0 0
mantino@mantino-desktop:~$  mount -t ntfs-3g /dev/sdb1 /media/My Book -o force
mount: only root can do that

I need Some Assistance....

Thanks

---

### Post by delphiguy on 2008-01-24
is this harddrive running off an enclosure?
please paste the output of **sudo fdisk -l **

thanks

---

### Post by MantinoX on 2008-01-24
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7657a64

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       29265   235071081   83  Linux
/dev/hda2           29266       30401     9124920    5  Extended
/dev/hda5           29266       30401     9124888+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS
mantino@mantino-desktop:~$


By  encloser You mean Usb? No I's SATA it was working when i had windows installed but no i think I messed up big.

---

### Post by Sef on 2008-01-24
I don't see any data partition on the hard drive.

> Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4b

Device Boot Start End Blocks Id System
/dev/sdb1 1 38913 312568641 42 SFS

If Windows was there, it was overwritten.  Look at [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") or [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").  

In addition, I would unplug that hard drive until you are ready to try one of the tools mentioned above.

Update:  Found this about [SFS]("http://www.cs.auckland.ac.nz/~pgut001/sfs/") (that is the file system that is on that hard drive):

>     Note for NTFS Users / Users of Runtime Software products
    Products from Runtime Software will occasionally erroneously report NTFS disks as containing SFS partitions. This is either due to NTFS having trashed its partition information and writing a random partition ID into the partition table that happens to match the one for SFS, or more likely bugs in the Runtime Software products, since this issue has only ever come up with their software. See this news posting for more information on how to fix this. You may also want to report this issue to Runtime Software. 



---

### Post by Pandemic187 on 2008-01-24
I had the exact same problem with an external hard drive. Is that what you're having trouble with?

I can't say for *sure* what caused me to have this problem with my external HD, but I'm pretty sure I know: I had been using it in Windows, removed it unsafely, then tried to use it in Ubuntu. When attempting the latter, I received that same error. Therefore, all I had to do was boot back into Windows, connect the drive, disconnect it using the safe removal procedure, reboot back into Linux, connect the drive, and it worked fine. I'm not sure if that's what caused the problem for you, but that seemed to be my issue.

EDIT: Oh, now I just saw your second post. Well, that's how *I* managed to get this error, anyway.

---

### Post by MantinoX on 2008-01-24
It's in Ntfs I believe

---

### Post by MantinoX on 2008-01-24
So i must Install windows Again? Unmounted the Hard Drive Safely then uninstall it again?

---

### Post by delphiguy on 2008-01-24
>     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   [312568641]("javascript:void(0)")   42  SFS

I dont know what SFS means.  But if your sure that your drive is NTFS
Formatted you could try to mount it yourself.

just do
sudo mount -t ntfs-3g /dev/sdb1 /media/yourmountpoint -o force

of course yourmountpoint must exist in your /media directory if not you
can 
sudo mkdir /media/yourmountpoint

Hopefully this works for you.

hth

---

### Post by MantinoX on 2008-01-24
Holly Cow it worked!!!!! Thank You!!!

---

### Post by delphiguy on 2008-01-24
glad to know that it worked... 
I had the same issue as yours but only with a USB Enclosure thats why I asked about it.

if you want it to be the case everytime you boot up you need to edit your
/etc/fstab and add this line at the end
            /dev/sdb1 /media/yourmountpoint ntfs-3g defaults,force 0 0

hth

---

### Post by MantinoX on 2008-01-24
Im looking in the etc folder and i don't seem to have it.....:confused:

---

### Post by zero-9376 on 2008-01-24
if you have no intention of installing windows again you might want to think about moving your data to an ext3 partition as it will be faster (ntfs-3g uses alot of cpu) however this will require a temporary storage location.
In the mean time you may want to look at ntfsprogs there may be something in there (cant recall right now) that can check the consistency of the partition so you dont have to use the force option. ntfsprogs is in the ubuntu repos so you can install from apt-get, synaptic or add/remove

---

### Post by MantinoX on 2008-01-24
Thats what im probly going to do.

---

### Post by delphiguy on 2008-01-24
you try this
sudo nano /etc/fstab

---

### Post by MantinoX on 2008-01-24
At the moment Im transferring 90gigs of Comic Files t (.Cbr)  to my other 320 gig hd Then im just going to re format the hd. I'll run the program this morning i need some sleep not to mention its going to take 40mins to tranfer all mystuff.

---

### Post by MantinoX on 2008-01-24
I reformatted the hard drive and put it in ext3 format but when i go and try to transfer my files over i have no permission.
My first question is (If you know) How do i by pass this?
I looked on the forums and found article about this  but im still lost i seen some threads about etx3 format and i just I need a little bit more assistance On how to get by this little obstacle. 

Thank you

---

### Post by RiTarDid on 2008-01-24
> **delphiguy said:**
> I dont know what SFS means.  But if your sure that your drive is NTFS
Formatted you could try to mount it yourself.

just do
sudo mount -t ntfs-3g /dev/sdb1 /media/yourmountpoint -o force



the error message says to type this command, but it didn't work for me in xubuntu gutsy, instead: 

sudo mount /dev/sdb1 /media/*your mountpoint* -t ntfs-3g -o force

worked like a charm and save me a windows "safe removal" :)

---

### Post by MantinoX on 2008-01-24
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7657a64

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       29265   235071081   83  Linux
/dev/hda2           29266       30401     9124920    5  Extended
/dev/hda5           29266       30401     9124888+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

[COLOR="Blue"][B]Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux[/B][/COLOR]
mantino@mantino-desktop:~$ 


How Can i get the ext3 to be recognized? I fromatted it but when i mount it it wont allow permission to transfer files.

---

### Post by MantinoX on 2008-01-24
](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by MantinoX on 2008-01-24
anyone?

---

### Post by cjm5229 on 2008-01-24
Lost and Found is a special file on your HDD. It is not there to write to. Just try adding a file to the drive, not that folder.

---

### Post by delphiguy on 2008-01-24
can you write to /media/disk?
what happens if you do
touch /media/disk/myfile.txt from terminal?

im guessing that your user have no permissions for /media/disk 
so maybe you could try this:
sudo chmod 777 /media/disk

and see what happens.

---

