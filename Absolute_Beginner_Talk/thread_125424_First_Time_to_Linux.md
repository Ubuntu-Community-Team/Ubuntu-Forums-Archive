---
title: "First Time to Linux"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by X-Cannon on 2006-02-03
I'm typing this from my new Linux box :D, anyway I have just instaled Ubuntu 5.10 and was wondering I have a swap partion at 500 mbs, a root at 2.4 GBs thats the partion Ubuntu is on (I think) and I have about 17.5 gbs free.

Where do I go to see my 17.5 GB free space? and if I download a file i.e macromedia and I double click it it wont install (yes, its for linux) also how can I get a my computer icon on the desktop so I can see all infos and see my drives i.e HDD, cdrom, floppy etc... like in XP?

---

### Post by xmastree on 2006-02-03
[QUOTE=X-Cannon]I'm typing this from my new Linux box :D,[/quote]
Well Done! \\:D/ 
> Where do I go to see my 17.5 GB free space?Go to places>home and it will open up nautilus. At the bottom of the window it will show you the status of that drive.

The big difference (or one of them) between Linux and Windows is that disks/partitions/filesystems are mounted differently. There is no c: d: etc.

Your primary master disk is hda (assuming it's a regular IDE drive, not SATA) primary slave is hdb. Partitions are marked like hda1, hda2 etc.

Open a terminal and type **df** to see a brief outline of what's there and what's available.

> how can I get a my computer icon on the desktop 
I'm assuming you're running Gnome here...
If you rightclick the desktop, and select **create launcher ** from the menu. Type 'My Computer' in the name, and 'nautilus' in the 'command' fields.

---

### Post by X-Cannon on 2006-02-03
I cant see my 17.5 gbs where are they? I went to terminal and df and this is what I see 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              2308616   1615308    576036  74% /
tmpfs                   128016         0    128016   0% /dev/shm
tmpfs                   128016     12588    115428  10% /lib/modules/2.6.12-9-386/volatile

where do I go to access my 17 gbs and put things in there? and how can I open media files i.e .wmv/mp3s divx, I dont believe that there is a one program in Linux that does all that maybe VLC but which do I download?

---

### Post by xmastree on 2006-02-03
Another way to see your available disk space is this:
[img]http://ubuntuforums.org/attachment.php?attachmentid=5833&d=1139024108[/img]
That's desklets (FTB in this case) and it's telling me that I have three drives (I put three of them there, one for each drive)
Top one is my root linux system. 9.2GB total, 800MB free :-k 
Next is a removable disk, 18.6GB, 12.6GB free
Last is my shared drive, 18.1GB, 1.9GB free
Below those are cpu/network data.

---

### Post by xmastree on 2006-02-03
[QUOTE=X-Cannon]I cant see my 17.5 gbs where are they? I went to terminal and df and this is what I see 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              [COLOR="Red"]**2308616**[/COLOR]   1615308    576036  74% /
[/QUOTE]
That's saying that the primary partition on your primary master disk is only 2.3GB

run this command, and post the output
**sudo fdisk -l**
that will list all partitions on all disks

re-reading your original post, Root=2.4GB which agrees with the above.
I suspect your 17.5GB hasn't been partitioned yet.

---

### Post by Virogenesis on 2006-02-03
/ is your main drive directory often known as your root space.
Each user has his own space on the system under /home this is where the user can keep his downloads and what have you.
Think of it like your "My Documents"
You the user only have access to access your home directory for security reasons.
You can see the space left on the drive by going to Applications -> System -> System Monitor

After running this program you shall see three tabs click on "Devices" this shall show you how much is remaining on the drive.

Going to Applications -> System -> configuration editior will allow you to place desktop icons for things such as DVD, Floppy and My Computer and Wastebin.

On the left hand pane click Desktop then scroll down to "Apps" click to expend 
Then nautilus then click on the desktop folder you shall see in the right pane.

trash_icon_visable, computer_icon_visable, document_icon_visable, volumes_visable...... tick all of these boxes.

---

### Post by mcmillan on 2006-02-03
It seems like you say your root partition is the 2.4 GB and the 17.5GB is seperate from that which you want to access. My impression is that this means you have 17.5 GB unformatted, therefore it would need to be formatted before you can do anything with this. You can do this with a program called gParted which I think is pretty intuitive. The simplest thing would to just increase the size of hda1 so it fills the free space, but you'll need to boot using a liveCD to do this. I think a better setup would be to make a new partition that takes up that all that space and use it as for your home partition. If you want to do this let me know and I can give you more detailed explantion. 

For installing things it usually easiest to install things using synaptic, so I'd suggest that, though you might have to enable extra repositories first. Explantion of how to do that is in the link at the end of this post. If there's something you really need that's not in the repositories let us know and we can try and walk you through that. 

To play music I'd recommend either amarok or xmms. For video I like xine. You'll probably need to download some other things to get mp3 and divx to work though.

It might also be a good idea to check out [this site]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories"), it's an updated version of ubuntuguide.org. It has a little of good walkthroughs for things you'll probabably want to know how to do.

---

### Post by Virogenesis on 2006-02-03
mp3 support isn't out of the box you'll have to enable that yourself. 
have a read of this [Link]("http://doc.gwos.org/index.php/BreezyCust") its got great documents on how to get started.
Beep-media-player is a fantasic audio player very much like winamp infact it supports winamp 2 skins.
A good media player is mplayer its skinable and is possible the best.

---

### Post by xmastree on 2006-02-03
I find mplayer slightly troublesome... My personal preference is beep, which can use winamp skins.

---

### Post by X-Cannon on 2006-02-03
Yes, I would like to get the 17.5 GBs as my root cause I want to use it :P, how can I do this ? I left it as free space cause I thought Linux would instal on the 2.5 gbs and I'd have the rest as stroage space aside form 500mbs for swap.

---

### Post by xmastree on 2006-02-03
You don't have to get it as root to use it.
Partition it, format it as ext3, and mount it somewhere. Anywhere you like. You can then use it. If you wish to increase your root filesystem to the full drive, you will have to unmount it. that means you can't do it from within the system you're running, hence mcmillan's live CD suggestion.
I would stick with the 2.4 you have and just make a new partition with the remainder.
If you decide to do this, I (we) will help you with how to partition/format and mount it.

---

### Post by X-Cannon on 2006-02-03
I think the easiest solution would be to pation the 17 gbs abd mount it how do I do this?

---

### Post by mcmillan on 2006-02-03
Open up gparted. 

Right click on the free space, and click new. I'm pretty sure it then asks you what size you want, the default is to use the all of the unformatted space. For the format you'll probably want ext3. Then click apply. I'm pretty sure that's all you need to format it. Not certain without messing with my partitions though, not something I'm up for doing.

As I said, the best setup would be then to use this as your home partition. This lets you can reinstall ubuntu without losing your personal settings. 

To do this first you'll need to mount your new partion. 
Make a new directory to do this, in a terminal type 

sudo mkdir /mnt/newhome

Then do

 sudo mount /dev/hda2 /mnt/newhome

I assumed your new partion is hda2, I don't see a reason for it to be something different, but if it is then change that to whatever it is.
Then

 sudo cp /home /mnt/newhome

Now you edit your fstab file, telling where the computer should mount partitions. 

sudo gedit /etc/fstab
and add a line like this:
/dev/hda2 /home ext3 defaults 0 1

Reboot your computer and then it should work with everything as a seperate partition.

---

### Post by X-Cannon on 2006-02-04
is Gparted included in Ubuntu or do I download it myself? if I have to download plz show me how to install it.

---

### Post by xmastree on 2006-02-04
As far as I know, it's not part of the basic installation. Look in Synaptic for it and install it from there. You'll find synaptic under System>Administration

Edit: You'll get used to Synaptic. It's one of the best things about ubuntu. You don't have to download anything yourself. Just find it in the list, select install, and it happens automagically. :cool:

---

### Post by X-Cannon on 2006-02-04
wont let me open it makes a ding sound when I click it samething happenes to the clock ( clock worked the first 2 mins not anymore)

---

### Post by xmastree on 2006-02-04
[QUOTE=X-Cannon]wont let me open it makes a ding sound when I click it samething happenes to the clock ( clock worked the first 2 mins not anymore)[/QUOTE]
Strange... Open a terminal and type```
sudo synaptic
```enter your password and it ought to open. If not, what's the error message?

---

### Post by X-Cannon on 2006-02-04
wont let me open it says " You must run this program as the root user" I thought I was the root user theres only 1 account and ths me as far as I know

---

### Post by percival95 on 2006-02-04
[QUOTE=X-Cannon]wont let me open it says " You must run this program as the root user" I thought I was the root user theres only 1 account and ths me as far as I know[/QUOTE]

Make sure you type the word "sudo" first. Like this sudo synaptic

---

### Post by X-Cannon on 2006-02-04
k did that and I cant find gparted anywhere

---

### Post by xmastree on 2006-02-04
you probably don't have gparted installed yet. Use synaptic to install it. Type **sudo synaptic** at the prompt, enter your password when asked, and it should open. Then, use the se

If synaptic is giving you a hard time (it shouldn't) try this instead. in a terminal

```
sudo apt-get install gparted
```

That ought to install gparted for you. then you can run gparted from the same prompt. Remember to use **sudo** before the command, to run it as root.

Beind the only account doesn't mean you are root, but you can act as root with **sudo**

---

### Post by bschuteker on 2006-02-04
Did you do a search for it? If you did and it doesn't show then you probably need to enable extra repositories. (places where it can got to find the packages) Here is a link to a very good tutorial on how to do that.
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Here is a link of a good explanation of installing software in Ubuntu.
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Also check out the Ubuntu beginners guid on that link.

Here is a link to a program called Automatix. Read it carefully and follow the instructions. It will enable you to do a lot of things like play mp3's and watch DVD's etc...
[http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

This should keep you busy for a while,

Bill

---

### Post by X-Cannon on 2006-02-04
K after I updated everything and finally gor gparter to work I did what mcmillan said to do and this is waht happened after I shutdown the computer then up again

/Dev/hda1 is mounted e2fscki cannot continue, aborting
underneth that is *fsck failed, Please repair manually

then in the login screen after name and PW theres this /home/thename

but it does not appear to exist

I really need help I did waht mcmillan said to the T!

All I want is my 17.5 gbs to mix with my hda1

---

### Post by xmastree on 2006-02-04
you don't want to touch /dev/hda**1**, that's your 2.4GB partition.
gparted should show unpartitioned space. I can't check as I don't have any.
You need to create /dev/hda2, a second partition on the disk.

Edit: Stick around, I'm trying something here...

---

### Post by X-Cannon on 2006-02-04
ther was a dev/hda2 it was about 500 mbs and there was also a swap I made.

---

### Post by xmastree on 2006-02-04
Ok, check this screenshot. I reduced the partition on my 3rd disk from 19 to 15GB, and this is how it now looks with gparted:-

[img]http://www.ubuntuforums.org/attachment.php?attachmentid=5842&stc=1&d=1139043441[/img]

If I right click on the **Unallocated** area, I have the option to create a new partition.

I expect yours ought to be similar, but with 2.4GB for /dev/hda1 and 17.5 unallocated. There's probably a swap in there too.

---

### Post by xmastree on 2006-02-04
[QUOTE=X-Cannon]ther was a dev/hda2 it was about 500 mbs and there was also a swap I made.[/QUOTE]

Run this command:
```
sudo fdisk -l
```
and post the output please.

It's safe to run that, it just lists what's there.

---

### Post by X-Cannon on 2006-02-04
I cant get past the log in screen waht should I do log in in terminal mode?

---

### Post by Packard Dell on 2006-02-04
Download Knoppix Live CD (Knoppix is a Linux distro that can boot from CD-ROM) and burn it to a disc. Once Knoppix is booted and loaded, select the **K** icon from the bottom panel then* System > QTParted*.

Since you are having problem with your Synaptic Package Manager, i think you will need to re-install your Ubuntu then modify your partitions. Add more space for your linux partition because 2.4GB i think will not be enough, you might want to install more applications or packages in the near future then you will run out of space. At least 10 - 15GB will do. Also you mentioned that your swap is 500MB, how much RAM do you have? if you have 256MB you should double that and that makes 512MB of swap. From your fresh installation, i'd advise you to do manual partitioning so that you can have access to your free space and format it. 

> and if I download a file i.e macromedia and I double click it it wont install (yes, its for linux)

installing software in linux is different, you cannot just click it and follow a wizards like Windows-habit. What file extension (e.g. .tar, .tar.gz, .bin) is that you are trying to install?

---

### Post by xmastree on 2006-02-04
what happened? You lost the desktop? in terminal mode you can log in with the same name and password, then type **startx** at the prompt. That ought to start the desktop environment running.
If not, and it claims it's already running, try Ctrl-Alt-F7

---

### Post by X-Cannon on 2006-02-04
I'm in the terminal now and I tried startx, nothing and ctrl+alt+F7 still nothing
MAYBE I should just format and install ubuntu all over again all on 1 partion and just have a swap as well.

What do u guys say?

---

### Post by xmastree on 2006-02-04
That might be the best option. There's an option during the install to wipe the disk. Select that. So long as you don't go for manual partitioning, it should use all the available space. It will make its own swap.
Some argue that manual partitioning is better, but only if you know what you want. Us new users don't usually, so the automatic will do what it wants to.

---

### Post by Packard Dell on 2006-02-04
[QUOTE=X-Cannon]I'm in the terminal now and I tried startx, nothing and ctrl+alt+F7 still nothing
MAYBE I should just format and install ubuntu all over again all on 1 partion and just have a swap as well.

What do u guys say?[/QUOTE]

That's what i have just said because i can see that you are having a lot of problem with your Ubuntu at the moment, re-installing it might solve the problem.r

---

### Post by X-Cannon on 2006-02-04
thats gonna take about 1 1/2 hours takes pretty long to install Ubuntu or amybe its just me :P

anyway plz list waht I should do just after reinstaling Ubuntu again? so I wouln't have to go over this again :D

---

### Post by Virogenesis on 2006-02-04
if you let ubuntu set up the partions you won't have this problem as it will set up a swap according to how much ram your system has and the rest will be used for / which will be basicaly be your whole drive.

---

### Post by Packard Dell on 2006-02-04
[QUOTE=X-Cannon]thats gonna take about 1 1/2 hours takes pretty long to install Ubuntu or amybe its just me :P

anyway plz list waht I should do just after reinstaling Ubuntu again? so I wouln't have to go over this again :D[/QUOTE]

Yeah, that's really quite long installation, maybe that's not you, that really depends on the speed of your PC. After you have installed Ubuntu successfully, go to this site [http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu").

---

### Post by X-Cannon on 2006-02-04
I have one last question after I've installed Ubuntu again how can I update it so that it has important things on it not useless things like language packs in germen etc... 

also I tried to plug in my mp3 player and Ubuntu said it was a Digital Camera and wanted me to put the "Pictures" in my album wahts that all about? Have you guys had this problem?

how can I fix this problem cause I might use a spare 80 gb HDD with a external case (USB) so I need to know how to fix thsi.

its damn late, sleep time 

THANK YOU GUYS FOR ALL THE HELP, I REALLY APPERIATE IT:-D ;)

---

### Post by Packard Dell on 2006-02-04
[QUOTE=X-Cannon]I have one last question after I've installed Ubuntu again how can I update it so that it has important things on it not useless things like language packs in germen etc... 

also I tried to plug in my mp3 player and Ubuntu said it was a Digital Camera and wanted me to put the "Pictures" in my album wahts that all about? Have you guys had this problem?

how can I fix this problem cause I might use a spare 80 gb HDD with a external case (USB) so I need to know how to fix thsi.

its damn late, sleep time 

THANK YOU GUYS FOR ALL THE HELP, I REALLY APPERIATE IT:-D ;)[/QUOTE]

Check out the website that i gave to you and you will find there how to update your Ubuntu. Go to the "4.1 How to add extra repositories" section first before you do some updates.

---

### Post by Virogenesis on 2006-02-04
Yeah also check out the link I gave you aswell I believe that site is easier to nav around compared to the wiki.

You should find that usb hard drive will auto detect and mount itself.
Linux does not support writting to NTFS so if it is going to be used with linux and windows make sure its fat32 that way you won't face any compatiablity issues.

---

### Post by chattanoga on 2006-02-04
I have installed Ubuntu maybe 5-6 times on the same computer; because I am a beginner who wants to learn by trial-and-error :D . 
The last time it took 30 minutes to install from CD (exactly the same time it took for Win2000, which I threw in as a dual-boot alternative before installing Ubuntu). Thereafter you have to "update" the system, just as for Windows, which might take 1-2 hours (depending on network speed).

This is how I do.
1. Dual boot (If you do not want Windows proceed to next step)
Create a partition (Gparted from the live-Ubuntu disk will work just fine) and install Windows first. 
2. Install Ubuntu form install-CD and let it do the partitioning automatically (30minutes)
3. Use Automatix to update/upgrade your system with missing applications and extended functionallity, go take a cup of coffee, it is virtually automatic and it is extremely user friendly! (1hour)
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

Voilá, you have a fully functional system.

Next thing I need to do is to shrink the Ubuntu-partition on HDA and create a new FAT32 partition which can be used by both OS:s. I have not figured out how to get Gparted to do that yet.


A really cool thing with Ubuntu (and many other distros) is that you update all your applications with synaptic (or terminal: apt-get update) whereas in windows, "Windows update" will only update the Windows components and the rest of your applications need special care individually.

---

### Post by xmastree on 2006-02-04
> Next thing I need to do is to shrink the Ubuntu-partition on HDA and create a new FAT32 partition which can be used by both OS:s. I have not figured out how to get Gparted to do that yet.
You need to boot from another source. If you boot normally, that partition contains the running OS, and can't be unmounted. If if can't be unmounted, it can't be resized.

---

### Post by John.Michael.Kane on 2006-02-04
Deleted wrong department

---

