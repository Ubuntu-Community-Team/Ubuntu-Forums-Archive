---
title: "Please verify what I'm doing..."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by seremina on 2006-12-21
[B][SIZE=4][FONT=Arial]I've decided to put Ubuntu 6.06 onto an empty drive rather than my main hard drive. I've read this... [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

but for the first option, it doesn't tell me if I can specify for it to go to Drive F instead of Drive C. I intend for this newer system to be a dual-boot. The main OS is WinXP Home.

So do I use Option 1? Am I going to be doing this right? Please use simple English and try to explain any Linux terms if they must be used. Thanks!

seremina
[/FONT][/SIZE][/B]

---

### Post by Bachstelze on 2006-12-21
Hi and welcome to Ubuntu :)

First, there are no such things as "Drive C:" and "DRive F:" in Ubuntu. Drive letters are a DOS/Windpows invention and you won't find them anywhere else. When you're saying "first option", I think you're referring to [this](http://img230.imageshack.us/img230/2340/w2u260tf.png), so yes, the first option is what you need to choose :) It will resize your Windows partition so defragging it in Windows before is not a bad idea.

---

### Post by rsambuca on 2006-12-21
With the Live CD, you first boot to the ubuntu desktop, which then runs from your CD drive and doesn't do anything to your existing hard drives.

After you have booted up, you will see an icon on the desktop that says install (or something like that, I can't remember exactly).  In any event, try booting to the live CD first, make sure your hardware is all detected, and then go through the installation from the live CD.

---

### Post by seremina on 2006-12-21
**[FONT=Arial][SIZE=4]Okay. But I don't want the Ubuntu on the same drive as the one that has Windows installed on it. I thought it would be a wise use of space to use a different hard disk for Ubuntu.[/SIZE][/FONT]**

---

### Post by Bachstelze on 2006-12-21
I personnally prefer to have all my OSes on the same drive but if you want to install UBuntu on another drive than Windows, you can perfectly well do so but I don't know how to do it when installing from a Live CD.

---

### Post by edwardLS on 2006-12-21
Maybe I am not understanding your question; however, I take it that you want to keep the Windows XP installation as is, and install ubuntu on a second hard drive.  If that is correct, I believe that the "First Option" refers to the Hard Dish containing your Windows XP installation.  I believe that you would want to "Manually Partition" your second drive so that you can leave the Windows XP intact.

---

### Post by aidanr on 2006-12-21
i've two disks and as far as i can remember gparted listed both my drives at that point, ie. an option to "erase entire disk: IDE1 master (hda)" and "erase entire disk: IDE1 slave (hdb)" so if that option is there choose hdb

---

### Post by seremina on 2006-12-21
[B][FONT=Arial][SIZE=4]Yes, you now have the idea. I want the Ubuntu on a 2nd hard drive, not on the main one.

Manually partition. Lovely. I hoped to avoid that headache since I'm such a beginner. At least the guide I posted guides me through that, though I won't know what Ubuntu will call my F drive. So that's what...the 3rd option on the guide? Is there anything in the guide that isn't being said? I'd like to know that since I'm so dense.[/SIZE][/FONT][/B]

---

### Post by voraistos on 2006-12-21
Drives are organised fifferently in Linux. No C:, F:,  or whatever.

Depending on what the installer finds, youll have options between /dev/hda1 , hdc5 and so ...

"hd" basically means hard drive, "a" means master of the first ide controller "b" slave of the first ide controller "c" is master of the second ide controller, etc... The final number in "hda1" means it is the first primary partition of the disc. Logical partition numbers start with "5" and go up to... i dont know how much :)

I will presume your windows drive/partition is hda1, and your computer's BIOS will look for its "bootloader" to load.. kernel32 or whatever it is called. The thing is to load linux you have to use another bootloader called "grub" (other bootloader exists). This bootloader can boot windows as well, and in fact, what matters in all that is that your BIOS asks the disk with GRUB to boot the computer. What i would do is not caring about windows at all, install ubuntu on /dev/hdc or wherever your "F" disk is. Ubuntu will create 2 partitions on it called "/" and "/swap". The ubuntu installer will most likely detect youyr empty "F" drive and assign automatically / and /swap to it.

Unless you are a gamer, you can also remove windows definetly (i promise you wont regret :) ) and free-up some disk space for your ogg and flac library :)

---

### Post by edwardLS on 2006-12-21
You are setting up your system very similar to the way I have set up my system.  I have a Windows 2000 partition, a Windows XP partition, and an MS-DOS partition on the First/Main hard drive.  On my second hard drive I have ubuntu installed with the partition table being manually edited.  In my case, the main drive (first) is hda, and the second drive (containing ubuntu) is hdb.  The numbers refer to the partitions on the drives which are lettered a, b, etc.

In manually partitioning a drive for ubuntu, the main two areas to be very careful of is: where you create a partition (which hard drive's free space) and where each of the created partitions are mounted in the Linux file system.  Unfortunately, the creation of the partitions and the designation of the mount points are on two different dialog screens.  So, what I do is carefully record what the names of the partitions are that I have created, (i.e. hdb3, hdb6, etc) along with where I want the partitions mounted (i.e. hdb3 -> /home, hdb6 -> /boot).

The one final caution - pay particular attention to which partitions are going to be REFORMATTED.  If you see something on hda (your main drive) marked for reformatting - you need to back up.  Hope this helps.

---

### Post by seremina on 2006-12-22
[B][SIZE=4][FONT=Arial]Okay. I'm really nervous but I'll give it my best shot. I'm taking an educated guess that F would be hdb--as someone said--since its the 2nd hard disk on this system, though C has a partition filled with emergency WinXP files called D. 

I'll follow your advice and the guide closely, using option 3. I realised that I could identify the correct drive just by the size the readout gives. I've already defragged that drive just so its nicely prepared.

Wish me luck. :)
[/FONT][/SIZE][/B]

---

### Post by edwardLS on 2006-12-22
Here's wishing you luck and success.  And, welcome to ubuntu Linux.  I am a newbie with Linux, but I am quite comfortable partitioning drives under both Windows and Linux.  That comfort comes from experience and learning what to expect as I do this stuff.  I have used several different partition table editors, and they all do the same thing, its just that Linux identifies devices (drives/partitions) differently than Microsoft and Windows has taught us.  I am sure you will do well if you take your time and check yourself at each step.

---

### Post by rsambuca on 2006-12-22
Good luck Seremina.  Keep us posted.

(And do you mind decreasing your font size a little bit?  I can't help but feel like you are mad at us for something!;) )

---

### Post by seremina on 2006-12-24
[SIZE=4][FONT=Arial][B]Umm...how am I seeming angry at you? As far as I know, all caps indicates yelling, and increased font indicates visual impairment. So I'm feeling kinda insulted here now.

I had a wonderful surprise happen. At the Option list, under the 1st Option, it actually listed hdb/F! So I happily chose it and continued as usual. Of course, I had less to do since it offered that. Well, when the computer rebooted...it offered no dual-boot menu. It just booted me into WinXP as usual. What went wrong?
[/B][/FONT][/SIZE]

---

### Post by spockrock on 2006-12-24
Umm...did you install grub you need to install grub.

just boot off the live disc
open terminal then

```
sudo grub
```
then you should see grub > 
```
find /boot/grub/stage1
```
this should give you something saying hdx,x ; where the x's are numbers 
```
root (hdx,x)
```
use what you were told in the previous output
```
setup (hd0)
```

_____ 

if that doesnt work, I think I may know what the problem is as well.

---

### Post by seremina on 2006-12-24
[B][SIZE=4][FONT=Arial]I thought Grub installed all by itself, as the guide indicated? It seems unusual I have to manually install it.

In any case, could you dumb down the instructions? It sounds technical. ](*,)
[/FONT][/SIZE][/B]

---

### Post by spockrock on 2006-12-24
> **seremina said:**
> [B][SIZE=4][FONT=Arial]I thought Grub installed all by itself, as the guide indicated? It seems unusual I have to manually install it.

In any case, could you dumb down the instructions? It sounds technical. ](*,)
[/FONT][/SIZE][/B]

it should install just on its own, but umm maybe you skiped the step, I dunno.

I dunno how much more I can dumb it down it seems simple enough

just boot off the live disc
open terminal, from the menu on the top left, applications>accessories>terminal

then enter the following inside terminal.
```
sudo grub
```
then you should see grub > 
```
find /boot/grub/stage1
```
this should give you something saying hdx,x ; where the x's are numbers 
```
root (hdx,x)
```
use what you were told in the previous output
```
setup (hd0)
```

---

### Post by tommcd on 2006-12-24
This explains in detail how to install grub off the live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
If all else fails get a super grub disk and install grub from that:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Hope this helps.

---

### Post by seremina on 2007-01-17
[B][SIZE=3]Okay...I've tried through the Live CD to install Grub. Sudo won't accept the command setup (hd0) nor setup (0). Both hd0 and 0 were stated to be booting drives and I have no idea which one to use.

I have no idea what's going wrong.
[/SIZE][/B]

---

### Post by tommcd on 2007-01-18
Have you actually installed ubuntu yet? And if so, did you install to the 2nd hard drive as you wanted?
See these 2 threads.
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)
[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

 Read the replies from "lha" about dual booting with 2 hard drives (ie, set the 2nd ubuntu disk as master and windows drive as slave). It sounds like an excellent way to dual boot with 2 hard drives.
I only have 1 hard drive in my systems, so I can't verify that.

---

### Post by seremina on 2007-01-18
> **tommcd said:**
> Have you actually installed ubuntu yet? And if so, did you install to the 2nd hard drive as you wanted?
See these 2 threads.
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)
[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

 Read the replies from "lha" about dual booting with 2 hard drives (ie, set the 2nd ubuntu disk as master and windows drive as slave). It sounds like an excellent way to dual boot with 2 hard drives.
I only have 1 hard drive in my systems, so I can't verify that.

[SIZE=3]I'll read the two threads, but I didn't know I'd have to do this to make it dual-booting from a secondary drive. I did install Ubuntu to the secondary drive, but I realise you have a point and I'm an idiot. How do I unformat my secondary drive and uninstall Ubuntu on it? I want to start over. I want to transfer my music to the secondary drive so I have plenty of room to stick Ubuntu onto my main drive alongside WinXP. I should've done it that way in the first place, being a beginner and all.[/SIZE]

---

### Post by tommcd on 2007-01-19
If you installed ubuntu to the 2nd drive, and everything works, I would leave it as is. If you really want to have ubuntu on the first drive, and windows on the second, the you could physically switch the drives in your PC, and edit your fstab if necessary (I have read that the UUIDs eliminate the need for this).
You could just put windows and ubuntu on the first drive and use the second drive for data. In the ubuntu installer just select the option to "resize existing partition" (or whatever it says). I have dual booted 3 different systems and never had a problem with windows after the installation.
After ubuntu installs windows will run the system file checker the first time you boot it. Also, it seems the first time you defrag windows after installing ubuntu the defrag takes longer than usual. Otherwise, I have never noticed a problem. Either way, it's not so much difficult as it is just different. Jump in and don't be afraid.

---

### Post by Malac on 2007-01-19
Just a quick tip for anyone unsure of drive names will be transfering from Windows to Linux.
Whilst in Windows just create  files on the root of each drive called; Drive_C, Drive_D, Drive_E, etc. easy.
and
```
df -h
``` always handy for listing sizes usage of drives.

---

### Post by blackened on 2007-01-19
Have you already tried changing the boot order in the BIOS? Set the slave as the first boot device and see if grub starts.

---

### Post by seremina on 2007-01-19
[SIZE=3]Well, I had wanted to uninstall Ubuntu and reformat the secondary drive because I realise it really -might- be easier to have both WinXP and Ubuntu on the same drive. So I asked how to do this.

If I set the slave drive as the first drive that boots up, I'm not sure what would happen. I mean, Grub wouldn't show up in the first place. So I'm concerned Grub wasn't even installed. So I wanted to start all over again the way I should've done it in the first place. Fear really bugged me up and I won't let fear control my decisions from here on.

I want to use the secondary drive as a data drive, since I'm -really- running out of space on the first drive. Once I have Ubuntu on the first drive, I'll have to transfer my song media to the secondary drive just to uncramp it.

Do you all understand now? :)
[/SIZE]

---

### Post by Malac on 2007-01-19
> **seremina said:**
> [SIZE=3]Well, I had wanted to uninstall Ubuntu and reformat the secondary drive because I realise it really -might- be easier to have both WinXP and Ubuntu on the same drive. So I asked how to do this.

If I set the slave drive as the first drive that boots up, I'm not sure what would happen. I mean, Grub wouldn't show up in the first place. So I'm concerned Grub wasn't even installed. So I wanted to start all over again the way I should've done it in the first place. Fear really bugged me up and I won't let fear control my decisions from here on.

I want to use the secondary drive as a data drive, since I'm -really- running out of space on the first drive. Once I have Ubuntu on the first drive, I'll have to transfer my song media to the secondary drive just to uncramp it.

Do you all understand now? :)
[/SIZE]
Yes,
I would recommend formating the second hard drive in fat32 (then it is accessible from win/ubu easily) then transfer the song media to the second hard drive first.
That way you have as much free space on disk one as possible for when you resize the Windows partition.
I also would recommend defragging from within windows 2-3 times to make sure it's as contiguous as possible before starting the install process.
And unless you don't mind losing windows completely make a backup of important files. (This probably won't be necessary but yours could be the 1 in 10000 installs that goes wrong) :)

---

### Post by seremina on 2007-01-19
[SIZE=3]Oh, okay. Will do. YES! Simple instructions at last! [giggles] I'll let you know what happens once I'm finished. Thank you muchly. ;)

Just one question. How do I make the formatted drive show up in my drives listing so I can reformat it? With it being Ubuntu format, its...well...vanished.
[/SIZE]

---

### Post by Malac on 2007-01-19
> **seremina said:**
> [SIZE=3]Oh, okay. Will do. YES! Simple instructions at last! [giggles] I'll let you know what happens once I'm finished. Thank you muchly. ;)

Just one question. How do I make the formatted drive show up in my drives listing so I can reformat it? With it being Ubuntu format, its...well...vanished.
[/SIZE]
Use gparted from Ubuntu (you may have to install this using apt-get install gparted or using Synaptic)
Preferably do it from Windows as the MB's are worked out slightly differently in Linux to Windows so it is possible to format it to the max in Linux but this will not be readable in Windows. This seems best to me as you are more familiar with Windows.
If you are doing it from gparted use the unmount option to enable formatting.

If it is a large drive you will have to split it in to 32 GiB partitions.
Good Luck.

---

### Post by seremina on 2007-01-19
[SIZE=3]All right. I'll handle it from Windows, but I thought Gparted was a Linux application. Where do I get Gparted?[/SIZE]

---

### Post by Malac on 2007-01-19
> **seremina said:**
> [SIZE=3]All right. I'll handle it from Windows, but I thought Gparted was a Linux application. Where do I get Gparted?[/SIZE]
There is a copy of gparted on the Ubuntu Live/Desktop CD under [System->Administration->Gnome Partition Editor] menu option.
But as I said if you can do all your fat32 partitions from within Windows then Ubuntu should pick them up and create entries for them in /etc/fstab when you install and mount them in the /media folder so you can access them.
Can you list the sizes of your drives/partitions as they are now and I will try to suggest a partitioning scheme to do from Windows if you want.
e.g. My set up:
Disk 1 is 30 GB
----partition 1 (/dev/hda1) set to 12 GB fat32 (Win98 )
                                  ----partition 2 (/dev/hda2) set to 15 GB ext3 (Ubuntu "/")
----partition 3 (/dev/hda3) set to 1.1 GB (Extended Partition)
----(within partition 3)
--------partition 5 (/dev/hda5) set to 1.1 GB (linux-swap)

Disk 2 is 200GB
----partition 1 (dev/hdb1) set to 32 GB fat32 (WinXP)
----partition 2 (/dev/hdb2) set to 10 GB ext3 (Ubuntu Backups)
----partition 3 (/dev/hdb3) set to 22 GB ext3 (Ubuntu "/home")
----partition 4 (/dev/hdb4) set to 127 GB (Extended Partition)
----(within partition 4)
--------partition 5 (/dev/hdb5) set to 32 GB fat32 (Misc)
--------partition 6 (/dev/hdb6) set to 32 GB fat32 (Misc)
--------partition 7 (/dev/hdb7) set to 32 GB fat32 (Misc)
--------partition 8 (/dev/hdb8 ) set to 32 GB fat32 (Misc)
--------partition 9 (/dev/hdb9) set to 1.5 GB (linux-swap)

I manually set all the fat32 partitions from within WinXP before installing Ubuntu.
Then shrank the partition 1, as it took up the whole drive originally,  using gparted on the Live CD.
Then ran the installer and told it to use the largest free space on Disk 1. which I had freed up with gparted.
I then formatted the other ext3 partitions once I had Ubuntu installed.
A quick way is to mark a rough note of your disk layout like above before you start and as you do operations that shrink or change the drives change your layout notes to match so you don't get lost or choose the wrong partition number.
As a rough guide /dev/hd**a** is disk **1**, /dev/hd**b** is disk [B]2
[/B]partition numbers are then added on the end so
/dev/hd**a1** is disk 1(**a**) first(**1**) partition 
/dev/hd**b3** is disk 2(**b**) third(**3**) partition

Hope this helps.

---

### Post by seremina on 2007-01-19
[SIZE=3]O...kay. I am totally confused at this point. I don't know how to do formatting in WinXP nor Linux. If I look at My Computer, the F drive doesn't show up. If I look in the hardware profiles, it shows up but has fewer options available to it in the right-click menu. One of the options, for either drive, is NOT Format... so... I'm totally lost.[/SIZE]

---

### Post by Malac on 2007-01-20
> **seremina said:**
> [SIZE=3]O...kay. I am totally confused at this point. I don't know how to do formatting in WinXP nor Linux. If I look at My Computer, the F drive doesn't show up. If I look in the hardware profiles, it shows up but has fewer options available to it in the right-click menu. One of the options, for either drive, is NOT Format... so... I'm totally lost.[/SIZE]
If you right-click My Computer and choose Manage from that menu there is a Disk Management Section in the program that is opened.
This lists all the disks and how they are partitioned. Right-clicking on any of the partitions gives you the option to format.

---

### Post by seremina on 2007-01-20
[SIZE=3]Okay! I have the list now and it shows up as an unknown format. So I can tell which is which. Format is grayed out. It just offers me the choices to Delete Partition and Delete Logical Drive.

So what do I do?
[/SIZE]

---

### Post by Malac on 2007-01-20
> **seremina said:**
> [SIZE=3]Okay! I have the list now and it shows up as an unknown format. So I can tell which is which. Format is grayed out. It just offers me the choices to Delete Partition and Delete Logical Drive.

So what do I do?
[/SIZE]
Can you post a screenshot of the window. As I am working with out knowing what you have on your drive now.
(Press [Print Screen] Key next to [Scroll Lock] then open Paint or whatever and Ctrl+V to paste and save it.)

Or do a list like in one of my previous posts.

---

### Post by seremina on 2007-01-20
[SIZE=3]Okay. Attaching now.[/SIZE]

---

### Post by dorcssa on 2007-01-20
Deleting means erasing the actual file system, and after that you can format it.

---

### Post by seremina on 2007-01-20
[SIZE=3]So if I delete both the partition and the Logical Drive, then I'm able to safely format the drive? I guess that makes sense...why else would format be grayed out?

Could I get a confirmation that this is what I should do?
[/SIZE]

---

### Post by Malac on 2007-01-20
> **seremina said:**
> [SIZE=3]Okay. Attaching now.[/SIZE]
[SIZE=3]Okay let me just check on two things.
From your screenshot it looks like you are booting off Disk 0 then going to partition 2 of Disk 1. It also looks like partition 1 of Disk 1 is a recovery partition.
To install Ubuntu on this system I would:
From Windows defrag [/SIZE][SIZE=3]2-3 times [/SIZE][SIZE=3]as outlined in earlier post.
Then Boot the Ubuntu Live/Desktop CD
Open [System->Administration->Gnome Partition Editor]
 Shrink/Decrease the partition 2 of Disk 1 to free up space for Ubuntu. This will be **/dev/hdb2** in Ubuntu.[/SIZE]
(Depending on what you are going to do with Ubuntu, it needs a minimum of 2GB for the Root system and as much storage for the /home/user files as you want to give it. Some where around 10GB-20GB should do it. depending on how much free space you have on the C: partition.)
[SIZE=3]Next [Apply] then quit when it has finished.
You will probably need to reboot at this point.
When you are back at the Live CD Desktop:
Fire up the installer and when you get to the section where to install to ask it to install to the largest free space on Disk 1(XP notation) which will be /dev/hdb (Ubuntu notation).
when it has finished [/SIZE][SIZE=3]remove the Live CD/[/SIZE][SIZE=3]reboot the machine and you should see a GRUB prompt, if you press Esc key at this point it should bring up a menu asking which option you want to boot;
Ubuntu
Ubuntu (Recovery Mode)
Memtest+
Windows XP
Choose Ubuntu and check that it gets you to the Desktop, etc.
Then [Applications->Accessories->Terminal] and run this command.
[/SIZE]```
[SIZE=3]sudo gedit /boot/grub/menu.lst[/SIZE]
```[SIZE=3]Find this section:
[/SIZE]```
[SIZE=3]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu[/SIZE]
```[SIZE=3]and insert a # in front of the word hiddenmenu in the 3rd line.
Save then Quit.
Reboot and check that the menu comes up on it's own if it does choose Windows XP and wait for that to boot up. If it doesn't run a disk check right click on the drives and choose Properties[/SIZE][SIZE=3] then on one of the tabs is a Check Disk option, choose that. It may say something like can't do it now do you want to schedule this for next boot, say "Yes".
Reboot again into Windows and it should check your disks.
Voila you're done.
You can then play around with the Disk 0(XP notation) **/dev/hda1** to get it to a size you want to use.
[/SIZE]

---

### Post by seremina on 2007-01-20
[SIZE=3]Okay. That's a lot of steps. Thank you for mentioning them in both Windows and Ubuntu terms. That helps a LOT. I'll write all this down and you can let me know if I can proceed with your instructions or follow different ones. I'm not sure if I should do yours or try to format the Ubuntu-using drive first. 

For now, I'll explain the pic you were looking at. 

Drive 0 [Win notation] (used to be Drive F) is the Ubuntu-formatted drive that I want to reformat. It includes a Swap Partition.
Drive 1 [Win notation] is the main hard drive (Drive C), has WinXP on it, and includes a partition as a "Recovery Disc", called Drive D.
Drive E is my Cd Rom, obviously.

So what's the word, Captain? :)
[/SIZE]

---

### Post by Malac on 2007-01-20
@seremina if you want to have ubuntu on the same disk as WInXP then follow my previous instructions.
But please backup as much as you can just in case anything goes wrong.

---

### Post by seremina on 2007-01-20
[SIZE=3]You got it. Thank you. =D>

So I can begin, how do I format the Ubuntu-formatted drive? You seemed to have missed that step in your instructions.
[/SIZE]

---

### Post by Malac on 2007-01-20
> **seremina said:**
> [SIZE=3]You got it. Thank you. =D>

So I can begin, how do I format the Ubuntu-formatted drive? You seemed to have missed that step in your instructions.
[/SIZE]
You can do that once you have Ubuntu installed from the Gnome Partition Editor. :)
Right-click the partition, unmount, right-click format.

---

### Post by seremina on 2007-01-20
[SIZE=3]Okay. Final question. [I know, I'm just driving you nuts, but I really am this stupid.]

Once I right click format...will it let me choose Fat32?
[/SIZE]

---

### Post by rsambuca on 2007-01-20
Yes, the Gnome partition Editor will let you format in FAT32 format.  (I jumped in as I see Malac is not online right now.) - and by the way, we do not think you are stupid for asking these questions.  Rather, I think it is important to understand what you are doing before messing around with formatting and partitioning.

Good luck!

---

