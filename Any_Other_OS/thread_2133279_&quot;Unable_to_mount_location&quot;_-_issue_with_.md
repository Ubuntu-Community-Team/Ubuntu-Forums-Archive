---
title: "&quot;Unable to mount location&quot; - issue with HDD on Linux Mint"
date: 2013-04-07
forum: Any Other OS
---

### Post by PlasticBlue on 2013-04-07
I hope somebody around can help me, I was reffered to this forum by a friend. I am aware that my problem is not Ubuntu-related, but here goes nothing:) I've already posted on the Linux Mint forums, but since I havn't had a reply as of yet, I am trying my luck here as well...
Now I did search and did google for an  answer, but what I've found where either unanswered topics or different  situations than mine. Most of the times, the error was described as  occuring either in Samba or when attempting to use network sharing -  which is not my case. Second, I am a complete noob when it comes to  Linux, so please be gentle.
Now to get to the actual problem  description: I've been wanting to try Linux for a while now, and decided  yesterday [ after some google-ing around ] to get Mint Nadia with MATE  Desktop on my laptop. Said laptop is an Acer Aspire 5315, 1.86 Ghz Intel  Celeron processor 540 with 1GB DDR2. Not really top of the line, but one makes do.  Because I was confident I could learn using Linux well enough for my  needs and the computer's performance and because I was rather sick and  tired of Windows' errors, I didn't go for the dual-OS option, but  installed only Mint.
I used the New Partition Table to discard all  previous partitions and create three completly new ones: for "/" root,  "/home" and swap. That seemed to go well, Linux was installed and after  rebooting the system I was the rather proud owner of a fresh Mint  machine. Until I went to "Computer" and tried to access my internal HDD.
What  I have are three items: 120GB Hard Drive, CD/DVD Drive and a File  System Drive. I cannot access my HDD, I only get an "Unable to mount  location. Can't mount file" error.

The sudo fdisk -l command gives me the following result:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2947

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    49999871    24998912   83  Linux
/dev/sda2        50001918   234440703    92219393    5  Extended
/dev/sda5        50001920   223999999    86999040   83  Linux
/dev/sda6       224002048   234440703     5219328   82  Linux swap / Solaris

```

And basically this is where I got stuck. In my searches, I've seen some suggesting installing a driver, but I didn't get what that was about... does anyone have any idea what to do next? Any help is much appreciated. Thanks!

---

### Post by Perfect Storm on 2013-04-07
Moved to Other OS/Distro Support.

---

### Post by Bashing-om on 2013-04-07
PlasticBlue; Hi ! Welcome to the forum.[INDENT]We love computers, just ubuntu in particular
[/INDENT]

I will do what I can to help. Using the "fdisk" command correctly, you are off to a good start !

Let's see if we can find out what is going on> Firstly in accordance with your "fdisk" You are aware there is only the one hard disk available ? And on this disk is : 1 primary partition containing / "root", 1 extended partition containing 2 logical partitions, /home and swap. As I understand what you are referring to, you do not see the files on your /home partition ?

In the / partition is a directory called "/boot". See if the system sees it; terminal command:
```
ls -la /boot
``` Good ? you have a listing.
Now lets see about the /home directory:
```
ls -la Desktop
``` --Note that is an Upper Case 'D'--
On a new install you should see in the listing 2 directories (drwxr where the d = directory).

No ?? 
Let's look and see what the system is mounting and how, in the file system table :
```
cat /etc/fstab
sudo blkid
mount
```

That should give a good idea of what is going on.

Post these outputs and we will advise on further actions.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by PlasticBlue on 2013-04-08
Hello,

Thanks for the quick reply!

   Yeap, that is pretty much what I understand from the fdisk as well, there is only the one HDD – which is ok, since I only have my internal HDD at the time, the external one is not connected – and the one HDD contains the named partitions, as I created them.  
I've attached a screenshot of what I actually see in Computer, complete with error message.

   But as I am able to actually use Linux and all it's programs without any problems, I assume that the installation was correct. Although it is a bit puzzling, given that the whole of my internal drive sums up to 120GB, that the said internal drive cannot be accessed and yet here I am using an OS installed on the  aforementioned HDD... Then again, I am after all just an ex-Windows User:)
 
 Well, these are the results for /boot:


```
   
arina@Hitachi ~ $ ls -la /boot  
 total 23388  
 drwxr-xr-x  3 root root     4096 Apr  7 13:24 .  
 drwxr-xr-x 22 root root     4096 Apr  7 13:22 ..  
 -rw-r--r--  1 root root   853738 Oct  9 23:05 abi-3.5.0-17-generic  
 -rw-r--r--  1 root root   154429 Oct  9 23:05 config-3.5.0-17-generic  
 drwxr-xr-x  5 root root     4096 Apr  7 13:22 grub  
 -rw-r--r--  1 root root 15068643 Apr  7 13:24 initrd.img-3.5.0-17-generic  
 -rw-r--r--  1 root root   176764 Oct 11 17:10 memtest86+.bin  
 -rw-r--r--  1 root root   178944 Oct 11 17:10 memtest86+_multiboot.bin  
 -rw-------  1 root root  2320733 Oct  9 23:05 System.map-3.5.0-17-generic  
 -rw-r--r--  1 root root  5171760 Nov 27 19:10 vmlinuz-3.5.0-17-generic


```


   And /home directory:

```
   
arina@Hitachi ~ $ ls -la Desktop  
 total 96  
 drwxr-xr-x  2 arina arina  4096 Apr  8 14:14 .  
 drwxr-xr-x 31 arina arina  4096 Apr  8 14:03 ..  
 -rw-r--r--  1 arina arina 51417 Apr  8 14:14 Forum_stuff.odt  
 -rw-r--r--  1 arina arina    73 Apr  8 14:14 .~lock.Forum_stuff.odt#  
 -rw-r--r--  1 arina arina 29659 Apr  8 14:10 Screenshot.png  


```

   
I hope I also got the last part correctly:

```
   
arina@Hitachi ~ $ cat /etc/fstab  
 # /etc/fstab: static file system information.  
 #  
 # Use 'blkid' to print the universally unique identifier for a  
 # device; this may be used with UUID= as a more robust way to name devices  
 # that works even if disks are added and removed. See fstab(5).  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    nodev,noexec,nosuid 0       0  
 # / was on /dev/sda1 during installation  
 UUID=28667502-d8e5-4461-b2d5-96f8b0554bd7 /               ext4    errors=remount-ro 0       1  
 # /home was on /dev/sda5 during installation  
 UUID=f46620b3-e787-4baf-90a6-4f489fdadcf0 /home           ext4    defaults        0       2  
 # swap was on /dev/sda6 during installation  
 UUID=19ed4d48-0627-43c8-8688-c2edca8caf5c none            swap    sw              0       0  
 arina@Hitachi ~ $ sudo blkid  
 /dev/sda1: UUID="28667502-d8e5-4461-b2d5-96f8b0554bd7" TYPE="ext4" 
 /dev/sda5: UUID="f46620b3-e787-4baf-90a6-4f489fdadcf0" TYPE="ext4" 
 /dev/sda6: UUID="19ed4d48-0627-43c8-8688-c2edca8caf5c" TYPE="swap" 
 arina@Hitachi ~ $ mount  
 /dev/sda1 on / type ext4 (rw,errors=remount-ro)  
 proc on /proc type proc (rw,noexec,nosuid,nodev)  
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)  
 none on /sys/fs/fuse/connections type fusectl (rw)  
 none on /sys/kernel/debug type debugfs (rw)  
 none on /sys/kernel/security type securityfs (rw)  
 udev on /dev type devtmpfs (rw,mode=0755)  
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)  
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)  
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)  
 none on /run/shm type tmpfs (rw,nosuid,nodev)  
 none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)  
 /dev/sda5 on /home type ext4 (rw)  
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)  
 gvfsd-fuse on /run/user/arina/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=arina)  
 /dev/sda5 on /media/sda5 type ext4 (rw) 


```

---

### Post by Bashing-om on 2013-04-08
PlasticBlue;
Everything on that installation appears to be in order.
I am not at all familiar with the application in your screen shot but, all I can surmise is that that application is trying to mount again the file system that is already mounted ???..I have not run Mint but I would expect that if I were to right click on that icon to gain access to "properties", more information would be available ? 
What file manager is available in Mint Can you navigate through the file system in that file manager ?

edit: 'nother thought, what is the package manager status ?
[INDENT=4]
it is only a thought

[/INDENT]

---

### Post by PlasticBlue on 2013-04-08
I really must appologise. I've been looking at this the wrong way, from a Windows p.o.v. ](*,)
i.e., I was expecting - when I open Computer - to see a list of available partitions and select the one I wanted to open... looking at my Home Folder, it dawned on me that that is the partition I had designed for my personal use and that is where all my personal data can be stored... and that is what I was actually looking for... I don't really need to access the _actual_ hardware, which is apparently what I was trying to do...

---

### Post by Bashing-om on 2013-04-08
PlasticBlue;
Good that you have it straight in your mind. This Mint system operates on different concepts than that of Windows. There is a learning curve ! Many (maybe most ?) things from Windows learning do not cross relate to linux. linux = open source and no secrets and full documentation can be found -> wonderful thing.

If this answers the question pertinent to this thread, please mark this thread as solved.
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button[INDENT=2]
we are but a keyboard away

[/INDENT]

---

### Post by PlasticBlue on 2013-04-09
Thank you again. I'll set the thread to Solved as described. And since I'm just at the beginning of the learning process, I guess I'll be reading you around:)

---

