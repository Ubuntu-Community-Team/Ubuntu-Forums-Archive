---
title: "PPC Dual Boot Install"
date: 2014-05-21
forum: Apple Hardware Users
---

### Post by robert94 on 2014-05-21
Hello

Before I try rsavages 'wubi' like install [here]("http://ubuntuforums.org/showthread.php?t=2224808") I want to install Lubuntu 14.04 as dual boot on a Powerbook G4.

/dev/sda [80GB total]
 /dev/sda1 0 GB unknown
 freespace 134MB
 /dev/sda3 hfs+ is the 58GB partition where the current MAC OS 10.5.8 is located in
 free space 134MB
 /dev/sda5 hfs+ is the 20GB partition I created for Lubuntu
 free space 134MB

1. When I format sda5 should I use ext2, 3 or 4 ? [or an I supposed to use a NewWorld partition boot or not, what is NewWorld for ?]
2. When I am asked for a mount point what should I use ?
3. When it is finished do I get some sort of yaboot menu that has MAC OS and Lubuntu or do I need to create that

I am mindful of breaking the existing MAC OS install

---

### Post by theos911 on 2014-05-21
I would let it get to the partitioning section and delete /dev/sda5. Then use the "Guided - Use Free Space" option. It will setup the boot loader and the system partition with a proper mount point and the swap that you will need.

Yaboot will ask you at boot which OS to start. It will have a menu and instructions, but "x" boots Mac OS X and "l" (that is a lowercase L) boots Linux. If you have multiple Linux installs you will choose at a second menu which distro to boot and you can see the options by hitting tab. This is also how you boot the previous kernel if a new one breaks something.

---

### Post by robert94 on 2014-05-22
Thank you for the reply 

I deleted the 20GB partition from inside MAC OS

When I now try the install options I now get are:


1.  'Install Lubuntu alongside MAC OS X', shows: 

Files /dev/sda4[ext4] 11.4GB
Lubuntu /dev/sda**[COLOR=#ff0000]5[/COLOR]** [ext4] 9.4GB

& can make either a minimum of 4.9GB using the slider 

or

2. 'Sometime else' install option shows the 20GB now as

/dev/sda4 ext 4 20GB
/dev/sda5 swap  951MB

Clearly the Lubuntu installed prefers or rather defaults to ext4

Questions:

1. Why does the install alongside option not allow a single partition for Lubuntu i.e. the os + files but wants 2 partitions one for files and one for 
Lubuntu but does not show a swap partition ? [I suspect it creates sda6 as swap ?]
 
2. The Something else options allows me a single partition for Lubuntu [os+files] and a swap

3. When I boot from live DVD i need to use the live video=radeonfb:1024x768-32 will I need to do that when installed onto the Powerbook and if so can I enter that at yaboot at the time "x" is needed ?

---

### Post by theos911 on 2014-05-22
Sorry, I always use the alternate installer rather than the live one so those options are different than I know, but the first looks it will give you dual boot and the second not so much.

---

### Post by rsavage on 2014-05-22
[COLOR=#000000]The 'Install X alongside Y' option is the auto-resize option.  It wants to shrink a partition and create a new one to install Lubuntu onto.  Which is what it looks like it is sort of doing, thinking [/COLOR]MAC OS X is installed on sda4.  Ages since I've used the automatic options, I always use the manual ('something else') option.  The auto-resize looks like it doesn't work anyway in 14.04 ([http://iso.qa.ubuntu.com/qatracker/milestones/314/builds/66927/testcases/1301/results](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds/66927/testcases/1301/results) ) so just go the manual route.  One thing though, surely it wants to install a bootstrap partition too?

[COLOR=#000000]video=radeonfb:1024x768-32 should be passed onto the install automatically, but it is not the best option.  You should be using radeon KMS which is the video=ofonly parameter (in Lubuntu you will probably also have to combine it with radeon.agpmode=-1 ).  Radeon KMS doesn't have suspend, but hibernation works.  You can adjust them after installed, video=radeonfb:1024x768-32 is the safest to do the install on.[/COLOR]

---

### Post by robert94 on 2014-05-22
> **rsavage said:**
> [COLOR=#000000]The 'Install X alongside Y' option is the auto-resize option.  It wants to shrink a partition and create a new one to install Lubuntu onto.  Which is what it looks like it is sort of doing, thinking [/COLOR]MAC OS X is installed on sda4.  Ages since I've used the automatic options, I always use the manual ('something else') option.  The auto-resize looks like it doesn't work anyway in 14.04 ([http://iso.qa.ubuntu.com/qatracker/milestones/314/builds/66927/testcases/1301/results](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds/66927/testcases/1301/results) ) so just go the manual route.  One thing though, surely it wants to install a bootstrap partition too?

[COLOR=#000000]video=radeonfb:1024x768-32 should be passed onto the install automatically, but it is not the best option.  You should be using radeon KMS which is the video=ofonly parameter (in Lubuntu you will probably also have to combine it with radeon.agpmode=-1 ).  Radeon KMS doesn't have suspend, but hibernation works.  You can adjust them after installed, video=radeonfb:1024x768-32 is the safest to do the install on.[/COLOR]

Actually the alongside option doesn't want to shrink the existing MAC OS partition [sda3] as you imply [or I would expect], it wants to partition the 20GB I had unallocated into two partitions sda4 [for files] and sda5 [for lubuntu], what I don't get is why the install wants one partition for files and one for lubuntu ?  or maybe it does that so the 'files' partition can be encrypted separately ? 

As you say I am leaning towards the 'something else' manual method and boldly assume it install a bootstrap and swap partition ? :eek:

note whenever I used video=ofonly,  I find that Lubuntu quickly freezes, with just video=live often the active window/panel doesn't display hence I used video=radeonfb:1024x768-32

---

### Post by robert94 on 2014-06-02
Since the along side doesn't appear to work I want to use the something else option [so I have a continuous 20GB partition for Lubuntu 14.04]

Can anyone advise which mount point I should use so I don't beak the existing MAC OS X install ?

---

### Post by theos911 on 2014-06-02
The partition you intend to install Linux on should have a mount point of /.

---

### Post by robert94 on 2014-06-03
> **theos911 said:**
> The partition you intend to install Linux on should have a mount point of /.

Thank you for the reply

**1. Will that break the MAC OS X already installed ?**
2. Why does the install give other options for mount points such as /boot,  /home etc

---

### Post by theos911 on 2014-06-03
1. No
2. Sometimes it is helpful to have certain parts of the Unix filesystem on separate partitions. They can make it so home directories are encrypted without encrypting the entire disk for instance Those who do a large amount of compiling from source will sometimes have /var on a separate partition. Nowadays there is not much reason to have /boot on a separate partition unless you are booting an old world machine and therefore need access to the kernel and initrd from within the classic Mac OS. The classic Mac OS only has ext2 drivers, but most people want their Linux installs on ext3 or ext4. In that case you can make an ext2 partition for your boot files that you can access from the classic Mac OS and have the benefits of a journaled filesystem on your main ext4 Linux partition that holds everything else.
[https://en.wikipedia.org/wiki/Unix_filesystem#Conventional_directory_layout](https://en.wikipedia.org/wiki/Unix_filesystem#Conventional_directory_layout)

---

### Post by robert94 on 2014-06-04
theos911

Thank you again for the explaination

I went to install into /dev/sda4 ext4 / 20GB and was prompted "No New Word partition was found. The Yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using HFS Macintosh File System"

This article [here]("https://help.ubuntu.com/12.04/installation-guide/powerpc/partition-programs.html") states that this partition must be the 1st partition and that any existing small [apple] driver partitions should be retained ?

gparted currently shows

/dev/sda
 /dev/sda1 0MB unknown
 freespace 134MB
 /dev/sda3 hfs+ 58GB
 /dev/sda2 1MB ext4 / 20GB
 /sda/sda5 swap 951MB
 /freespace 0MB 


I could make the 134MB free space [or a portion of it] the 'new world' boot partition but I suspect it could be a apple driver partition in the before mentioned article?

What should I do so I don't loose the existing MAC OS X install on sda3 ?

---

### Post by theos911 on 2014-06-04
Unless I'm forgetting something, you should be able to put the New World Partition in that free space.

---

### Post by robert94 on 2014-06-08
> **theos911 said:**
> Unless I'm forgetting something, you should be able to put the New World Partition in that free space.

I went to do that but it gives an option of the 'newworld boot partition' being a primary or logical, which should I use ?

---

### Post by theos911 on 2014-06-08
Primary

---

### Post by robert94 on 2014-06-13
Well I created a 1MB Neworld boot partition so the partition map looks like this

dev/sda
/dev/sda1 0MB unknown
/dev/sda6 newworld / 1MB
freespace 133MB
/dev/sda3 hfs+ 58GB
/dev/sda2 1MB
/dev/sda4 ext4 / 20GB
/sda/sda5 swap 951MB
/freespace 0MB 

But when got to install into sda4 [20GB Ext4] I get the following msg

[COLOR=#a52a2a]The file system on dev/sda6 assigned to / has not been marked for formatting/ Directories containing system files (etc/,/lib,usr,/var...) that already exist under any defined mountpoint will be deleted during the install.

Please ensure you have backed up etc

[/COLOR]It appears that is is saying the 1MB Newworld parition I created [presumably for yaboot] not been marked for formatting [it doen't allow me to format] so I assume it is saying anything under sda6 and sda4 [which both have mount points] will be lost ?

Thoughts ?

---

### Post by theos911 on 2014-06-13
Yes, it would be lost, but you have nothing stored there so you are fine.

---

### Post by robert94 on 2014-06-14
> **theos911 said:**
> Yes, it would be lost, but you have nothing stored there so you are fine.

Thank you for the reply

presumably sda6 [newworld] and sda4 [where I want lubuntu] would be impacted and not sda3 where mac os x is ?

I have two mount points on on sda6 [newworld] and sda4 [ext4], is that to be expected for dual boot or should there be one mount point ?

---

### Post by theos911 on 2014-06-14
Unless it says sda3 will be formatted, your data on sda3 will be fine.

I honestly don't recall if the newworld partition gets a mount point.

---

### Post by robert94 on 2014-06-16
theos

success ! I am now typing this msg from lubuntu 14.04 and MAC OS X is still there and working

My many thanks to you 

ps: do you use Java if so what package. Icedtea + openjdk7 is really slow [& takes the cpu to 100%] and doesn't work for a remote citrix gateway I access at work

---

### Post by theos911 on 2014-06-16
I am glad to hear it! I don't really use java on PowerPC.

---

### Post by robert94 on 2014-06-17
> **theos911 said:**
> I am glad to hear it! I don't really use java on PowerPC.

I spoke too soon 

When I cold or warm restart the G4 I no longer get the yaboot menu :(
I then used the Apple Option key to get the Apple boot menu it shows 2 drives - the MAC OS one [with a X] and the other one [with a little penguin] obviously the later being lubuntu

When I select boot of the linux one I finally get the yaboot menu back but when I type l for linux I get the following:

[COLOR=#b22222]welcome to yaboot version 1.3.16
Enter "help" to get some basic usage information
boot: l
please wait, loading kernel....
/pci@f4000000/ata-6@d/@0:4,l: no such file or directory
boot:
[/COLOR]
So it appears a normal boot sequence is no longer picking up the new world boot partition, when I force that and type l [for linux] it would seem that it cannot load the ubuntu kernel [whatever that may be]

Any ideas  :confused:

---

### Post by rsavage on 2014-06-17
You should get a menu before that where you type 'l'.  When you get the "boot:" prompt you type "Linux" (or just press return).

---

### Post by robert94 on 2014-06-23
> **rsavage said:**
> You should get a menu before that where you type 'l'.  When you get the "boot:" prompt you type "Linux" (or just press return).

For the first few times I got the yaboot menu when I restarted the G4. I can now only access the yaboot menu if I boot by holding down the the Apple command key which then displays the Apple boot menu i.e. MAC OS, Linux and Optical. When I choose to boot from the Linux disk only then do I get the yaboot menu as you describe. I am not sure yet why that is.

So far the Lubuntu 14.04 performance is slow [but usable] with the cpu often going to 100%. I assume this is due to the 1Ghz PPC processor. For comparision my Netbook with an atom dual core 1.5Ghz processor is far faster [at least with Xubuntu]

---

### Post by Ric_Helm on 2014-06-26
For a Mac PowerPC architecture, does it have to be Lubuntu?
I have a G5 that I would like to install Ubuntu Studio. I don't care if is an older Ubuntu OS. I would like to set it up as dual boot. I even plan to use separate internal Hard Drives for each OS.

---

### Post by robert94 on 2014-06-28
> **Ric_Helm said:**
> For a Mac PowerPC architecture, does it have to be Lubuntu?
I have a G5 that I would like to install Ubuntu Studio. I don't care if is an older Ubuntu OS. I would like to set it up as dual boot. I even plan to use separate internal Hard Drives for each OS.

No it does not have to be Lubuntu

Located [here]("https://wiki.ubuntu.com/PowerPCDownloads") is a list of PPC releases

---

