---
title: "Not Installing   - Kernel Panic"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Cyan1 on 2008-04-21
I've made a number of attempts to Intall Ubuntu 7:10 and it is getting progressively worse.

IDE Primary Master is Samsung SV2044D
Processor is AMD 761+686B AGPset

The first time it made it 96% of the way through the Install - it gave one error message at about 90% - something about unable to move user (didn't write it down so can't remember now) - I hit Ok and carried on to 96% and then froze/crashed.

I rebooted the computer and it came to an Ubuntu page asking for username and password - I tried to username and password that I had used on the unsuccessful install - they were not accepted.

I then removed the Ubuntu CD and rebooted - it was unable to find an OS (So I know it has wiped Windows)

Booted with CD again and was back to the Live CD window with option of running with CD or installing - tried installing again - froze at 23%

I have verified the CD
Tried to see how I can reformat the HDD from BIOS (sure I did it before a few years ago when we installed XP - but can't see how)

and have once again tried to reboot - the intail Ubuntu page comes up - I tell it to Start or Install - and it runs down a number of codes which end with

[ 29.805636] Kernel panic - not syncing: fatal exception in interrupt


Where do I go from here?

---

### Post by phidia on 2008-04-21
Can you get a livecd to run-that is to get a desktop?
It's always a good idea to 1st try the livecd to see if your specific hardware is recognized.

When you selected to install ubuntu did you choose to have it use the entire drive?
If you chose that option then your window's install has been removed, but if you chose to resize and install to the appropriate partition then all that has happened 
is the MBR has been overwritten and you can get back to windows by fixing the MBR. (There are threads on how it do that)

Without  know more it hard to say what your options are however you can try different [live cds]("http://en.wikipedia.org/wiki/LiveCD") and see 
if one of those will recognize your hardware, and mount your hard drive to see what's there.

Please include the amount of ram and video card in your computer too.

---

### Post by Cyan1 on 2008-04-21
I've been running it with the Live CD for a while and so was happy that it was recognising my hardware.

My last couple of attempts to boot it - it has not got as far as the Live CD page

On my first install attempt - when asked about partitions - I left it in the top button, which I think was available free space - it came back with an error and then only gave me the option of using the whole disk (which I was happy to do, because I really don't want Windows there anymore)

RAM is 526k Video Card is GeForce 2 GTS

C

---

### Post by Cyan1 on 2008-04-21
Further to the last - I know have the LiveCD working - so if there is a way of checking my system from here, I would appreciate the help.

C

---

### Post by phidia on 2008-04-21
> **Cyan1 said:**
> I've been running it with the Live CD for a while and so was happy that it was recognising my hardware.

My last couple of attempts to boot it - it has not got as far as the Live CD page

On my first install attempt - when asked about partitions - I left it in the top button, which I think was available free space - it came back with an error and then only gave me the option of using the whole disk (which I was happy to do, because I really don't want Windows there anymore)

RAM is 526k Video Card is GeForce 2 GTS

C


I don't think there is any 526 RAM configuration but if it's 512MB not "KB" it should run. 
A GeForce 2 series is pretty old but still it should work.

From the live cd the gui should let you view your hard drive-look in "computer" from the Places top menu item.

---

### Post by louieb on 2008-04-21
I'd like for you to do 2 things.
1st boot the live CD and run the check media for defects option. If you have any errors you should burn another CD. All it takes is a few twisted bits in the wrong place to get very weird and unwanted results.

2nd. open **applications>accessories> terminal** and list and post the partition table. (lower case L at the end).
```
sudo fdisk -l  
```

---

### Post by Cyan1 on 2008-04-21
Thanks phidia - typing 526k just shows how confused I'm getting!

What am I looking for in "computer" ? and how will it help me complete an Install?

---

### Post by phidia on 2008-04-21
> **Cyan1 said:**
> Thanks phidia - typing 526k just shows how confused I'm getting!

What am I looking for in "computer" ? and how will it help me complete an Install?

Are you able to get a functioning desktop from the live cd?

If you are the ubuntu desktop/GUI lets you look at your hardware-in this case your hard drive partitions should show on the desktop or from the menu Places>Computer.

louieb's post should work and is a good idea too. Check the cd for integrity and from the terminal type sudo fdisk -l and copy and paste the output of that.

---

### Post by Cyan1 on 2008-04-21
I have checked the Cd for errors - and it says it is OK

Looking at sudo fdisk -1 I get

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd94dd94

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2372    19053058+  83  Linux
/dev/hda2            2373        2481      875542+   5  Extended
/dev/hda5            2373        2481      875511   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
 

What does that tell me?

C

---

### Post by Cyan1 on 2008-04-21
and at Places>computer there is
computer:///Floppy%2520Drive.drive
computer:///CD-ROM%2520Drive.drive
computer:///CD-RW%2520Drive.drive
computer:///18.2%2520GB%2520Volume.drive
computer:///HP%2520Photosmart%25203310.drive
computer:///Filesystem.desktop

and within File system there is:-

/bin       Modified 15 Oct 2007
/boot     Modified 15 Oct 2007
/cdrom  Modified 15 Oct 2007
/dev      Modified 21 Apr 2008
/etc      Modified 21 Apr 2008
/home   Modified 21 Apr 2008
/initrd    Modified 15 Oct 2007
/lib        Modified 21 Apr 2008
/media Modified 15 Oct 2007
/mnt     Modified 08 Oct 2007
/opt     Modified 15 Oct 2007
/proc    Modified 21 Apr 2008
/rofs    Modified 15 Oct 2007
/root    Modified 21 Apr 2008
/sbin    Modified 21 Apr 2008
/srv    Modified 15 Oct 2007
/sys    Modified 21 Apr 2008
/tmp   Modified 21 Apr 2008
/usr    Modified 21 Apr 2008
/var    Modified 21 Apr 2008
/initrd.img Modified 15 Oct 2007
/vmlinuz   1.7MB link to unknown Modified 15 Oct 2007


So I presume some of those are old files and some are the result of today's attempted Installation

C

---

### Post by louieb on 2008-04-21
The fdisk output tells me the partitioning step worked. Your disk is partitioned in the normal manner for a use whole disk install. 

The fact  there is a broken link in root tell me the install died while trying to install the kernel or build the initrd file. 

Just wondering how much ram does this PC have. Building the initrd file is takes time and memory. 

My next suggestion is to use the alternate install CD, its a text based installer.  Its not any harder to use that the live CD and it often works where the live CD has failed.

---

### Post by phidia on 2008-04-23
> **Cyan1 said:**
> I have checked the Cd for errors - and it says it is OK


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd94dd94

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2372    19053058+  83  Linux
/dev/hda2            2373        2481      875542+   5  Extended
/dev/hda5            2373        2481      875511   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
 

What does that tell me? C

It tells us that you have the ext3 (linux filesystem) on your 1st (hda) 20GB drive. *Due to the forum revamping there was a delay in seeing your response-sorry

You are unable to boot or successfully login to your desktop but you can use the live cd to get a desktop-gui is that correct?

You could try a re-install or use the alternate cd and choose the rescue a broken system option. At this point if you don't have any personal data or settings you want to keep perhaps re-installing, while paying careful attention to any error output, is easier.

---

### Post by phidia on 2008-04-23
louieb, Cyan1 has said he has 512MB of RAM (unless I'm confusing this post with another). That should be enough to install with, but I agree that the alternate cd can be a better choice for some installs.

---

### Post by Cyan1 on 2008-04-29
Thanks to Louieb and phidia for advice so far - not been able to carry it out until today - work and life getting in the way! - and this is still causing trouble.

I have 64Mb of RAM (or a base memory of 640k - which I presume is the same thing and an extended memory of 523264k - I presume that is the HDD)

I tried to carry out a memory test v1.70 - which failed at test 7 "random number sequence failed" and then a list of numbers  which started
0000529f044 - 82.8mb
0000356e044 - 53.8mb
0000b03e044 - 176.8mb
0001b655044 - 438.3mb
and so on - too many to write them all down

I had one more go to install from the Live Cd (using OEM install) and it got as far as as 96% and the stopped saying
"Error installing oem-config subprocess post-installation script killed by signal (segmentation fault)

Error installing oem-config -gtk dependency problems - leaving unconfigured

An error occurred whilst installing package E:sub-process/user/bin dpkg returned an error code   (1)

It then continued trying to install - and got to 103% (!) completely removed language-pack-bin - at which point it froze.

Trying today with the Alternate CD

The first attempt was going well until it got to 81% configuring yelp - at which point it froze (left it an hour but clearly nothing was happening)

Attempts 2 & 3 resulted in a "linux panic"

Attempt 4 - had a couple of errors but allowed me to go back a step and try again, until  whilst installing the base system it froze at 66% python

Attempt 5 froze at 83% of installing base system

As my processor is an AMD I tried the Alternate AMD - the first attempt wanted a login and password - which I haven't got, the second took me to the first menu but then said "Your CPU does not support long mode. use a 32 bit distribution" - which I presume means that I'm right to stick with the i386

Another attempt stopped whilst partitioning - all blue screen and no text

Final attempt finished with the message "An error was returned whilst trying to install kernal into the target system kernal pack 'linux-generic' check lvar/log/syslog/ or see virtual console for the details

It took me back to install from menu but froze on 0%

So any ideas what is happening or what more I can do? - is the memory test showing there is a problem with RAM which is going to make installation impossible? My local computer shop says he will re-install the original Windows and clean everything up - if I can find it, but that was ME and I really don't want it

I can get a desktop with the Live CD - and looking at my files I can see that they look much the same as they did on 20 April - they are just dated 29 April - and the broken link vmlinuz 1.7MB link to unknown Modified 15 Oct 2007 is still at the bottom of the list

Re-reading phidia's last post I guess the next move might be the rescue a broken system option - but what am I looking for?

all advice gratefully received

C

---

### Post by Cyan1 on 2008-04-29
also wondering if there would be any benefit in reformating and starting on a clean HDD? - trouble is I've found the code for doing that on the warning about Malicious Commands to be Read but not Run!

but then I know have a Hard Drive with nothing much on it and no way of using it without an installed OS - so what would be the harm?

---

### Post by Cyan1 on 2008-05-01
Bump

---

