---
title: "GRUB 10.04 MacBook /dev/sd3 (NEED HELP!!)"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by xxander on 2010-05-01
Hello.  I have installed rEFIt on my computer and burned a Live CD of Ubuntu 10.04.  I created a partition via Boot Camp Assistant.  Then I booted from the Live CD and used gparted to delete partition and create 'free space'.  I then proceeded to install Ubuntu and chose 'choose largest free space' option.  When I get to the last page of installation, I click on 'advanced' and I am supposed to assign the boot loader (GRUB) to /dev/sda3 (this link said how to do it - [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation))  BUT THERE IS NO OPTION FOR THIS...  there are options for my entire hard drive, /dev/sda1, /dev/sda2. and two options for /dev/sda-1..  I would really like to know how to install Ubuntu 10.04 on my system (Intel MacBook 3,1.)  9.04 worked for me, but I chose a weird way to install it, so I though I would use rEFIt this time.  Please help me with this.

If the best way is to install 9.04 and then upgrade from that, let me know.  But until then, I would like to know how to actually install this version.

---

### Post by xxander on 2010-05-01
bump.. I REALLY  NEED HELP GUYS... and so do others... a lot of others...

---

### Post by jacques4x4 on 2010-05-01
Xxander,  No joy here on upgrading Karmic..  It blew out my grub.

Jacques4x4

---

### Post by xxander on 2010-05-01
NOOO!  Man, well we really need help with this.  How can we contact Ubuntu?!

---

### Post by amd-64 on 2010-05-01
Not the best help, but I will give it a try. 

First, you may have needed to bless the partitions from rEFIt or MACOSX. I don't remember how this was done. 

Second, it you wanted to proceed with the install, you can skip installing grub all together. Finish the installation, reboot from live CD, mount /dev/sda3 and chroot to the /dev/sda3 system you just installed and install grub. From the live CD:

```


sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo chroot /media/sda3
grub-install /dev/sda3
```


Needless to say, make sure you have backed up whatever you have in case this does not work out.

---

### Post by bmu2010 on 2010-05-02
hii amd-64,


did it work for u ?

thanks

---

### Post by Daniel1994 on 2010-05-02
Hi guys

Im having the same problem on a mac pro.

Any progress?

---

### Post by jacques4x4 on 2010-05-02
Daniel,

No joy for me..  I tried using the alternate installer..  (text based). And it allowed me to point grub to sda4.  Even with that it blew out my first partition..  the efi firmware.. I could boot into osx or 10.04 by holding down the option key.. but got an error message "Error: Not Found return from gptsync.efi"  Also "stats:MBR partition table is invaid, partition overlap"

At this point I am out of my depth.

Jacques4x4

---

### Post by xxander on 2010-05-02
I'm going to try some things today, and if that doesn't work, I'll use the Terminal codes AMD supplied for us.. I'll post how it went later today or tomorrow.

---

### Post by ne0genius on 2010-05-02
you need to install grub

this guide will walk you through installing grub using the livecd. it worked for me.

[https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD](https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD)

check which partition linux is installed on (should be sda4 i have same setup)

```
sudo fdisk -l
```

here are the commands you will *likely* use if you are dual booting off a single drive with refit.

```
sudo mount /dev/sda4 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub
grub-install /dev/sda
```

if you have trouble chroot'ing you can also use this

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

make sure to run update-grub so that grub.conf gets written. let me know how it goes.

-
aj

---

### Post by jacques4x4 on 2010-05-02
> here are the commands you will *likely* use if you are dual booting off a single drive with refit.

Code:

sudo mount /dev/sda4 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub
grub-install /dev/sda

if you have trouble chroot'ing you can also use this

Code:

sudo grub-install --root-directory=/mnt/ /dev/sda

make sure to run update-grub so that grub.conf gets written. let me know how it goes.

shouldn't the grub-install be /dev/sda4 ??? Would you please clarify?

thank you... Jacques4x4

---

### Post by bmu2010 on 2010-05-02
Jacques4x4

I have same experience as you faced. 
Partition overlaps and its also sometime not booting from rEFit.

thanks

---

### Post by ne0genius on 2010-05-02
> **jacques4x4 said:**
> shouldn't the grub-install be /dev/sda4 ??? Would you please clarify?

thank you... Jacques4x4

no. this is correct

grub-install /dev/sda

---

### Post by jacques4x4 on 2010-05-02
ne0genius.. please be patient..  when I install from the live cd I should just let the installer choose sda for grub?  won't that over write the EFI on sda1?  

bmu2010.. sorry but I am glad I am not alone on this..  I did an install choosing not to install grub.. First bootcamp for free space, the gparted to delete sda3, then the install from 10.04 choosing use largest free space without installing grub..and I got this error again..  It was my plan to follow ne0genius instructions.

The next time I try I will specify partitions with gparted, install, and try to install grub2 from the live cd..  

Struggling here.  any hints??

thanks,

Jacques4z4

---

### Post by xxander on 2010-05-02
Prepare to mark this thread as 'solved'.  For us MacBook (Pro) users....

1.  Install 9.10... using rEFIt and Boot Camp Assistant to create the partition.
2.  Boot from Live CD - choose to try without changes to computer.
3.  Go to System --> Administration --> Gparted
4.  Delete the partition you just created
5.  Make sure to APPLY CHANGES
6.  Double click on INSTALL icon on desktop
7.  On last step, click 'advanced' and choose /dev/sda3
8.  Once 9.10 installation successful, have an ethernet cable to connect to internet.
9.  Go to Update Manager and install all of the jank in there. (DO NO UPGRADE YET)
10.  IMPORTANT - There is a GRUB update or something (GRUB-PC), choose to keep the locally modified one... don't change anything. I did this and so far my computer still works.
11.  In Update Manager, choose Upgrade to 10.04 at the top. (Notes- I haven't done this step yet, I am going to let my computer run through the night doing this [takes several hours].
12.  ENJOY!!

If this doesn't work, I will be surprised... I haven't done #11 yet, but I will and will post results tomorrow.  Thanks everybody.  I would only do it this way because Jacques4x4 and I have tried a bunch of other ways, only to destroy our hard drive and have to restore...

Good Luck!

---

### Post by jacques4x4 on 2010-05-02
No joy for me using this method..  sigh..

---

### Post by bmu2010 on 2010-05-02
This not the solution for me ..... as I remember there was a problem (i am not sure abt it now) when i did it earlier........thanks for your effort

---

### Post by jacques4x4 on 2010-05-02
ne0genius  working through your guide I get this error when I execute update-grub

ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found memtest86+ image: /boot/memtest86+.bin
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done


Thoughts please??

---

### Post by amd-64 on 2010-05-02
> **bmu2010 said:**
> hii amd-64,


did it work for u ?

thanks

I don't know for sure. I upgraded from Karmic, it has been a while since I installed. In my case, I have grub on /dev/sda3 and the root partition is on /dev/sda7, I manually update grub with each new kernel. It is not optimal, but bios cannot see /dev/sda7 and I am not brave enough to try grub2 with EFI.

There are some conflicting messages here. Why would you install to /dev/sda. This will likely affect efi and OSX. Is it update-grub or grub-install. I don't have definite answers.

---

### Post by jacques4x4 on 2010-05-02
> There are some conflicting messages here. Why would you install to /dev/sda. This will likely affect efi and OSX. Is it update-grub or grub-install. I don't have definite answers.

No question about that..  

results of sudo fdisk -l = 

[COLOR="Blue"]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       25090   201326592   af  HFS / HFS+
/dev/sda3           25090       29802    37848064   83  Linux
/dev/sda4           29802       30402     4816896   82  Linux swap / Solaris[/COLOR]

then using Recover Grub2 via LiveCD 

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
 
[COLOR="Blue"]ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# nano /etc/default/grub
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
done
root@ubuntu:/# grub-install /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
[/COLOR]
then as ne0genius suggested I tried:

[COLOR="Blue"]root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.[/COLOR]


Needless to say I did not use force...

thoughts comments???

thank you,

Jacques4x4

---

### Post by WindPower on 2010-05-02
I have exactly the same problem. I wouldn't date try to install GRUB on /dev/sda. That's a recipe for even further computer suicide.

---

### Post by xxander on 2010-05-02
Updating as we speak!  Keeping my figers crossed!! :)

---

### Post by panachippara on 2010-05-02
Well, I just did a triple boot on my Mac Book. I really don't have much experience with Linux or mac. So anyone should be able to repeat what I did. Here is a brief description.

Mac model. 2.53GHz processor(Intel core i5), 8GB RAM, 500GB HDD, NVDIA GeForce GT330M, 15 inch display. The machine is just one month old.

First I installed Windows 7 Ultimate using bootcamp. Used 100GB for windows partition. By just following Bootcamp instructions everything worked fine.

Second I went back to OsX and used disk utility to repartion Mac drive. Divided the MAc HDD into two(100GB for OsX  and 270GB as new partition.

Then used Ubuntu 9.10 CD to boot the system. Followed the initial screens, and selected the option "install on a specific drive". I forgot the actual name of that option. But it allows you pick the exact drive you want install Ubuntu. There I picked the new partition I made in OsX. choose to create a small partition out of it for using as swap. I made 8GB for swap from the free area at the end of drive. Choose that as linux swap.

Next choose the other area (262GB partition)   and formatted that in JFS format. Then choose that for ubuntu install. The rest went pretty straight. Then  it will ask whether to import boot loading option for other OS. I choose to import windows boot to be handled by GRUB. 

Then restarted the machine. It went into Mac by default. if you press option key down then it will show windows and Mac drives. But when I select windows, Linux grub will load and ask for choosing ubuntu or Windows. And you can boot any one of the os from that menu.

Then I went back to Mac and installed rEFIt. After two reboots it shows all three OS's and I when I choose windows the Ubuntu grub loads and ask to choose windows or ubuntu. So unknowingly I made an option for double selection. In Ubuntu 9 everything except sound worked. Then I updated the OS (using software update in Ubuntu) to Ubuntu 10 and everything including sound worked.

So there you go. Its very simple. I am a newbie. If I managed to get this thing up, then for Guru's it must be easy.

---

### Post by jacques4x4 on 2010-05-02
panachippara the 9.10 version installs just fine.. it is the 10.04 version where we are having troubles..  I have had no issues triple booting with 9.10..  now 10.04.. that is a different story...

---

### Post by panachippara on 2010-05-02
Why dont you upgrade to  10.04 from the update manager of version 9.10?  Upgrade works perfect. May be your  problem come from attempt to install fresh from CD. Please excuse if it sounds ignorant.

---

### Post by Zannek on 2010-05-02
> **panachippara said:**
> Well, I just did a triple boot on my Mac Book. I really don't have much experience with Linux or mac. So anyone should be able to repeat what I did. Here is a brief description.

Mac model. 2.53GHz processor(Intel core i5), 8GB RAM, 500GB HDD, NVDIA GeForce GT330M, 15 inch display. The machine is just one month old.

First I installed Windows 7 Ultimate using bootcamp. Used 100GB for windows partition. By just following Bootcamp instructions everything worked fine.

Second I went back to OsX and used disk utility to repartion Mac drive. Divided the MAc HDD into two(100GB for OsX  and 270GB as new partition.

Then used Ubuntu 9.10 CD to boot the system. Followed the initial screens, and selected the option "install on a specific drive". I forgot the actual name of that option. But it allows you pick the exact drive you want install Ubuntu. There I picked the new partition I made in OsX. choose to create a small partition out of it for using as swap. I made 8GB for swap from the free area at the end of drive. Choose that as linux swap.

Next choose the other area (262GB partition)   and formatted that in JFS format. Then choose that for ubuntu install. The rest went pretty straight. Then  it will ask whether to import boot loading option for other OS. I choose to import windows boot to be handled by GRUB. 

Then restarted the machine. It went into Mac by default. if you press option key down then it will show windows and Mac drives. But when I select windows, Linux grub will load and ask for choosing ubuntu or Windows. And you can boot any one of the os from that menu.

Then I went back to Mac and installed rEFIt. After two reboots it shows all three OS's and I when I choose windows the Ubuntu grub loads and ask to choose windows or ubuntu. So unknowingly I made an option for double selection. In Ubuntu 9 everything except sound worked. Then I updated the OS (using software update in Ubuntu) to Ubuntu 10 and everything including sound worked.

So there you go. Its very simple. I am a newbie. If I managed to get this thing up, then for Guru's it must be easy.

panachippara, The fact is that you were using Karmic (9.10). In Karmic, this all worked dandy. There was a /dev/sda3 option in the installer that you could use to install GRUB. This no longer seems to be the case with Lucid (10.04), the version of Ubuntu that this thread is about, where one's only option appears to be to install GRUB to the root of the hard drive(/dev/sda), which on a Mac can permanently break things. Please read all the other posts in the thread before posting.

---

### Post by jacques4x4 on 2010-05-02
> Why dont you upgrade to 10.04 from the update manager of version 9.10? Upgrade works perfect. May be your problem come from attempt to install fresh from CD. Please excuse if it sounds ignorant. 

Certainly not ignorant..  gave that a try and Grub was borked..  Xxander is giving that a try again right now..  

Fingers crossed we can find a reliable solution.

---

### Post by Zannek on 2010-05-02
> **panachippara said:**
> Why dont you upgrade to  10.04 from the update manager of version 9.10?  Upgrade works perfect. May be your  problem come from attempt to install fresh from CD. Please excuse if it sounds ignorant.

The problem is that upgrading does **_not_** always work perfect. If you read some earlier posts in this thread, you'll see that some users already are trying this method, and it may turn out to be a suitable work-around. However, this has not been established as working just yet.

---

### Post by panachippara on 2010-05-02
> **Zannek said:**
> panachippara, The fact is that you were using Karmic (9.10). In Karmic, this all worked dandy. There was a /dev/sda3 option in the installer that you could use to install GRUB. This no longer seems to be the case with Lucid (10.04), the version of Ubuntu that this thread is about, where one's only option appears to be to install GRUB to the root of the hard drive(/dev/sda), which on a Mac can permanently break things. Please read all the other posts in the thread before posting.

That is what I mean exactly. Why dont you guys use Karmic first and then update to Lucid using the update option in a working karmic? The Update runs overnight, but works without problems. I agree that this is not as direct as installing fresh from CD.  I did read all other post and though that at least some people may want to choose this as a solution. Anyway sorry if this was out of place.

---

### Post by WindPower on 2010-05-03
I have wiped my whole disk, reinstalled OS X and rEFIt, and reinstalled Kubuntu 10.04 without problems (with Grub on the Linux partition, /dev/sda3 in my case). For people who want a reasonably quick solution and don't mind wiping their whole drive, here's a solution.

---

### Post by NeddyDownUnder on 2010-05-03
**How I installed Ubuntu 10.4 LTS Desktop Edition on a Macbook 6,1 along with OS X and Win 7.**

Hi all,

**EDIT: Be sure to backup first... I imaged my HD before attempting the install. And I needed it once!**

I'm not an expert or anything, this is just how I did it, there may be better ways etc, but this worked for me. It's not all my own work, many of the steps below I found somewhere on Google  or this forum etc.. at some point. I'm just putting them all together.

I'm currently running a Macbook 6,1 triple booting OS X, Ubuntu 10.4 LTS Desktop Edition and Win7. I'm relatively new to Linux but I'm going to attempt to walk you guys through how I did it. Most of the stuff should also work if you only want to boot OS X and Ubuntu... **EDIT:APPARENTLY NOT - For feedback in this thread it appears this method only works when Win7 is also installed...**

Before I start, I have noticed in this thread people asking which device to install the GRUB onto. i.e. should I install on /dev/sda2 or /dev/sda3...Firstly I didn't install GRUB on /dev/sda, it's not how I wanted my setup to run, and I'm not sure if it would work anyway... Secondly, where you install GRUB will depend on your configuration i.e. how many partitions you have, and which one Ubuntu is installed on etc... No one can just tell you where to install GRUB (excuse me if this is obvious to some). That being said I will show you how I figured out  where to install GRUB on my Macbook (basically you want to install GRUB on the same partition as you install Ubuntu, below is a full description of how I did it.)

Alright, here we go...:D

I'm going to assume we're starting from a clean install of OS X installed on a hard drive with a single partition. (You can't run Bootcamp if you already have multiple partitions.)

1. Boot into OS X and install rEFIt.

2. Run Bootcamp setup assistant and create a partition large enough for both Windows 7 and Ubuntu operating systems - If you are just installing Ubuntu then just partition off your desired space for Ubuntu. Obviously the installation of Windows 7 is optional.

3. Install Windows 7, including Bootcamp drivers and updates (As I said Win7 is optional...)

4. Run Ubuntu 10.4 LTS live CD and use **Gparted** to: (be sure you have selected your HD to preform the following to - in general it's best not to have any external media such as removable HD's plugged in when you are doing this to save confusion and unwanted mistakes - I'm talking from experience)[INDENT]When I did this step I was careful not to disrupt the small amount of free  space that Bootcamp leaves between the OS X partition and the Bootcamp  partition. I know Bootcamp allows a GPT to contain a MBR somewhere and I  don't know where, I could be way off base in thinking that the free  space between the two partitions contains the MBR, but after Googleing a  bit I couldn't find any info as to where the MBR is stored so I choose  not to touch that free space. I'm not sure if this makes any difference.  It's just what I did and my  install works. If anyone has any info on this I'd be keen to hear it.
[B]
Skip to the second step of this section if you are not installing Win7.
[/B]**1.** Firstly I resized my Windows 7 partition(BOOTCAMP partition) using Gparted's 'Resize' feature. Resize the Win7 partition to the size you desire for Win7... (Note: Keep the Windows partition as the first partition after OS X, this is because the MBR only recognises the first 4 partitions of the disk.)
[B]
2.[/B] This step will differ if you are only installing Ubuntu. (note I have not done this, I'm just going by how I think it will work, should be fine.) Firstly determine what Swap size you want to have.  Some documentation says to allocate a  Swap space double the size of your RAM, however I have read in other  sources that this is outdated given the size of RAM these days.  Personally I allocated a Swap space slightly larger that my RAM to allow  for hibernation. I.e. I have 4GB of RAM so i chose a 5GB swap. Either  do your own research or use my method to determine you Swap size, I'm  far from an expert when it comes to choosing a Swap size... 

Now follow the next step below depending on whether or not you have installed Win7.
**With Win7**
Now you should have a Windows 7 partition that is the size you desire and a bunch of free space after it. What we are going to do now is make two partitions out of this free space, one for Ubuntu and another as a Swap area for Ubuntu. In Gparted select the free space after the Win7 partition and click the new button to create a new partition. A window will pop up allowing you to select the format of the new partition. I selected ext4. Now select the field that says 'Free Space Following' and enter in the amount that you would like to leave free for you Swap partition. Click ok. Now select the free space that you have remaining and click the 'New' button again to create another partition. This time select the 'linux-Swap' format, no need to adjust the size this time as this should be your last partition and thus you want it to take up the remaining space on your disk. Click the apply button to apply the changes. After the changes apply you can set the Partition Labels under the 'Partition' menu, **Partition>Label**. Do this if you want, but leave the 'BOOTCAMP' as is. I named my Ubuntu ext4 partition 'Ubuntu'...


**EDIT: I don't think these instructions are working for people after reading feedback in this thread so if you are installing just Ubuntu with OS X then you may want to look to other posts in this thread.**

[COLOR="Red"]**Without Win7** 
Select the 'BOOTCAMP' partition and resize it using the 'Resize' feature so that you can make room for a Swap area (A I said above, I was careful not to disturb the space between the Bootcamp and OS X partitions.). Click apply. After the partition has been resized format it for Linux, this can be done in the 'Partition' menu **Partition>Format to>ext4**, I choose ext4. Then select the free space at the end of the disk that you left for your Swap space and click 'New' and choose the 'linux-Swap' format, click ok. Now apply the changes. After the changes apply you can set the Partition Labels under the  'Partition' this can be done in the 'Partition' menu **Partition>Label**, menu heading in Gparted. Do this if you want, you could rename the 'BOOTCAMP' to 'Ubuntu' if you want.[/COLOR] 

[B]
After this step you should have all your required partitions for all of the operating systems that you intend to run.[/B]
[/INDENT]5. Now reboot, in the rEFIt menu at boot-up select the rEFIt partition tool. It should prompt you to let it sync the EFI and MBR tables. Allow it to do this.

6. Now we are going to install Ubuntu:[INDENT]1. Boot the Ubuntu CD and select 'Install Ubuntu'
2. Select the options that suit you until you reach step 4.
3. When you reach the screen to select where to install Ubuntu (step 4) select the option to 'Specify partitions manually' 
4. Now you are at the 'Prepare partitions' page, there is a table describing all of the partitions on your hard disk (and any other removable media you have plugged in, best not to have any this other media such as external HD's plugged in to save confusion)
5. Select the partition that you have formated for Linux, this can be identified by the format of the partition. In my case I selected the ext4 partition.
6. Once your Linux partition is selected click the 'Change' button at the bottom of the table.
7. The 'Edit partition' window will pop up. Under the field 'Use as' select the format that you previously formated this partition to, in my case I choose ext4. After this specify the 'Mount point' as** ' / '** which is the root directory where Ubuntu will be installed. There is also a field called 'Format the partition' you **don't** need to tick this. Now click ok.
8. Now select the partition that is formatted as 'swap' and click the change button and ensure that the filed 'Use as' is set to 'swap area'. Click ok.
9. At this point write down the location of the partition you have market to install Ubuntu on. This is the partition you marked to be used as the root directory ( ' / ' ). i.e. I think mine was '/dev/sda4'. ' (We will use this later to select which device to install GRUB onto.) 
10. Click forward and enter your details etc... click 'Forward'...
11. Now you should be at step 8 with the option to install as well as an 'Advanced' button. Click the 'Advanced' button and now select to install grub on the same partition that you choose as your root directory (the device you wrote down in step nine of this section.) I selected '/dev/sda4'. The actual device will differ depending on how many partitions you have etc... Once you have selected to install the GRUB on the same partition as Ubuntu click ok and then click install. :D
12. After my install the reboot fails with a bunch of I/O errors from the cd drive I just held down the power button to force a shut down when this happens

[/INDENT]7. Now reboot and at the rEFIt menu again select the 'Partition tool' and update the GPT and MBR tables if prompted to do so.

8. Now boot into Ubuntu 10.4 LTS Desktop Edition from the rEFIt menu!!!

9. After I booted Lucid I did need to make a few adjustments to get it running nicely, this will differ depending on what flavour of Mac you own, this page helped me: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) , I used the 'Karmic' pages as not many have been created for Lucid yet (just apply the fixes selectively under Lucid as some Karmic fixes are not needed in Lucid). 

One particular difference between Karmic and Lucid for my 'Macbook 6,1' was the sound fix. I found that for me the sound was working out of the box, the front speakers were just muted. I found that I had to adjust the 'Alsamixer' settings from terminal to get sound.  I did this by:[INDENT]Opening terminal ([B]Applications>Accessories>Terminal)
 [/B]then:

```
neddy@Linux-Mac:~$ alsamixer
```Then use the arrow keys to select the different devices and press 'm' to toggle mute. I un-muted the front speakers and the surround speakers and set both volumes to max and my sound works perfectly.

I also did a fix to reboot properly, the page I linked above walked me through that, just navigate to the page for your Macbook version and selectively apply fixes where needed... ( [https://help.ubuntu.com/community/MacBook )]("https://help.ubuntu.com/community/MacBook")

One thing that I have yet to get working correctly is my DVD drive... 

[/INDENT]Well, that should be it... (Hopefully I didn't miss anything...)

I hope this helps someone, it was a bit longer that I anticipated... Any feedback is appreciated as I'm only new to Ubuntu and Linux and this is my first real post on the Ubuntu Forums.
 
Good Luck

---

### Post by Zannek on 2010-05-03
> **NeddyDownUnder said:**
> **How I installed Ubuntu 10.4 LTS Desktop Edition on a Macbook 6,1 along with OS X and Win 7.**

Hi all,

**EDIT: Be sure to backup first... I imaged my HD before attempting the install. And I needed it once!**

I'm not an expert or anything, this is just how I did it, there may be better ways etc, but this worked for me. It's not all my own work, many of the steps below I found somewhere on Google  or this forum etc.. at some point. I'm just putting them all together.

I'm currently running a Macbook 6,1 triple booting OS X, Ubuntu 10.4 LTS Desktop Edition and Win7. I'm relatively new to Linux but I'm going to attempt to walk you guys through how I did it. Most of the stuff should also work if you only want to boot OS X and Ubuntu...

Before I start, I have noticed in this thread people asking which device to install the GRUB onto. i.e. should I install on /dev/sda2 or /dev/sda3...Firstly I didn't install GRUB on /dev/sda, it's not how I wanted my setup to run, and I'm not sure if it would work anyway... Secondly, where you install GRUB will depend on your configuration i.e. how many partitions you have, and which one Ubuntu is installed on etc... No one can just tell you where to install GRUB (excuse me if this is obvious to some). That being said I will show you how I figured out  where to install GRUB on my Macbook (basically you want to install GRUB on the same partition as you install Ubuntu, below is a full description of how I did it.)

Alright, here we go...:D

I'm going to assume we're starting from a clean install of OS X installed on a hard drive with a single partition. (You can't run Bootcamp if you already have multiple partitions.)

1. Boot into OS X and install rEFIt.

2. Run Bootcamp setup assistant and create a partition large enough for both Windows 7 and Ubuntu operating systems - If you are just installing Ubuntu then just partition off your desired space for Ubuntu. Obviously the installation of Windows 7 is optional.

3. Install Windows 7, including Bootcamp drivers and updates (As I said Win7 is optional...)

4. Run Ubuntu 10.4 LTS live CD and use **Gparted** to: (be sure you have selected your HD to preform the following to - in general it's best not to have any external media such as removable HD's plugged in when you are doing this to save confusion and unwanted mistakes - I'm talking from experience)[INDENT]When I did this step I was careful not to disrupt the small amount of free  space that Bootcamp leaves between the OS X partition and the Bootcamp  partition. I know Bootcamp allows a GPT to contain a MBR somewhere and I  don't know where, I could be way off base in thinking that the free  space between the two partitions contains the MBR, but after Googleing a  bit I couldn't find any info as to where the MBR is stored so I choose  not to touch that free space. I'm not sure if this makes any difference.  It's just what I did and my  install works. If anyone has any info on this I'd be keen to hear it.
[B]
Skip to the second step of this section if you are not installing Win7.
[/B]**1.** Firstly I resized my Windows 7 partition(BOOTCAMP partition) using Gparted's 'Resize' feature. Resize the Win7 partition to the size you desire for Win7... (Note: Keep the Windows partition as the first partition after OS X, this is because the MBR only recognises the first 4 partitions of the disk.)
[B]
2.[/B] This step will differ if you are only installing Ubuntu. (note I have not done this, I'm just going by how I think it will work, should be fine.) Firstly determine what Swap size you want to have.  Some documentation says to allocate a  Swap space double the size of your RAM, however I have read in other  sources that this is outdated given the size of RAM these days.  Personally I allocated a Swap space slightly larger that my RAM to allow  for hibernation. I.e. I have 4GB of RAM so i chose a 5GB swap. Either  do your own research or use my method to determine you Swap size, I'm  far from an expert when it comes to choosing a Swap size... 

Now follow the next step below depending on whether or not you have installed Win7.
**With Win7**
Now you should have a Windows 7 partition that is the size you desire and a bunch of free space after it. What we are going to do now is make two partitions out of this free space, one for Ubuntu and another as a Swap area for Ubuntu. In Gparted select the free space after the Win7 partition and click the new button to create a new partition. A window will pop up allowing you to select the format of the new partition. I selected ext4. Now select the field that says 'Free Space Following' and enter in the amount that you would like to leave free for you Swap partition. Click ok. Now select the free space that you have remaining and click the 'New' button again to create another partition. This time select the 'linux-Swap' format, no need to adjust the size this time as this should be your last partition and thus you want it to take up the remaining space on your disk. Click the apply button to apply the changes. After the changes apply you can set the Partition Labels under the 'Partition' menu, **Partition>Label**. Do this if you want, but leave the 'BOOTCAMP' as is. I named my Ubuntu ext4 partition 'Ubuntu'...

**Without Win7**
Select the 'BOOTCAMP' partition and resize it using the 'Resize' feature so that you can make room for a Swap area (A I said above, I was careful not to disturb the space between the Bootcamp and OS X partitions.). Click apply. After the partition has been resized format it for Linux, this can be done in the 'Partition' menu **Partition>Format to>ext4**, I choose ext4. Then select the free space at the end of the disk that you left for your Swap space and click 'New' and choose the 'linux-Swap' format, click ok. Now apply the changes. After the changes apply you can set the Partition Labels under the  'Partition' this can be done in the 'Partition' menu **Partition>Label**, menu heading in Gparted. Do this if you want, you could rename the 'BOOTCAMP' to 'Ubuntu' if you want.
[B]
After this step you should have all your required partitions for all of the operating systems that you intend to run.[/B]
[/INDENT]5. Now reboot, in the rEFIt menu at boot-up select the rEFIt partition tool. It should prompt you to let it sync the EFI and MBR tables. Allow it to do this. 

6. Now we are going to install Ubuntu:[INDENT]1. Boot the Ubuntu CD and select 'Install Ubuntu'
2. Select the options that suit you until you reach step 4.
3. When you reach the screen to select where to install Ubuntu (step 4) select the option to 'Specify partitions manually' 
4. Now you are at the 'Prepare partitions' page, there is a table describing all of the partitions on your hard disk (and any other removable media you have plugged in, best not to have any this other media such as external HD's plugged in to save confusion)
5. Select the partition that you have formated for Linux, this can be identified by the format of the partition. In my case I selected the ext4 partition.
6. Once your Linux partition is selected click the 'Change' button at the bottom of the table.
7. The 'Edit partition' window will pop up. Under the field 'Use as' select the format that you previously formated this partition to, in my case I choose ext4. After this specify the 'Mount point' as** ' / '** which is the root directory where Ubuntu will be installed. There is also a field called 'Format the partition' you **don't** need to tick this. Now click ok.
8. Now select the partition that is formatted as 'swap' and click the change button and ensure that the filed 'Use as' is set to 'swap area'. Click ok.
9. At this point write down the location of the partition you have market to install Ubuntu on. This is the partition you marked to be used as the root directory ( ' / ' ). i.e. I think mine was '/dev/sda4'. ' (We will use this later to select which device to install GRUB onto.) 
10. Click forward and enter your details etc... click 'Forward'...
11. Now you should be at step 8 with the option to install as well as an 'Advanced' button. Click the 'Advanced' button and now select to install grub on the same partition that you choose as your root directory (the device you wrote down in step nine of this section.) I selected '/dev/sda4'. The actual device will differ depending on how many partitions you have etc... Once you have selected to install the GRUB on the same partition as Ubuntu click ok and then click install. :D
12. After my install the reboot fails with a bunch of I/O errors from the cd drive I just held down the power button to force a shut down when this happens

[/INDENT]7. Now reboot and at the rEFIt menu again select the 'Partition tool' and update the GPT and MBR tables if prompted to do so.

8. Now boot into Ubuntu 10.4 LTS Desktop Edition from the rEFIt menu!!!

9. After I booted Lucid I did need to make a few adjustments to get it running nicely, this will differ depending on what flavour of Mac you own, this page helped me: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) , I used the 'Karmic' pages as not many have been created for Lucid yet (just apply the fixes selectively under Lucid as some Karmic fixes are not needed in Lucid). 

One particular difference between Karmic and Lucid for my 'Macbook 6,1' was the sound fix. I found that for me the sound was working out of the box, the front speakers were just muted. I found that I had to adjust the 'Alsamixer' settings from terminal to get sound.  I did this by:[INDENT]Opening terminal ([B]Applications>Accessories>Terminal)
 [/B]then:

```
neddy@Linux-Mac:~$ alsamixer
```Then use the arrow keys to select the different devices and press 'm' to toggle mute. I un-muted the front speakers and the surround speakers and set both volumes to max and my sound works perfectly.

I also did a fix to reboot properly, the page I linked above walked me through that, just navigate to the page for your Macbook version and selectively apply fixes where needed... ( [https://help.ubuntu.com/community/MacBook )]("https://help.ubuntu.com/community/MacBook")

One thing that I have yet to get working correctly is my DVD drive... 

[/INDENT]Well, that should be it... (Hopefully I didn't miss anything...)

I hope this helps someone, it was a bit longer that I anticipated... Any feedback is appreciated as I'm only new to Ubuntu and Linux and this is my first real post on the Ubuntu Forums.
 
Good Luck

I still don't think this quite solves the problem. Whatever we choose to make the ubuntu partition (mount point: /), it _**DOESN'T APPEAR**_ under "Advanced options" as a selectable drive to install GRUB to. I am quite convinced that somewhere between Karmic and Lucid, the installer itself has been broken in this department. It seems a lot of people are confused as to what the actual issue is here. It's not that we're all luddites who can't figure out our way around the installer, it's that the installer simply doesn't behave like it used to!

---

### Post by NeddyDownUnder on 2010-05-03
> **Zannek said:**
> I still don't think this quite solves the problem. Whatever we choose to make the ubuntu partition (mount point: /), it _**DOESN'T APPEAR**_ under "Advanced options" as a selectable drive to install GRUB to. I am quite convinced that somewhere between Karmic and Lucid, the installer itself has been broken in this department. It seems a lot of people are confused as to what the actual issue is here. It's not that we're all luddites who can't figure out our way around the installer, it's that the installer simply doesn't behave like it used to!

Are you sure the partition does not appear for you under the advanced option as it did for me... It's how I installed it and I'm using it now. I noticed that it will not let you select a partition to install GRUB on if you have just created that partition with the installer's partition tool. But you can select it if you first create the partition using Gparted... 

 I was NOT implying that you or anyone else is a luddite, but rather I was just try to give you a comprehensive solution that HAS worked for me.

Good Luck.

---

### Post by amsterdamharu on 2010-05-03
Hold on here, NeddyDownUnder are you saying that when you use gparted to create the swap and root partition and during setup choose 'Specify partitions manually' instead of “largest continuous free space” the option to install grub on /dev/sda? returns?

Than this would be the solution. 
Since everyone probably uses the documentation here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
Everyone uses the “largest continuous free space” and that option might have a bug later on in the process that does not allow you to install grub.

Another option that might work is skipping installing grub (not sure if this is possible) and after install boot with a live CD and install grub on that partition with the force option (this should in theory just mess up your /dev/sda? boot record and leave the rest in tact).

It might also have something todo with ext4, NeddyDownUnder selected ext4. Did you guys who have problems selected ext4 as well?

---

### Post by Zannek on 2010-05-03
> **NeddyDownUnder said:**
> Are you sure the partition does not appear for you under the advanced option as it did for me... It's how I installed it and I'm using it now. I noticed that it will not let you select a partition to install GRUB on if you have just created that partition with the installer's partition tool. But you can select it if you first create the partition using Gparted... 

 I was NOT implying that you or anyone else is a luddite, but rather I was just try to give you a comprehensive solution that HAS worked for me.

Good Luck.

My sincerest apologies. At first glance late at night, it looked like you were describing the generic installation instructions for a Mac. Now that I understand what you've done, I have to say thank you, because you've actually found a successful workaround for this irritating bug.

After using gParted to create my partitions instead of the partitioner contained within the installer, and simply selecting the appropriate partition to mount at "/", the partitions now show up under the "Advanced" options, allowing me to install Grub to my Ubuntu partition. 

You sir, have saved me from a lot of trouble at uni (I needed Ubuntu for something important). I'm sorry for ranting with the "luddite" bit, but myself and others have been given false (rather, uninformed) guidance at every turn since trying to resolve this issue, and I've had to completely reformat my drive to fix the errors that have been generated by this false information.

Until this bug gets fixed, someone should post this information somewhere noticeable.

---

### Post by jacques4x4 on 2010-05-03
NeddyDownUnder-- You nailed it.   Thank you..  Interestingly enough to get this to work I had to install Windows 7  ... I crashed and burned just trying to install Ubuntu without Windows 7.

thank you,

Jacques4x4

---

### Post by xxander on 2010-05-03
I posted a while back that I would try uprading from 9.10 to 10.04 within the Ubuntu OS... it failed... the GRUB-PC thing just sits there with an error.  Jacques 4x4, I;m glad it worked for you.  I am also going to try to do it with just ubuntu (even though it failed for you).  Then I will install Win7 if that goes badly.  

I hope everybody has a good day and gets Ubuntu to work... I won't be able to install until this weekend... :(

And thanks the Neddy!  Your description is very thorough!

---

### Post by Zannek on 2010-05-05
> **xxander said:**
> I posted a while back that I would try uprading from 9.10 to 10.04 within the Ubuntu OS... it failed... the GRUB-PC thing just sits there with an error.  Jacques 4x4, I;m glad it worked for you.  I am also going to try to do it with just ubuntu (even though it failed for you).  Then I will install Win7 if that goes badly.  

I hope everybody has a good day and gets Ubuntu to work... I won't be able to install until this weekend... :(

And thanks the Neddy!  Your description is very thorough!

There shouldn't be any need to install Windows 7 (is there ever? :P) I simply used the Live CD environment to run gParted, which allowed me to make my necessary partitions as I usually would with the manual mode of the installer. Then, run the installer from the icon on the desktop, go thru the steps as normal, and assign the newly made partitions to where they should be mounting to, as well as telling the installer to put GRUB on the appropriate Ubuntu partition. 

If anyone needs, I can do a step-by-step like Neddy did, sans Windows 7.

---

### Post by Nikos.Alexandris on 2010-05-05
> **WindPower said:**
> I have exactly the same problem. I wouldn't date try to install GRUB on /dev/sda. That's a recipe for even further computer suicide.

Was _not_ for me. Quite the opposite, trying 3 times to install on sda3 ended up with a broken grub. I would recommend you to try it! As usual, no warranty! Needless to say, make your Backup before anything else.

Regards

EDIT: before I add more to the confusion, what I successfully installed on **sda** was Kubuntu Karmic 64-bit, not Lucid. I am still waiting to see a "verification" post that the upgrade will work and wont touch grub.

EDIT2: reading some posts above I understand that it is important to provide more details: I too specified manually the partitions ( a "/", a "home" and another one for data) - yet, I did not see any option except **sda**... this is strange!??

---

### Post by Nikos.Alexandris on 2010-05-05
> **WindPower said:**
> I have wiped my whole disk, reinstalled OS X and rEFIt, and reinstalled Kubuntu 10.04 without problems (with Grub on the Linux partition, /dev/sda3 in my case). For people who want a reasonably quick solution and don't mind wiping their whole drive, here's a solution.

Hmmm... that is really strange (because, as I already posted, I installed Kubuntu on **sda**) -- I really would like to understand the grub-background but don't have the required free-time to do my homework.

Cheers

---

### Post by jacques4x4 on 2010-05-06
In one of my many attempts to install 10.04 I tried the sda option.. I ended up trashing my first partition and I had to reformat the drive and reinstall OS X.  I could boot into OS X but only by holding down the option key.  

This is my installation solution  and you all are welcome to refine the process:

As always a current backup is critical as your mileage may vary..   



1.	Install rEFit first and make sure it is working.  You will have to start your Mac twice before it shows up.
2.	In OS X use Bootcamp to make a Windows partition; make this the size you want for Ubuntu and your swap.  I chose 40 gigs. 
3.	After that, boot the Ubuntu 10.04 live CD, start the partition editor, gparted..  Its under System > Administration.   
4.	Use gparted to delete the partition you made in OS X.  It should be the last partition on the disk as it follows the HFS+ partition (OS X).  Still using gparted make a new primary partition; for the file system choose NTFS;  for the label type in BOOTCAMP.  There is no need for space between your HFS+ partition and this one..  I chose the new size to be 512 MiB.   Apply the changes and exit gparted. . 
5.	Start the Ubuntu 10.04 installer from the desktop; when it asks you to prepare the disk space choose specify partitions manually.
6.	Select the partition you just created it should be /dev/sda3 > choose change > use as NTFS> check format > mount point = /windows > select ok.
7.	In the free space choose add, in the new partition size adjust it down so you have room for a swap file.  I shrunk it down by 4096.  (4 gigs).  > Use as Ext4 >  mount point = /    click ok.
8.	In the remaining free space choose add > use as swap > check ok.
9.	If your system is like mine you will soon have these partitions, sda1  (the EFI partition), sda2 (the OS X partition) sda3 (the NTFS partition), sda4 (the Ext4 Ubuntu partition) and sda5 (your swap partition).
10.	 When you arrive at step 8 the last dialogue box of the installer before you commit to all of this select the advanced button and choose to install the grub boot loader to /dev/sda3  Your NTFS partition.   Rock and roll
11.	Reboot when the install is complete and in the rEFit menu choose the partition tool and resync if necessary.   
12.	Power down your computer..  again a choice in the rEFit menu.
13.	Power up and you should be good to go..

---

### Post by beanstalker on 2010-05-06
Hi, I had an almost identical problem when installing karmic on my MBP5,3
When you use the largest free space install option, for some reason grub gets put in the wrong place (for me it created a whole new partition just for grub that wasn't bootable). The easiest solution is to just use manual partitioning and specify where you want grub.

My partition map: 

dev/sda1 efi
dev/sda2 Mac
dev/sda3 ext4 plus grub
dev/sda4 swap

Works fine.
Hope this helps.

---

### Post by jacques4x4 on 2010-05-06
I tried that first... but for some reason I was only able to boot into Lucid once... then always the second time I would get the error message "no operating system" strange.. for me grub seems to be happiest on its own tiny NTFS partition.  What I tried to do was use NeddyDownUnder's approach and make it work without Win7.. hence a tiny ntfs partition.  When I left that out I would have to boot with the live CD chroot in and force install Grub onto the Ext4 partition.  I would be only able to boot into Ubuntu once..  The tiny NTFS partition method seems to be bullet proof... and I really did not want win7

---

### Post by patg7590 on 2010-05-06
Hey everyone, I am pretty stuck. After spending days in the IRC rooms to no avail, practically getting booted out of #grub (pun intended), I finally stumbled across this. 

My Macbook Pro 4,1 has a 500GB drive that looks like this:

/dev/sda1-EFI-fat32-200mb
/dev/sda2-HFS+-OSX 10.6.3
unallocated-200mb
/dev/sda3-NTFS-WINDOWS7PROX64
/dev/sda5-ext4-UBUNTU studio x64
/dev/sda6-linux swap

Note the lack of an sda4. I don't know why this is. This is just what I see in Gparted. 

I had refit installed and working, everything worked great. 

Until the update to Lucid....

I ran update-manager -d from terminal, everything went fine. and then when I restarted...

grub: error: symbol 'image_puts_' not found

I tried booting to a Live CD to resinstall grub, followed the steps, but I cannot get it to install; 

NOTE YOU NEED A 64bit LIVE CD IF YOU WANT TO GET PAST CHROOT STEP ON 64 BIT MACHINES.

I get the error about blocklists and force. I'm a moron, so I tried force, i tried putting grub on /dev/sda4 i tried /sda. I got nowhere. Someone please help me. 

Thanks. I'm _pg_ on IRC if anyone wants to get in touch ;)

---

### Post by jacques4x4 on 2010-05-06
have you tried putting grub on your NTFS partition.. sda3 ?  

Perhaps a more important question... do you have all of your data backed up?

---

### Post by patg7590 on 2010-05-06
Not yet, which is why I don't want to reinstall, but that is next on the list, probably do that tonight. (I'm pretty sure I dodged a bullet trying to install using --force and having at least osx still work haha)

---

### Post by jacques4x4 on 2010-05-06
Good luck.. let us know how it goes... I had success putting grub on the NTFS partition.

---

### Post by patg7590 on 2010-05-06
Do you also use rEFIt? does it take you to grub from windows being selected in rEFIt and from Ubuntu? This seems like a hack which makes me think it will make it even harder to get support next update :/

---

### Post by jacques4x4 on 2010-05-06
I do. and it works well.   It is an easy install and uninstall. I used the Mac disk image.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Note that this does not appear on the first boot. you have to power down osx a couple of time..  be sure to check out the faq. 

Also after your install go to refit partition tool to be sure that you are synced up.

refit is very easy to uninstall before the "next update"

---

### Post by patg7590 on 2010-05-06
I am not communicating this very well... 

> **patg7590 said:**
> 

I had refit installed and working, everything worked great. 



I was asking if *you* were using rEFIt. I already use it without issue. I just have a botched GRUB now. Someone in IRC thought the same thing though. Perhaps I worded that poorly.

---

### Post by jacques4x4 on 2010-05-06
Perhaps I should read a bit more carefully.  :)

After you back up I do think you will be successful if you install grub to your NTFS partition..  

But do back up

---

### Post by patg7590 on 2010-05-06
The latest I'm hearing in IRC is that I should install grub to my MBR. located at (i think) /dev/sda.

I think to do this I need to run 

install-grub --force /dev/sda 

at the install step of the process. I'm not sure yet though. I still need to backup and I will post back if that works.

---

### Post by jacques4x4 on 2010-05-06
Backup before you try that.  

When I gave that a spin I had to reformat my drive and reinstall OS X.  Your mileage may vary.

---

### Post by patg7590 on 2010-05-06
I don't mind reinstalling Ubuntu, anything important there is on Dropbox but I dont even know how I would restore osx and w7 if I had to restore from a backup(s). Do I have to run bootcamp again? Do I need my windows key? That and I finally got rEFIt working, all more reasons I don't want to have to start all over.

---

### Post by jacques4x4 on 2010-05-06
OSX restores perfectly with Time Machine and a Snow Leopard install DVD.   

Use an external usb drive and Time Machine and you will have a complete backup.

Win7 is another animal.. yes you would need your install Key.  Again backup your data to an external drive.   

I personally would not risk any change until I had my data securely backed up.

---

### Post by Jordan Uggla on 2010-05-06
> **jacques4x4 said:**
> Backup before you try that.  

When I gave that a spin I had to reformat my drive and reinstall OS X.  Your mileage may vary.

That sounds like a **very** serious bug, did you report it?

What version of Ubuntu/GRUB did this happen with, and what exactly happened when you tried to boot afterward that required you to re-install OSX?

---

### Post by jacques4x4 on 2010-05-06
Grub installed it self on sda1 my EFI partition hence my need to reinstall OS X.  The distribution I am using is  Ubuntu 10.04.

I could boot to my OSX partition by holding down the option key. 

I recovered by booting with the OSX installer DVD, going into the disk utility and then reformatting the drive with a GUID partition table.. then using the Time Machine backup/restore utility on the OSX install disk I restored my OS and data.   


Be sure to read through the entire thread.  I am certainly not an expert user by any means and some of the folks in this thread are more knowledgeable than I am. 

No I did not report this as a bug, I don't feel qualified to make that call.  

I am just recounting my experiences.. both failures and successes.

I have just learned to keep Grub away from sda1 at any cost.. at least in my case.

---

### Post by WindPower on 2010-05-06
> **Jordan Uggla said:**
> That sounds like a **very** serious bug, did you report it?

What version of Ubuntu/GRUB did this happen with, and what exactly happened when you tried to boot afterward that required you to re-install OSX?

This has always been a "bug" on Macbook (Pro)'s, you can't let the installer do the default action of installing GRUB/GRUB2 to /dev/sda because it ruins the GPT part of the disk and you end up with a non-working dual-boot. It's mentioned in all the installation methods at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I'm not sure this has changed in Lucid, but if the guys on IRC say so, then give it a shot. :o

---

### Post by jacques4x4 on 2010-05-06
> I'm not sure this has changed in Lucid, but if the guys on IRC say so, then give it a shot. 

Be sure to back up first..    

I am not convinced that the installer is smart enough to choose the correct partition on sda ..  and if it does choose sda1 you will need to reinstall.

---

### Post by newbie80 on 2010-05-10
Followed the instructions posted by [NeddyDownUnder]("http://ubuntuforums.org/member.php?u=1046785"), was able to install lucid (triple boot with osx and win7) without any glitches on mbp 6.2. Infact I forgot to partition for the swap drive but installation took care of it and allocated 5.6 GB (8 GB ram). Followed the wiki page for macbookpro 6.2 for making other things work.

---

### Post by kwatson on 2010-05-10
I was able to get it to work by sticking GRUB on the partition where linux is installed.

My setup:

MacPro
2 HD's, 2nd hd is being used by ubuntu, first is for mac.

At the end of 10.04 installation, make sure to click on advanced and have grub installed to the partition where linux is installed -- NOT on the entire HD.

You may need to re-install grub by using the liveCD after installation...just use --force to get it into the linux partition. (ex: grub-install /dev/sdb2 --force)

---

### Post by jamesixgun on 2010-05-11
> **jacques4x4 said:**
> In one of my many attempts to install 10.04 I tried the sda option.. I ended up trashing my first partition and I had to reformat the drive and reinstall OS X.  I could boot into OS X but only by holding down the option key.  

This is my installation solution  and you all are welcome to refine the process:

As always a current backup is critical as your mileage may vary..   



1.    Install rEFit first and make sure it is working.  You will have to start your Mac twice before it shows up.
2.    In OS X use Bootcamp to make a Windows partition; make this the size you want for Ubuntu and your swap.  I chose 40 gigs. 
3.    After that, boot the Ubuntu 10.04 live CD, start the partition editor, gparted..  Its under System > Administration.   
4.    Use gparted to delete the partition you made in OS X.  It should be the last partition on the disk as it follows the HFS+ partition (OS X).  Still using gparted make a new primary partition; for the file system choose NTFS;  for the label type in BOOTCAMP.  There is no need for space between your HFS+ partition and this one..  I chose the new size to be 512 MiB.   Apply the changes and exit gparted. . 
5.    Start the Ubuntu 10.04 installer from the desktop; when it asks you to prepare the disk space choose specify partitions manually.
6.    Select the partition you just created it should be /dev/sda3 > choose change > use as NTFS> check format > mount point = /windows > select ok.
7.    In the free space choose add, in the new partition size adjust it down so you have room for a swap file.  I shrunk it down by 4096.  (4 gigs).  > Use as Ext4 >  mount point = /    click ok.
8.    In the remaining free space choose add > use as swap > check ok.
9.    If your system is like mine you will soon have these partitions, sda1  (the EFI partition), sda2 (the OS X partition) sda3 (the NTFS partition), sda4 (the Ext4 Ubuntu partition) and sda5 (your swap partition).
10.     When you arrive at step 8 the last dialogue box of the installer before you commit to all of this select the advanced button and choose to install the grub boot loader to /dev/sda3  Your NTFS partition.   Rock and roll
11.    Reboot when the install is complete and in the rEFit menu choose the partition tool and resync if necessary.   
12.    Power down your computer..  again a choice in the rEFit menu.
13.    Power up and you should be good to go..

THANK YOU! THANK YOU! THANK YOU! This worked perfectly! And I'm now the proud owner of a MacBook 1,1 dual-booting 10.5.8 and 10.04. Woo!

And for anyone else with the vexing GRUB issues, these are the instructions to follow. Or, rather, they worked for me on my revA mb. 

And thanks again, jacques! You rock.

Now off to find a way to adjust the screen brightness. I'm about to go blind.

---

### Post by jacques4x4 on 2010-05-11
:P  Glad it worked for you..

---

### Post by NeddyDownUnder on 2010-05-12
Hi Everyone,

Just thought I would let you guys know that I edited my previous post to reflect the feedback in this thread stating that my method appears to only work if you are installing Win7 and Ubuntu with OS X.

Cheers

---

### Post by patg7590 on 2010-05-13
I got it working!

Here's how I did it. 

booted to a live 10.04 Ubuntu [COLOR="Red"]**x64**[/COLOR] cd (very important if you have a 64bit install. (otherwise you can't chroot. dont know why)

open a terminal

sudo fdisk -l gave me
/dev/sda1 gpt
/dev/sda2 osx
/dev/sda3 win7
/dev/sda4 ubuntu

(I paraphrase the output of course)

but it was not true! I installed gparted on the live cd and it showed that i didn't really have /dev/sda4 and that ubuntu was located on /dev/sda5!!!

so I proceeded to reinstall grub, and when I got to

sudo-install /dev/sda

I had to use

sudo-install --force /dev/sda

and then ran sudo update-grub again for good measure.

Now my osx, ubuntu, and win7 installs all work again from rEFIt! I'm so happy. 

(no guarantees this will work for any other setup than mine. back up all your important data before trying anything drastic like this)

---

### Post by linux-hack on 2010-05-13
I had the same problem instaling ubuntu on my mac, so what I dit when I saw that there is no sda3, I used gparted to make a partition sda3 and one for the swap sda4 and instaled grub on sda3 and everithing works fine :D

Hope this helps !!

---

### Post by thomas.clark on 2010-05-22
Is this:

> **jacques4x4 said:**
> 
I recovered by booting with the OSX installer DVD, going into the disk utility and then reformatting the drive with a GUID partition table.. then using the Time Machine backup/restore utility on the OSX install disk I restored my OS and data.   

necessary before doing this:

[QUOTE=jacques4x4]
1.    Install rEFit first and make sure it is working.  You will have to  start your Mac twice before it shows up.
2.    In OS X use Bootcamp to make a Windows partition; make this the  size you want for Ubuntu and your swap.  I chose 40 gigs. 
3.    After that, boot the Ubuntu 10.04 live CD, start the partition  editor, gparted..  Its under System > Administration.   
4.    Use gparted to delete the partition you made in OS X.  It should  be the last partition on the disk as it follows the HFS+ partition (OS  X).  Still using gparted make a new primary partition; for the file  system choose NTFS;  for the label type in BOOTCAMP.  There is no need  for space between your HFS+ partition and this one..  I chose the new  size to be 512 MiB.   Apply the changes and exit gparted. . 
5.    Start the Ubuntu 10.04 installer from the desktop; when it asks  you to prepare the disk space choose specify partitions manually.
6.    Select the partition you just created it should be /dev/sda3 >  choose change > use as NTFS> check format > mount point =  /windows > select ok.
7.    In the free space choose add, in the new partition size adjust it  down so you have room for a swap file.  I shrunk it down by 4096.  (4  gigs).  > Use as Ext4 >  mount point = /    click ok.
8.    In the remaining free space choose add > use as swap > check  ok.
9.    If your system is like mine you will soon have these partitions,  sda1  (the EFI partition), sda2 (the OS X partition) sda3 (the NTFS  partition), sda4 (the Ext4 Ubuntu partition) and sda5 (your swap  partition).
10.     When you arrive at step 8 the last dialogue box of the installer  before you commit to all of this select the advanced button and choose  to install the grub boot loader to /dev/sda3  Your NTFS partition.    Rock and roll
11.    Reboot when the install is complete and in the rEFit menu choose  the partition tool and resync if necessary.   
12.    Power down your computer..  again a choice in the rEFit menu.
13.    Power up and you should be good to go.. [/QUOTE]

???

I'm backed up and can if I have to, but I'd rather somehow just fix having installed the boot loader to /dev/sda without wiping it all clean.

---

### Post by NeddyDownUnder on 2010-05-23
**@ thomas.clark**

If I understand you correctly you installed Grub to /dev/sda and you want to fix it..

**EDIT: <snip> Look below to wford002's post...**

---

### Post by jacques4x4 on 2010-05-23
@ thomas.clark

> Is this:  ..... > necessary before doing this:

> I'm backed up and can if I have to, but I'd rather somehow just fix having installed the boot loader to /dev/sda without wiping it all clean.

Thomas... I am sorry to say it was for me..

Jacques4x4

---

### Post by thomas.clark on 2010-05-23
Okay, thanks guys.  Will continue to tinker and go the nuclear option if necessary.  Thanks for providing the How To!

---

### Post by jacques4x4 on 2010-05-23
If you find a way around the "nuclear option" please post a step by step..  I am very sure it will be useful to others in the future.

---

### Post by wford002 on 2010-05-24
Thanks to all in this thread, it helped me install grub to the correct partition (/dev/sda3) by doing the manual partition method. 

Afterwards, however, ubuntu still would not boot since there was an old version of grub from an earlier install on /dev/sda. In order to fix the mbr I took a chance on these instructions (there was a scary warning), and am very happy that it worked:

[http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot)

Basically after i installed I could only boot to OSX or a grub menu, but this fixed the problem. Hopefully, this can help others avoid the nuclear option.

---

### Post by jacques4x4 on 2010-05-24
> **wford002 said:**
> Thanks to all in this thread, it helped me install grub to the correct partition (/dev/sda3) by doing the manual partition method. 

Afterwards, however, ubuntu still would not boot since there was an old version of grub from an earlier install on /dev/sda. In order to fix the mbr I took a chance on these instructions (there was a scary warning), and am very happy that it worked:

[http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot)

Basically after i installed I could only boot to OSX or a grub menu, but this fixed the problem. Hopefully, this can help others avoid the nuclear option.

wow.. perhaps this and the install instructions would qualify for a sticky?  I believe this would help many mactel installers of 10.04.

---

### Post by wford002 on 2010-05-24
yeah, it's really such a simple fix, but I kinda just stumbled on it. It doesn't seem to be well known, which added to my apprehension of using it. I'm definitely glad I did though, rather than reinstall everything! Of course it may not work as well for triple boot etc...

---

### Post by thomas.clark on 2010-05-24
> **jacques4x4 said:**
> this and the install instructions would qualify for a sticky?  I believe this would help many mactel installers of 10.04.

+1 (billion)

---

### Post by andraxch on 2010-06-14
Thank you! it worked like a charm on my macbook 4,1
Beautiful-

---

### Post by linuxopjemac on 2010-06-14
I asked many times for stickies in the Apple Ubuntu forums to no avail. That's why I started my own website (mac.linux.be). If people want to add content as an editor after this thread, they are free to do so. It would be helpful for other people too. I am still on my own trying to get the best content on that site. Unfortunately people always try to solve it themselves, not looking enough at the winning ideas of the past.

---

### Post by linuxopjemac on 2010-06-14
Oops, double post, sorry.

---

### Post by JohnAtilano on 2010-06-14
> **linuxopjemac said:**
> I asked many times for stickies in the Apple Ubuntu forums to no avail. That's why I started my own website (mac.linux.be). If people want to add content as an editor after this thread, they are free to do so. It would be helpful for other people too. I am still on my own trying to get the best content on that site. Unfortunately people always try to solve it themselves, not looking enough at the winning ideas of the past.

I went through this same problem this weekend.  Ended up going the nuclear route.  Wish I would've seen your website before.

I outlined how I installed Linux Mint 9 on my blog.  This works exactly the same for Lucid.  I know because I removed Mint and installed Lucid after I posted this.  I'm not sure who is responsible for updating the MacTel "how-to's" but they are woefully inaccurate.

How I installed Linux on my MacBook Pro 5,1 is posted [here]("http://johnatilano.posterous.com/dual-boot-mac-os-x-and-linux-mint-9-on-a-macb")

---

### Post by Matt3223 on 2010-06-19
Thank you all this worked!
My situation was that I had the ol' grub on the MBR problem, but it didn't ruin everything... I could still boot OSX, however, ubuntu would not get past the grub menu upon booting with option held.

but, I had ubuntu installed and could boot to it on /dev/sda3 using superGrubDisk... so

I went to terminal in lucid and:

```

sudo grub-install --force /dev/sda3
sudo update-grub

```

after telling me how installing to a partition was a BAD idea... I shrugged and updated grub.

then booted back into OSX and followed [**wford002's**](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot) link to rewrite the MBR on disk0.

rEFIt still would not boot linux on sda3 by selecting tux icon, but rebooting and holding down option and selecting "windows" booted me into ubuntu on sda3. :)

now to copy efi folder to desktop and then delete it off Macintosh HD so I don't have to mess with it anymore... for now. ;)

---

### Post by vibe3 on 2010-06-30
So it looks like Neddy's instructions seem to work for a lot of people, but those instructions are based on a "new" install off a CD? Has anyone successfully used the update manager to upgrade from 9.10 to 10.04 and avoid the grub problem?

---

### Post by Just visiting on 2010-08-09
I just finished installing Ubuntu in addition to an existing OSX (10.6) system. The procedure on this site:
 [AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")  (wich lead me here) didn´t work, but  the procedure described by  jacques4x4 in [post #41]("http://ubuntuforums.org/showthread.php?t=1468240&page=5") did the job. I didn´t even have to resync.

So, just some grateful feedback... thx

---

### Post by chillyperson23 on 2010-08-09
You shouldnt have to use the advanced option at all. rEFTi will boot into grub either way.  At least it has on mine. it never failed unless i tried to install windows at the same time. 

Make a partition of free space with disk utility in OS X. then choose the free space option in ubuntu to avoid issues. Then rEFIt should boot into grub when you choose linux, and OS X when you choose it. but you wont be able to boot OS X from grub.

---

### Post by simeon.fm on 2010-08-10
I didn't read through the entire thread, so I can't be sure if this has been hashed out already, but I was successful installing grub to /dev/sda instead of /dev/sda3.

Sounds like a couple people have had some serious problems with that method, but I went ahead and did it without knowing what I was doing (because /dev/sda3 wouldn't work) and dual-booting with rEFIt has worked flawlessly for several days.

So, perhaps it's a a worthy attempt if you're willing to take the risk or have any idea of what you're doing (unlike me).

Good luck everyone!

---

### Post by jimla on 2010-12-12
> **simeon.fm said:**
> I didn't read through the entire thread, so I can't be sure if this has been hashed out already, but I was successful installing grub to /dev/sda instead of /dev/sda3.
Good luck everyone!
I had the same experience installing Ubuntu 10.10 on my Macbook 7,1.  The first time the installer put grub on /dev/sda and everything worked fine.  Thinking I made a mistake, I restored the MBR with the OSX install disk and reinstalled Ubuntu, putting grub on /dev/sda5, my linux root partition.  Now when I try to boot Ubuntu from rEFIt, I get a blank screen with blinking cursor!  I will try reinstalling with grub on /dev/sda.  Is there anything wrong with that?

Thanks,

Jim

---

### Post by xlollie106 on 2011-01-05
> **jacques4x4 said:**
> In one of my many attempts to install 10.04 I tried the sda option.. I ended up trashing my first partition and I had to reformat the drive and reinstall OS X.  I could boot into OS X but only by holding down the option key.  

This is my installation solution  and you all are welcome to refine the process:

As always a current backup is critical as your mileage may vary..   



1.    Install rEFit first and make sure it is working.  You will have to start your Mac twice before it shows up.
2.    In OS X use Bootcamp to make a Windows partition; make this the size you want for Ubuntu and your swap.  I chose 40 gigs. 
3.    After that, boot the Ubuntu 10.04 live CD, start the partition editor, gparted..  Its under System > Administration.   
4.    Use gparted to delete the partition you made in OS X.  It should be the last partition on the disk as it follows the HFS+ partition (OS X).  Still using gparted make a new primary partition; for the file system choose NTFS;  for the label type in BOOTCAMP.  There is no need for space between your HFS+ partition and this one..  I chose the new size to be 512 MiB.   Apply the changes and exit gparted. . 
5.    Start the Ubuntu 10.04 installer from the desktop; when it asks you to prepare the disk space choose specify partitions manually.
6.    Select the partition you just created it should be /dev/sda3 > choose change > use as NTFS> check format > mount point = /windows > select ok.
7.    In the free space choose add, in the new partition size adjust it down so you have room for a swap file.  I shrunk it down by 4096.  (4 gigs).  > Use as Ext4 >  mount point = /    click ok.
8.    In the remaining free space choose add > use as swap > check ok.
9.    If your system is like mine you will soon have these partitions, sda1  (the EFI partition), sda2 (the OS X partition) sda3 (the NTFS partition), sda4 (the Ext4 Ubuntu partition) and sda5 (your swap partition).
10.     When you arrive at step 8 the last dialogue box of the installer before you commit to all of this select the advanced button and choose to install the grub boot loader to /dev/sda3  Your NTFS partition.   Rock and roll
11.    Reboot when the install is complete and in the rEFit menu choose the partition tool and resync if necessary.   
12.    Power down your computer..  again a choice in the rEFit menu.
13.    Power up and you should be good to go..




this worked great for me too.

weird thing though...when i run reffit, it gives me the option to boot either mac, ubuntu, or windows...i haven't installed windows on my comp so this seems odd to me. i haven't tried to see what happens if i choose to boot this imaginary windows. anyone know why this would happen? or if it will cause problems?


edit: ok when i boot into "windows on partition 3" its just boots me into ubuntu...weird.

---

### Post by onyxrev on 2011-01-13
What I had to do to solve this issue is to create a small bios_grub partition on my hard drive for grub to install itself into.

I happened to have a small amount of unallocated space on my drive.  If you do not have any unallocated space on your drive you'll have to resize a partition or something to make some.

But, to get it working I booted into rescue mode on an alternate installer CD, chose my computer's root partition as the target for the root shell, then did:

```
parted
```

In the parted) prompt I typed 

```
print
```

which showed me the layout of the drive.

I saw the available partition, which was partition 9 in my case.

I typed "quit" to exit parted and from the command line I typed:

```
parted /dev/sda set <partition_number> bios_grub on
```

It created the bios_grub partition for me.

Once that was complete, I tried grub-install:

```
grub-install /dev/sda
```

While that had previously failed with the same errors others have reported in this thread, it now worked because it had the bios_grub partition to work with.  

I rebooted, selected my partition from refit, and grub came up just as it did before the OSX update that trashed it.

---

