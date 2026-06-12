---
title: "[SOLVED] copy/write to disk BY ANY MEANS??????????"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-12
Can this be done? Does anyone know how?

From local drive, to USB HDD???

Anybody?

Mr. Torvalds?

Help?

:confused:

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
ya

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
umm just for get a little give me a min 
what happens when you plug in the usb drive
what do you wanna copy

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> umm just for get a little give me a min 
what happens when you plug in the usb drive
what do you wanna copy

Device no longer shows when plugged in.

Just wanna' get data off of local drive, onto USB HDD.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **buccaneere said:**
> Device no longer shows when plugged in.

Just wanna' get data off of local drive, onto USB HDD.

so it used to show up?

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> so it used to show up?

yup.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
what doses 
```
fdisk -ls 
```
say
edit i think thats the code i :/ lol sorry sleepy

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> what doses 
```
fdisk -ls 
```
say
edit i think thats the code i :/

Disk /dev/sdb1: 80 G

xxx
xxx

/dev/sdb1             xxx             xxx                                  sys HPFS/NTFS

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
is that after you have your usb drive attached ? cuss it's only listing one hdd right now

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
and just copy  and past everything!! here
usallly theres more then that

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> is that after you have your usb drive attached ? cuss it's only listing one hdd right now

Yes. After pluggin' in USB device.

---

### Post by robinl on 2007-11-12
Your USB harddrive is not getting recognised. Can you please post the output of
```
lsusb
``` from terminal?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
just an idea dose the hard drive have a power switch on it or require external power 
make shur there plugin and on 

i know but its something i would do :) lol

---

### Post by buccaneere on 2007-11-12
> **robinl said:**
> Your USB harddrive is not getting recognised. Can you please post the output of
```
lsusb
``` from terminal?


bus 003 dev 001 ID 0000:0000
..    002        001      0000:0000
...   001 dev 017 ID 067b:2507        Prolif tech Inc.
...   001 dev 002 ID 0402:5602 Ali corp.
...   001        001 ID 0000:0000

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well i am out of my leage 
robinl would you take over lol
and i will learn from your wisdom

---

### Post by robinl on 2007-11-12
Is that the exact output? Try doing the command with the harddrive unplugged first and the with it plugged, to see if there's any difference between the two to see if your computer is detecting it.

Also, are you connecting the harddrive to frontpanel USB sockets or the ones at the back? Front panel ones vary a lot in quality and may not supply enough current to drive your harddrive. Try plugging it to the back and see if it works.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **robinl said:**
> Is that the exact output? Try doing the command with the harddrive unplugged first and the with it plugged, to see if there's any difference between the two to see if your computer is detecting it.

Also, are you connecting the harddrive to frontpanel USB sockets or the ones at the back? Front panel ones vary a lot in quality and may not supply enough current to drive your harddrive. Try plugging it to the back and see if it works.

so what do we do if it still dosent see it?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
hey now i know he has a web cam lol

---

### Post by robinl on 2007-11-12
> **<<joe>> said:**
> so what do we do if it still dosent see it?

Please post the output of lsusb before and after you plugged in your harddrive. 

PS. you can just select the text and right click in the terminal and select copy to avoid having to retype the output to here.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
i am not shur but this is your hdd?
... 001 dev 017 ID 067b:2507 Prolif tech Inc.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **robinl said:**
> Please post the output of lsusb before and after you plugged in your harddrive. 

PS. you can just select the text and right click in the terminal and select copy to avoid having to retype the output to here.

no its the other  guy with the problem 
buccaneere

---

### Post by buccaneere on 2007-11-12
> **robinl said:**
> Is that the exact output? Try doing the command with the harddrive unplugged first and the with it plugged, to see if there's any difference between the two to see if your computer is detecting it.

Also, are you connecting the harddrive to frontpanel USB sockets or the ones at the back? Front panel ones vary a lot in quality and may not supply enough current to drive your harddrive. Try plugging it to the back and see if it works.

USB unplugged = no data returned.

Plugged back in = 
Disk /dev/sdb:           80G
255 heads      63 sectors/track           9279 cyl
Units      =      cyls of 16065   *   512 = 8225280 bytes

Dev boot.......................start...................end..............blocks.............ID.......SYS
/dev/sdb1.......................1.....................9370.............78148608............7...HPFS/NTFS

terminal...

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **buccaneere said:**
> USB unplugged = no data returned.

Plugged back in = 
Disk /dev/sdb:           80G
255 heads      63 sectors/track           9279 cyl
Units      =      cyls of 16065   *   512 = 8225280 bytes

Dev boot.......................start...................end..............blocks.............ID.......SYS
/dev/sdb1.......................1.....................9370.............78148608............7...HPFS/NTFS

terminal...

what comand gave you that ?
lsusb 
fdisk

---

### Post by buccaneere on 2007-11-12
Machine is offline. I'm on a vistabox.

---

### Post by robinl on 2007-11-12
That doesn't look right... You have to type 
```
lsusb
```
into terminal with the drive unplugged and plugged and post it here for us to diagnose your problem. A typical output should look something like this:
```

Bus 003 Device 004: ID 058f:6362 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:0038 Microsoft Corp. SideWinder Precision 2
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 001 Device 008: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 007: ID 03f0:b402 Hewlett-Packard 
Bus 001 Device 006: ID 056a:00b1 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **buccaneere said:**
> Machine is offline. I'm on a vistabox.

oh

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> what comand gave you that ?
lsusb 
fdisk

Return given by 'fdisk -ls'.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **buccaneere said:**
> Return given by 'fdisk -ls'.

oh good !!! then all we have to do is mount it :)

---

### Post by buccaneere on 2007-11-12
lsusb return...


> **buccaneere said:**
> bus 003 dev 001 ID 0000:0000
..    002        001      0000:0000
...   001 dev 017 ID 067b:2507        Prolif tech Inc.
...   001 dev 002 ID 0402:5602 Ali corp.
...   001        001 ID 0000:0000

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
i don't know why its not automounting still but you can use this command to mount it
```
sudo mount /dev/sda1 /some/empty/folder   
```
then to unmount it use 
```
sudo umount /dev/sda1 
```
or
```
sudo umount /some/empty/folder 
```

note there is no n in umount for the unmount comand

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
as for makein auto mount work agin i have not had to do that yet soo i will have ask  google
but its lat and i dont wanna right now but thoughs comand i gave you should fix it for now

---

### Post by buccaneere on 2007-11-12
lsusb return UNPLUGGED:

bus 003 dev 001 ID 0000:0000
.... 002 ......001 ID 0000:0000
.... 001 dev  002 ID 0402:5602 Ali corp.
.... 001 ......001 ID 0000:0000

and plugged in...

bus 003 dev 001 ID 0000:0000
..... 002 .....001 ID 0000:0000
..... 001 dev 017 ID 067b:2507 Prolif tech Inc.
..... 001 dev 002 ID 0402:5602 Ali corp.
..... 001 ......001 ID 0000:0000

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
read the last few posts i think i got it figured out for now tell me if you under stand or should i explan more 
how do you have the commands out put's if you on diff computer

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
you got it ??

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> you got it ??

I was kinda' mindin' what robin was postin', after you said you were out of your league there...

Can you tell me anything by the LSUSB plugged in and unplugged return?


lsusb return UNPLUGGED:

bus 003 dev 001 ID 0000:0000
.... 002 ......001 ID 0000:0000
.... 001 dev 002 ID 0402:5602 Ali corp.
.... 001 ......001 ID 0000:0000

and plugged in...

bus 003 dev 001 ID 0000:0000
..... 002 .....001 ID 0000:0000
..... 001 dev 017 ID 067b:2507 Prolif tech Inc.
..... 001 dev 002 ID 0402:5602 Ali corp.
..... 001 ......001 ID 0000:0000


Only one USB port on the box. Drive was recognized when Linux file system was on it originally, then recognizing with NTFS formatting (fresh), but not since second re-format ext2 filesystem, and swap space assignment.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well the lsusb command just displays the stuff you computer can see on your usb and when you plug it in it sees it thats what this is
```
..... 001 dev 017 ID 067b:2507 Prolif tech Inc.

```

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> well the lsusb command just displays the stuff you computer can see on your usb and when you plug it in it sees it thats what this is
```
..... 001 dev 017 ID 067b:2507 Prolif tech Inc.

```

So how do I write to that thingy???

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
the fdisk is really what i was interested in becuses that is what can tell us if its mounted or not and if it even sees the usb device as a hdd from what you have given me it looks like it sees it in both and its just not mounting it for some reason ??? but i gave you commands to mount it manual 
you may need to adjust them a little bit though if the disk has multiple portions 
like sda1 sda2 ...

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well to right to a drive it needs to be mounted first so make a /some/empty/folder some ware and name it what ever you would like and the first command here is to mount and the others umount 


> **<<joe>> said:**
> i don't know why its not automounting still but you can use this command to mount it
```
sudo mount /dev/sda1 /some/empty/folder   
```
then to unmount it use 
```
sudo umount /dev/sda1 
```
or
```
sudo umount /some/empty/folder 
```

note there is no n in umount for the unmount comand

after its mounted all you have to do is put stuff in that folder

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
got it ?

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> well to right to a drive it needs to be mounted first so make a /some/empty/folder some ware and name it what ever you would like and the first command here is to mount and the others umount 




after its mounted all you have to do is put stuff in that folder

/some/empty/folder is where? Already on the local drive?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
i made up some emty folder i mean 
```
mkdir /home/"yourusername"/usbdrive
```

and then just replace /home/"yourusername"/usbdrive with the /some/file thing before
and yes its in the existing file system

---

### Post by buccaneere on 2007-11-12
I entered this:

sudo mount /dev/sda1 /some/empty/folder , 

where 'some/ empty/ folder' is an empty folder on my desktop.

then I entered this:

sudo umount /dev/sda1

Now my desktop icons are blank, and I don't have access to them (access denied).

**How do I reverse that?**

[SIZE="5"]**[COLOR="Red"]OKAY JOE - WHAT DID WE DO HERE? WE NEED TO VERY CAREFULLY BACK THIS TRAIN OUT OF THIS ALLEY...........[/COLOR]**[/SIZE]

---

### Post by buccaneere on 2007-11-12
...and how I back out before a disaster occurs?

[http://ubuntuforums.org/showthread.php?t=610453&page=5](http://ubuntuforums.org/showthread.php?t=610453&page=5)

If I reverse the very last 'umount' command (with a 'mount'), will I reverse the entire command, and it effect???

Please help on this one.........

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
sorry i was gone aaa to the bath room what did you do
sorry i left you

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
ok so 

this should fix everything back to the way it was 

```
sudo umount -a
```
then 
```
sudo mount-a
```

also what you probly did any way was turn the computer of and back on this should also fix the problem we just made

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
now back to the problem at hand perhaps I am not the best for explaining things i thought i was doin a good job
but i have to sleep soon so this is were i learned all of that
```
man mount
``` 
tells you more than we need to know 
i would allso look for a howto on mounting exteral harddrives 
i will be back tomarow to help you out but i got to go

---

### Post by buccaneere on 2007-11-12
> **<<joe>> said:**
> ok so 

this should fix everything back to the way it was 

```
sudo umount -a
```
then 
```
sudo mount-a
```

also what you probly did any way was turn the computer of and back on this should also fix the problem we just made

I haven't done anything since I entered

sudo umount /dev/sda1

That's when the icons went blank, and all local acces is denied. I NEED TO KNOW WITH ABSOLUTE CERTAINTY HOW TO REVERSE THAT. I CANNOT LOSE LOCAL DATA...

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> ...and how I back out before a disaster occurs?

[http://ubuntuforums.org/showthread.php?t=610453&page=5](http://ubuntuforums.org/showthread.php?t=610453&page=5)

If I reverse the very last 'umount' command (with a 'mount'), will I reverse the entire command, and it effect???

Please help on this one.........


bumpin' this

---

### Post by kpkeerthi on 2007-11-12
Can you post the post of the output of the commands below?

```

sudo fdisk -l

```
(this will list all the partitions you have)
and 

```

sudo mount

```
(this will list the partitions/devices mounted)

---

### Post by dnns123 on 2007-11-12
I not sure if I understand your thread. From what I assume, you want to copy something to/from your external HDD?

just go to add/remove and install NTFS config.
After isntalling it, go to applications --> system tools --> NTFS config

click on the box with external blah blah blah.

You should be able to write to/detect NTFS now. (not sure about detect though)

---

### Post by bulldog on 2007-11-12
I don't understand the problem entirely.

You want to copy your ubuntu to an external USB hdd?
You gave a umount and you're stuck?

Did you by any change umount your ubuntu where you're working with? [sda1]

---

### Post by Samhain13 on 2007-11-12
I was reading the other thread and waiting for solutions, just a bit curious. But from what I understand, won't a simple restart put things in order since Buccaneere didn't edit and save his fstab anyway?

When you've restarted (and hopefully, things are put back in order), to try the other guy's (from the other thread) suggestion, you need to create a directory first so that you'll have a place to mount to. Try:

```

mkdir myUSBdrive

```

this will make a "myUSBdrive" folder/sub-directory in your home directory. Then, as in the other thread, mount your drive to that directory by doing:

```

mount /dev/sda myUSBdrive

```

which basically says, "mount my drive to the directory I created earlier." Then you can copy, move and/or create files in your external drive by copying, moving and/or creating files in your newly created myUSBdrive directory.

To unmount the drive when you're done using it:

```

umount myUSBdrive

```

---

### Post by buccaneere on 2007-11-12
No. 

I Have To First Find Out How To Back Out Of The Fix That I Was Just Led Into, Before Data Is Lost.

**[http://ubuntuforums.org/showthread.php?p=3755100#post3755100](http://ubuntuforums.org/showthread.php?p=3755100#post3755100)**

---

### Post by bulldog on 2007-11-12
If you simply gave a umount command for the partition you're working with,just reboot.
If you did actual edit the fstab.wait a moment.

---

### Post by kpkeerthi on 2007-11-12
Looks like you mounted your NTFS partition (external disk) to a folder on desktop. After unmounting the partition you just lost the icons from the desktop. 

If this is the case, things should be fine after rebooting. But just to be sure, why don't you respond to my queries above?

---

### Post by buccaneere on 2007-11-12
> **bulldog said:**
> If you simply gave a umount command for the partition you're working with,just reboot.
If you did actual edit the fstab.wait a moment.

I'm on another machine.

On the ubuntu machine, I've done nothing since the last umount' command, and the desktop icons went blank and access was lost.

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> Can you post the post of the output of the commands below?

```

sudo fdisk -l

```
(this will list all the partitions you have)
and 

```

sudo mount

```
(this will list the partitions/devices mounted)

I've done nothing on that machine since I entered the umount command, and lost the local access, and desktop icons.

That's why I can't respond to those queries...

I'm another machine.

---

### Post by kpkeerthi on 2007-11-12
Have you rebooted since then? If not do it now. Unmount will not erase any data from the partition. As long as you did not mess up with your /etc/fstab entries, all your partitions should get mounted properly upon reboot.

Do not mount any filesystem on to your desktop. If you wish, always mount to /media/some-folder

---

### Post by Samhain13 on 2007-11-12
Did you, or did you not do anything to your fstab?

---

### Post by bulldog on 2007-11-12
[b]Which partition did you umount??? whas it the partition ubuntu is installed ergo you where working with??
Did you or did you not,edit the fstab??
Please answer these questions to get things solved[/b]

Or tell at least which partition you did umount,but I,m pretty sure it was the ubuntu partition.
If that's the fact and ** you did not edit the fstab** just reboot.

By umounting you won't lose data.

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> Have you rebooted since then? If not do it now. Unmount will not erase any data from the partition. As long as you did not mess up with your /etc/fstab entries, all your partitions should get mounted properly upon reboot.

Do not mount any filesystem on to your desktop. If you wish, always mount to /media/some-folder

No, I haven't rebooted. I've done nothing...

I entered no commands related to  etc / fstab  entries, before, or after.

'Umount' only, will not erase ANY data? From ANY partition?

---

### Post by bulldog on 2007-11-12
> **buccaneere said:**
> No, I haven't rebooted. I've done nothing...

I entered no commands related to  etc / fstab  entries, before, or after.

'Umount' only, will not erase ANY data? From ANY partition?

No it won't erase anything,by rebooting your partitions will be mounted as before **if you did not edit fstab that is**

---

### Post by buccaneere on 2007-11-12
Re-booted.

Data intact. Thanks/good job helpers.

WWWWWWWWHHHHHHHHHHEEEEEEEEEEEEWWWWWWWWWWWWWWWWW!!!!!!!!

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> I haven't done anything since I entered

sudo umount /dev/sda1

That's when the icons went blank, and all local acces is denied. I NEED TO KNOW WITH ABSOLUTE CERTAINTY HOW TO REVERSE THAT. I CANNOT LOSE LOCAL DATA...

[COLOR="Red"]Data not lost; back to original problem - USB HDD not accessed/mounted/writeable...[/COLOR]

---

### Post by kpkeerthi on 2007-11-12
Which version of ubuntu are you using? Gutsy? or Edgy (as I read from your user information)? 

Reply back if you still need help copying data to your external NTFS disk.

---

### Post by kpkeerthi on 2007-11-12
Which version of ubuntu are you using? Gutsy? Feisty or Edgy?

---

### Post by kpkeerthi on 2007-11-12
If your are using Gutsy,
 
1. Make a folder in /media/
```

sudo -i
cd /
mkdir /media/windows

```
 
2. Mount the partition to the folder you just created:
```

mount -t ntfs-3g /dev/sda1 /media/windows

```
 
This should bring an icon on your desktop. Then copy your files and unmount:
 
```

umount /dev/sda1

```
 
[COLOR=red]**THIS WILL WORK ONLY IN GUTSY. YOU NEED TO MANUALLY INSTALL NTFS-3G OTHERWISE**[/COLOR]

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> Which version of ubuntu are you using? Gutsy? or Edgy (as I read from your user information)? 

Reply back if you still need help copying data to your external NTFS disk.

Attempted to load NTFS-config; but was unsuccessful for dependency error. 

Attempt to load python 2.5.1 [dependency error] was unsuccessful.

Disk was then formatted from NTFS, to ext2 file system, and swapspace assigned (successfully). Last known 'proper' execution. 

Mount then 'evaporated' - and isn't seen properly now at USB port...

---

### Post by kpkeerthi on 2007-11-12
I don't understand. Your reply does not seem to be inline with my question. I have responded to your post in the OTHER thread.

---

### Post by bapoumba on 2007-11-12
Threads merged.

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> Which version of ubuntu are you using? Gutsy? Feisty or Edgy?

I have edgy loaded on the machine. 6.10.

---

### Post by kpkeerthi on 2007-11-12
You need to install ntfs-3g.
```

sudo aptitude install ntfs-3g

```

And then follow my instructions in the last page.
[http://ubuntuforums.org/showpost.php?p=3755307&postcount=68](http://ubuntuforums.org/showpost.php?p=3755307&postcount=68)

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> You need to install ntfs-3g.
```

sudo aptitude install ntfs-3g

```



Package not found.

I could not earlier burn ntfs-config to a CD to load onto the Ubuntu box. Windows referred to a new DVD+R as an unwriteable disc (several). This machine is also new.

I saved ntfs-config to an external HDD, and tried to load it through the mounted USB port, onto the Ubuntubox.

THAT is when the dependency error was tripped [for python2.5].

Python2.5.1 would not load, that I could tell.


That's when I formatted the HDD in ext2 filesystem, and successfully assigned swapspace. USB-mount then disappeared...

---

### Post by kpkeerthi on 2007-11-12
Do you have [universe repository ]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")enabled?

---

### Post by buccaneere on 2007-11-12
> **kpkeerthi said:**
> Do you have [universe repository ]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")enabled?

What about suppositories???:shock:


JK...

I don't the answer to that question. 

Is [are] the sources on the local machine, or the web?

---

### Post by kpkeerthi on 2007-11-12
[https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

---

### Post by kpkeerthi on 2007-11-12
It is a good idea to read through the Ubuntu Desktop Guide if you want use your system effectively... You will have the most basic questions answered in this document. 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

---

### Post by steve.horsley on 2007-11-12
I would also like to add that he should be trying to mount /dev/sdb1 not /dev/sda1 (see page 2 of this thread where he gives a partial fdisk -l output.

Buccaneere: When you are asked for the output of a command, it would be better if you posted the whole thing. In trying to filter what you think is not relevant, you could be removing something quite important. I.e. one of your posts kind of suggests that you don't have a hard disk at all, whcih I don't believe. I'm sure that sudo fdisk -l must list something when your external drive is not plugged in. 

Unfortunately, I don't know how to get nffs-3g running, but I do know that this is needed to be able to write to ntfs partitions.

---

### Post by buccaneere on 2007-11-12
The Ubuntu machine in not online.

Is there no format I can execute to the HDD, such that I can mount it, and transfer files to it?

I attempted to format ext2 file system, but got no further than swapfile assignment.

---

### Post by buccaneere on 2007-11-12
Any way to format it, to make it accessible?

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> Any way to format it, to make it accessible?

Any way to format a drive, to make it accessible???

---

### Post by buccaneere on 2007-11-12
bumpin again...

Why is this so hard?

---

### Post by buccaneere on 2007-11-12
Still need help here...


Few solitaires, few free cells...

Hello?

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> Still need help here...


Few solitaires, few free cells...

Hello?

todatopagin',,,

few more free cells, sotares...

cursor pixels are busy...

whiskers gettin' longer...

bill g's rakin it in...






anyone?

---

### Post by buccaneere on 2007-11-12
bak2topagin...

c'mon folks - someone's got a solution, I know....................

---

### Post by Whiffle on 2007-11-12
when you plug it in, what is the output of 'dmesg'?  It should say somethind about your device being plugged in, and then scanning it and such.

---

### Post by buccaneere on 2007-11-12
> **Whiffle said:**
> when you plug it in, what is the output of 'dmesg'?  It should say somethind about your device being plugged in, and then scanning it and such.


Hi whiffle...

No pop-up icon/message/nothin', when I plug in.

From the terminal, several pages of info after enterin' dmesg!!!

[COLOR="Red"]
Copyin' info; gimme a minute...[/COLOR]

---

### Post by Whiffle on 2007-11-12
You may have to wait a bit to get all the info and then run dmesg again, assuming things are working correctly only the last 10 lines or so will probably be relevant.

---

### Post by buccaneere on 2007-11-12
last 20 lines of info on dmesg...

17182843:844000 usb 1 -1: usb disconnect, address 2
.......................................device using ehci_hcd and address 4
.......................................config #1 chosen from 1 choice
.......................................device found at 4
.......................................waiting for device to settle before scanning
.......................................scan complete
.......................................vendor
.......................................type
17182876.216000.................device sdb 156301487  512-byte sectors 80kMB
.......................................dev write protect off
.......................................dev mode sense 03 00 00 00
.......................................dev - assuming drive cache - write through
17182876.220000.................device sdb 156301487  512-byte sectors 80kMB
.......................................dev write protect off
.......................................dev mode sense 03 00 00 00
.......................................dev - assuming drive cache - write through
.......................................dev (sdb): sdb1
.......................................sd 03 00 00 00 attached disk sdb
.......................................sd 03 00 00 00 attached generic sgl type 0

---

### Post by bulldog on 2007-11-12
> **buccaneere said:**
> Hi whiffle...

No pop-up icon/message/nothin', when I plug in.

From the terminal, several pages of info after enterin' dmesg!!!

[COLOR="Red"]
Copyin' info; gimme a minute...[/COLOR]

I think nobody is going to read so many pages to filter out your problem.
Better start a new and fresh topic,with a short disctription of the problem.
That said,you're not the only one who needs some help,so be a little patient.

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> last 20 lines of info on dmesg...

17182843:844000 usb 1 -1: usb disconnect, address 2
.......................................device using ehci_hcd and address 4
.......................................config #1 chosen from 1 choice
.......................................device found at 4
.......................................waiting for device to settle before scanning
.......................................scan complete
.......................................vendor
.......................................type
17182876.216000.................device sdb 156301487  512-byte sectors 80kMB
.......................................dev write protect off
.......................................dev mode sense 03 00 00 00
.......................................dev - assuming drive cache - write through
17182876.220000.................device sdb 156301487  512-byte sectors 80kMB
.......................................dev write protect off
.......................................dev mode sense 03 00 00 00
.......................................dev - assuming drive cache - write through
.......................................dev (sdb): sdb1
.......................................sd 03 00 00 00 attached disk sdb
.......................................sd 03 00 00 00 attached generic sgl type 0

bumped... 

thanks dog. Lotta wanna be helpers clog up the thread tho, when the real helpers are lookin for my replies... Just no good..........................

---

### Post by Whiffle on 2007-11-12
Alrite, so its finding it.  I see that you say you've formatted it in ext2, lets check to be sure by trying to mount it as ntfs and ext2.  As far as I know, you should be able to read ntfs w/o ntfs-3g.

lets do this the full manual way, just to make sure things are working:
```

#make a directory to mount it to
sudo mkdir /media/newdrive

#mount
sudo mount -t ntfs /dev/sdb1 /media/newdrive

#if that doesn't work

sudo mount -t ext2 /dev/sdb1 /media/newdrive

sudo ls /media/newdrive


```

If that works, you should be able to see your files.  If not, then we may just have to format it as ext3 and move on.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
hey buccaneere  did you get it yet or what :)

---

### Post by buccaneere on 2007-11-12
> **Whiffle said:**
> Alrite, so its finding it.  I see that you say you've formatted it in ext2, lets check to be sure by trying to mount it as ntfs and ext2.  As far as I know, you should be able to read ntfs w/o ntfs-3g.

lets do this the full manual way, just to make sure things are working:
```

#make a directory to mount it to
sudo mkdir /media/newdrive

#mount
sudo mount -t ntfs /dev/sdb1 /media/newdrive

#if that doesn't work

sudo mount -t ext2 /dev/sdb1 /media/newdrive

sudo ls /media/newdrive


```
If that works, you should be able to see your files.  If not, then we may just have to format it as ext3 and move on.


new directory successful

error return mount ntfs, and mount ext2 = wrong file system, bad option, bad super block on disk, no codepage or other error.

What is 'dmesg' | tail or so' ??? (for more info from syslog)

No files on disk to protect. What's format ext3 sequence?

---

### Post by Whiffle on 2007-11-12
dmesg | tail   just pipes the output of dmesg through tail, and tail is a program that just outputs the last part of a file.  More info in 'man tail'

To format it as ext3 (which is what I would use, windows can read it with this driver:  [http://www.fs-driver.org/](http://www.fs-driver.org/)


```

#we'll start with fdisk
fdisk /dev/sdb

#in here, what we're going to do is delete all partitions on the drive, and add a new one
d  # delete partition (it'll ask you which one or something, I dont remember exactly)
n  # make new partition.  by default, it sets partitions to a linux type, which is what we want.
w # write changes to disk
q  # quit fdisk

# and now to format
mkfs.ext3  /dev/sdb1

#mount
sudo mount -t ext3 /dev/sdb1 /media/newdrive


```

That should get it formatted as ext3.  Hopefully the next time you plug it in it will work correctly, although I can't remember how well ubuntu handles automounting ext3.  *crosses fingers*

---

### Post by buccaneere on 2007-11-12
> **Whiffle said:**
> dmesg | tail   just pipes the output of dmesg through tail, and tail is a program that just outputs the last part of a file.  More info in 'man tail'

To format it as ext3 (which is what I would use, windows can read it with this driver:  [http://www.fs-driver.org/](http://www.fs-driver.org/)


```

#we'll start with fdisk
fdisk /dev/sdb

#in here, what we're going to do is delete all partitions on the drive, and add a new one
d  # delete partition (it'll ask you which one or something, I dont remember exactly)
n  # make new partition.  by default, it sets partitions to a linux type, which is what we want.
w # write changes to disk
q  # quit fdisk

# and now to format
mkfs.ext3  /dev/sdb1

#mount
sudo mount -t ext3 /dev/sdb1 /media/newdrive


```

That should get it formatted as ext3.  Hopefully the next time you plug it in it will work correctly, although I can't remember how well ubuntu handles automounting ext3.  *crosses fingers*

Now I'm gettin' the warning related to partitions (to ignore).

What's the entry to start deletin' all of the partitions?

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> Now I'm gettin' the warning related to partitions (to ignore).

What's the entry to start deletin' all of the partitions?


I enter 'd', and 'enter'. The return is 'no partition is defined yet'.

Does that mean there are no partitions existing now on the disk, or does that mean I have not defined an existing partition to delete???

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> I enter 'd', and 'enter'. The return is 'no partition is defined yet'.

Does that mean there are no partitions existing now on the disk, or does that mean I have not defined an existing partition to delete???


bak2datopagain:)

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> I enter 'd', and 'enter'. The return is 'no partition is defined yet'.

Does that mean there are no partitions existing now on the disk, or does that mean I have not defined an existing partition to delete???

Hello?

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> I enter 'd', and 'enter'. The return is 'no partition is defined yet'.

Does that mean there are no partitions existing now on the disk, or does that mean I have not defined an existing partition to delete???


AHOY, MATEYS!!!

I'M BACK!

---

### Post by Whiffle on 2007-11-12
Looks like there aren't any partitions to delete, so go ahead and make a new one.

---

### Post by buccaneere on 2007-11-12
> **Whiffle said:**
> Looks like there aren't any partitions to delete, so go ahead and make a new one.

I wrote out (write and exit), and return was 'failure; kernel still in use'. Permission problem.

Kernel still using old table.

???

---

### Post by buccaneere on 2007-11-12
> **buccaneere said:**
> I wrote out (write and exit), and return was 'failure; kernel still in use'. Permission problem.

Kernel still using old table.

???

What does that mean?

---

### Post by buccaneere on 2007-11-12
Yikes - 13th thread down. No good.

upandatem - numbah 1.........

Anyone/body/thing/dice/coin flip/tarot card/monkey on keyboard/???

---

### Post by buccaneere on 2007-11-13
**[COLOR="Navy"]ENERGIZER BUNNY IS BACK AGAIN!!![/COLOR]**

Little help folks...

---

### Post by buccaneere on 2007-11-13
> **buccaneere said:**
> I wrote out (write and exit), and return was 'failure; kernel still in use'. Permission problem.

Kernel still using old table.

???


REBOUND!!!

What is stopping me from modifying the partitions? What kernal? What table?

Hello? Don't be scared...

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
whats up?
to much reading sence last time i look here

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
so were formating a usb hdd right

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
just use gparted i know your ubuntu comp is not on line but its on the livecd 
so with the cd as a resorce
sudo apt-get install gparted
then gksudo gparted
if you get it installed or boot with live cd i will walk you through it

---

### Post by buccaneere on 2007-11-13
tryin' to delete partitions in the drive, and find out what kernels are using what tables.

Will zeroing out the MBR accomplish this?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
wow slow down
whats not working
your mbr no doing something to it may be help full but not zeroing it out (and in this case i dont think at all helpfull)
what about kernels and tables why do you need this to delete partitons in the drive ???

---

### Post by buccaneere on 2007-11-13
> **<<joe>> said:**
> wow slow down
whats not working
your mbr no doing something to it may be help full but not zeroing it out (and in this case i dont think at all helpfull)
what about kernels and tables why do you need this to delete partitons in the drive ???

'Partition table cannot be deleted on this drive because tables are being used by kernel'.

What kernel? What table?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
ya thats what i was thinking
what code generated that error out put

were trying to delete the partions on your external hard drive that ubuntu is not installed on right?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
I think your best bet is to stop everything your doing and reboot with the usb drive unhooked
then use fdisk to make the ext2 or ext3 partition after pluging in the usb drive
really think your over complicating things

---

### Post by buccaneere on 2007-11-13
> **<<joe>> said:**
> I think your best bet is to stop everything your doing and reboot with the usb drive unhooked
then use fdisk to make the ext2 or ext3 partition after pluging in the usb drive
really think your over complicating things


Make partitions??? 

You're not getting it. There is ***only READ access ***to this disk, and it cannot be changed, because there is a kernel using a table, which is in one of the partitions.

I'm trying to delete the partitions. Then, and only then, IF AT ALL, can I create partitions and file systems.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
nope i get it you dont restart your computer with the hdd not pluged in if it starts the kernal thats running dosent need it so then you can just format the thing

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
do you know what a kernel is?
maybe i am confused but there should be only one kernel running on you computer at a time unless you have some virtuization going on

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
To make things extreamly simple this is what i would do
1. Shutdown computer
2. dissconnect all hard drives
3. connect the usb hdd
4. boot liveCD
5 System > Administration > Partition Editor
6. Delete all partitions by right clicking them and then click delete 
7  make new partition by right clicking free space and then click new partion
8 configure partion - should be able to figure this part out on your own
9 click apply and wait

I would like you to try this

you cant get the kernel error because the kernel you were useing is not running anymore
the one on the live cd is
i would format in ext3 
a nother bonus to using the live cd is i dont have to figure out whats rong with your system kuss were just going to wippe the drive

but befor i did this i would make shur you can boot with out it

note* after 7.10 gparted likes to crash but only after it does the work you told it to so just start it back up if it does, the crash of gparted in this way will not affect your system

---

### Post by steve.horsley on 2007-11-13
Before you start reformatting drives, I'd really like to check we are reformatting the right one. Please can we have the full output from the command
**sudo fdisk -l**
firstly wiith the USB drive not plugged in, and again after it has been plugged in.
That way we can be really sure which drive is which.

---

### Post by buccaneere on 2007-11-13
> **steve.horsley said:**
> Before you start reformatting drives, I'd really like to check we are reformatting the right one. Please can we have the full output from the command
**sudo fdisk -l**
firstly wiith the USB drive not plugged in, and again after it has been plugged in.
That way we can be really sure which drive is which.

Something changed with recognition, but here's what's showin' now...

[COLOR="Red"]Without USB plugged in:[/COLOR]
disk /dev/sda: 120G 120034123776 bytes
255 heads 63 sectors/track 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Dev...........boot........start...........end.......blocks........ID.....system
dev/ sda1...................1............1019.......8185086......12....compaq diagnostics
...........2....*.............1020........8528.....60315769+....6.....Fat 16
...........3...................9391.......14378....40066110.....83....Linux
...........4...................14379......14593....1726987+.....5....Extended
...........5...................14379......14593.....1726956.....82....linux swap/solaris

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
hey can you get the ubuntu computer online it would be so much easier that way

---

### Post by buccaneere on 2007-11-13
> **buccaneere said:**
> Something changed with recognition, but here's what's showin' now...

[COLOR="Red"]Without USB plugged in:[/COLOR]
disk /dev/sda: 120G 120034123776 bytes
255 heads 63 sectors/track 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Dev...........boot........start...........end.......blocks........ID.....system
dev/ sda1...................1............1019.......8185086......12....compaq diagnostics
...........2....*.............1020........8528.....60315769+....6.....Fat 16
...........3...................9391.......14378....40066110.....83....Linux
...........4...................14379......14593....1726987+.....5....Extended
...........5...................14379......14593.....1726956.....82....linux swap/solaris

[COLOR="Red"]...and with the drive plugged in...[/COLOR]

[above], 

plus:

Disk /dev/sdb : 80 G,    80026361344  bytes
255 heads 63 sectors / track  9729 cylinders
Units = cylinders of   16065  *  512 = 8225280 bytes

Device.....boot.............start..........end...............blocks.......ID......system
/sdb1..........*..............1..............9545.............76670181....83......linux
/sdb2..........................9546.........9729..............1477980......5......Extended
/sdb5..........................9546.........9729..............1477948+...82......linux swap / Solaris

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-14
Hello I urge you to use gparted i could what you right through that with out any problems

but if you dont wanna use gparted heres my best shot at exactly what you will have to type to get 
your hdd cleared and make really big part of the howl thing 
```
sudo fdisk /dev/sdb
d /sdb1
d /sdb2
d /sdb5
n
p
1
   #  just press enter here to used default value
   #  just press enter here to use the remainder of the disk

```

now i am not shure here but fdisk should help you out its ether 
```
t 1 
83
w

```

or

```
t 
1
83
w

```
i just for get 	

By typing w, you are permanently destroying any data that currently exists on the device. If you need wish to preserve any data, type q to exit the program without altering the disk and back up your data. 

if this is what you did before and got that error from the kernel then its a problem i dont know how to fix

however if you boot the livecd you can just use gparted or do this there and then the kernel can't be messing with this disk

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-14
then we have to do this ```
sudo mkfs -t ext3 /dev/sdb1
```
edit : oh that may need a sudo infront of it

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-14
now make a new emty dir and mount the hdd

```
mkdir ~/usbdrive
sudo mount /dev/sdb1 ~/usbdrive
```

now copy file into ~/usbdrive
 
make shure you can read the files
and if all goes well

```
 umount ~/usbdrive
```

then the file should disapper from ~/usbdrive

if you would like to access the drive you will need to mount it agin

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-14
This was vary step by step if it dosent work then you have other problems that are over my head
and i would use the live cd to set up this disk you can even use the live cd on your vista box to set up this disk would be very good cuss then you have copy past options and can post here.
how ever you may wanna dissconnect you hdd with vsta on it so you can't mess that up :)

---

### Post by buccaneere on 2007-11-14
thanks there joe, I appreciate your perserverance.

That's what I though I needed to do before, but the issue is of root ownership of the device.

What code do I enter to execute root ownership to [user]???






EDIT:
From another forum...

Quote:
> Originally Posted by RobLinux
There's a swap partition drive, he should check :

swapon -s

To see if the kernel is using that swap space, which will prevent writes, to avoid a panic.

swapoff /dev/<swapdevice>

May stop the disk being used and allow writes to partition table. This can happen sometimes even with Live CD's. 


Excellent observation.

This is apparently why I have been unsuccessful at deleting partitions (although I don't know that I even executed properly).

The return message, when entering 'w', to save and exit the deletions, was [paraphrase] cannot be done/permission denied/kernel is using table.

What exactly does this mean, and how do we terminate this process. This is an ownership function. 

Correct?

Thanks again............


EDIT: This means that my on-board processor is communicating with the file allocation table on the external drive boot sector, and determining ownership of the drive.

Correct? 
__________________

---

### Post by buccaneere on 2007-11-14
2 Hours Ago  
buccaneere  
A Carafe of Ubuntu
   Join Date: Nov 2007
Location: eastern NC
Beans: 105
Ubuntu 6.10 Edgy User 

 
Re: copy/write to disk BY ANY MEANS?????????? 

--------------------------------------------------------------------------------

thanks there joe, I appreciate your perserverance.

That's what I though I needed to do before, but the issue is of root ownership of the device.

What code do I enter to execute root ownership to [user]???






EDIT:
From another forum...

Quote:

> 
Originally Posted by RobLinux
There's a swap partition drive, he should check :

swapon -s

To see if the kernel is using that swap space, which will prevent writes, to avoid a panic.

swapoff /dev/<swapdevice>

May stop the disk being used and allow writes to partition table. This can happen sometimes even with Live CD's.  


Excellent observation.

This is apparently why I have been unsuccessful at deleting partitions (although I don't know that I even executed properly).

The return message, when entering 'w', to save and exit the deletions, was [paraphrase] cannot be done/permission denied/kernel is using table.

What exactly does this mean, and how do we terminate this process. This is an ownership function. 

Correct?

Thanks again............


EDIT: This means that my on-board processor is communicating with the file allocation table on the external drive boot sector, and determining ownership of the drive.

Correct?

---

### Post by buccaneere on 2007-11-14
EDIT:
From another forum...

Quote:


> Quote:
Originally Posted by RobLinux
There's a swap partition drive, he should check :

swapon -s

To see if the kernel is using that swap space, which will prevent writes, to avoid a panic.

swapoff /dev/<swapdevice>

May stop the disk being used and allow writes to partition table. This can happen sometimes even with Live CD's.  


Excellent observation.

This is apparently why I have been unsuccessful at deleting partitions (although I don't know that I even executed properly).

The return message, when entering 'w', to save and exit the deletions, was [paraphrase] cannot be done/permission denied/kernel is using table.

What exactly does this mean, and how do we terminate this process. This is an ownership function. 

Correct?

Thanks again............


EDIT: This means that my on-board processor is communicating with the file allocation table on the external drive boot sector, and determining ownership of the drive.

Correct?

---

### Post by buccaneere on 2007-11-15
EDIT:
From another forum...

Quote:



> 
Originally Posted by RobLinux
There's a swap partition drive, he should check :

swapon -s

To see if the kernel is using that swap space, which will prevent writes, to avoid a panic.

swapoff /dev/<swapdevice>

May stop the disk being used and allow writes to partition table. This can happen sometimes even with Live CD's.  


Excellent observation.

This is apparently why I have been unsuccessful at deleting partitions (although I don't know that I even executed properly).

The return message, when entering 'w', to save and exit the deletions, was [paraphrase] cannot be done/permission denied/kernel is using table.

What exactly does this mean, and how do we terminate this process. This is an ownership function. 

Correct?

Thanks again............


EDIT: This means that my on-board processor is communicating with the file allocation table on the external drive boot sector, and determining ownership of the drive.

Correct?

---

### Post by buccaneere on 2007-11-15
What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size............used................priority
/dev/sda5.............partition....1726948......0....................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

---

### Post by buccaneere on 2007-11-15
> **buccaneere said:**
> What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size............used................priority
/dev/sda5.............partition....1726948......0....................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

bumpin'...

---

### Post by buccaneere on 2007-11-15
> **buccaneere said:**
> What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size............used................priority
/dev/sda5.............partition....1726948......0....................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

b...

---

### Post by buccaneere on 2007-11-15
What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size.......... ..used................priority
/dev/sda5.............partition....1726948......0. ...................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

---

### Post by buccaneere on 2007-11-15
Originally Posted by buccaneere  
What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size.......... ..used................priority
/dev/sda5.............partition....1726948......0. ...................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

---

### Post by buccaneere on 2007-11-15
Originally Posted by buccaneere 
What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size.......... ..used................priority
/dev/sda5.............partition....1726948......0. ...................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

---

### Post by KIAaze on 2007-11-15
Hey, cool down!
No need to post 7 times the same text in a row in less than an hour!

I'll have a look at your problem.
And all those whio have posted here are probably still following your post too if they had automatic subscription on.

If you want real-time help (altough the beginner's section is often instant help), you'd better go on the ubuntu IRC. ;)
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")

It's also reasonable to wait at least 24 hours before bumping again.

---

### Post by buccaneere on 2007-11-15
> **KIAaze said:**
> Hey, cool down!
No need to post 7 times the same text in a row in less than an hour!

I'll have a look at your problem.
And all those whio have posted here are probably still following your post too if they had automatic subscription on.

If you want real-time help (altough the beginner's section is often instant help), you'd better go on the ubuntu IRC. ;)
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")

It's also reasonable to wait at least 24 hours before bumping again.

Sounds great there, KIAaze!

I just wanna' copy to disk. 

Although I think I could write code to solve for Pi, before I get write access...

---

### Post by jw5801 on 2007-11-15
Try booting into the GParted LiveCD (find a link in my signature) and use it to wipe the drive and make it into one ext3 partition (I'm assuming you only want it for storage?). At the moment it appears like an installer has tried to put a linux system on the external drive. Or else your system is using the swap on the drive for some reason.

Booting from the LiveCD is the best method you can have for any kind of partition editing! Try that and report back.

---

### Post by SpiritIsReality on 2007-11-15
howdy
how's it going

---

### Post by buccaneere on 2007-11-15
> **SpiritIsReality said:**
> howdy
how's it going


Nope.



Re: copy/write to disk BY ANY MEANS?????????? 

--------------------------------------------------------------------------------

What is the command, to stop a kernel on the local drive from communicating with a file table on the USB drive.

swapon -s returned:

Filename..............type..........size.......... ..used................priority
/dev/sda5.............partition....1726948......0. ...................-1

What exactly does this mean? What am I asking? What am I knowing?

swapoff /dev/<swapdevice>??? What does 'swap' mean? What IS the swapdevice?

How do I assign self-ownership?

I have <10hrs of exposure to open-source. 

How do I write to this external disk?

---

### Post by buccaneere on 2007-11-15
mount attempt from root console:

root @ abc... mount /dev/sdb1 /mnt

return:

wrong file system type, bad option, bad superblock on device1, missing code page, or other error



get additional info at dmesg | tail [following]


FAT: utf 8 is not recommended IO charset for FAT; case sensitive warning...

ext2 fs error - (on device1) ext2 check descriptors - block bit error

group descriptors corrupted also...

Can anyone help?

---

### Post by jw5801 on 2007-11-15
Refer to my previous post! **Boot into the GParted LiveCD, wipe the disk, make it into one big ext3 partition and you should be ok.** Have you tried this? What happens when you try? The messages you're reporting above are telling you the filesystem on this disk is corrupt. The easiest way to deal with this is to wipe it and start again since there's nothing on there you want to keep.

---

### Post by buccaneere on 2007-11-15
> **jw5801 said:**
> Refer to my previous post! **Boot into the GParted LiveCD, wipe the disk, make it into one big ext3 partition and you should be ok.** Have you tried this? What happens when you try? The messages you're reporting above are telling you the filesystem on this disk is corrupt. The easiest way to deal with this is to wipe it and start again since there's nothing on there you want to keep.

I'm in the absolute beginner thread, because I'm an absolute beginner.

"Boot into the GParted CD", means nothing to me.

Is that an app on the edgy eft live disk? Did it load when I installed the OS? Does it need to be extracted from somewhere? Downloaded? (the machine is not online, so that option is unavailable).

Wow. More questions now, than when I posted.:confused:

But thanks for tryin' anyway.............

Anybody help me get this drive wiped/formatted? I just need a few lines of code.

Anybody?

---

### Post by 900donuts on 2007-11-15
boot into gparted cd means you burn live cd with gparted on it (i fact gparted has released there own gparted cd) [http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

---

### Post by jw5801 on 2007-11-15
> **buccaneere said:**
> I'm in the absolute beginner thread, because I'm an absolute beginner.

"Boot into the GParted CD", means nothing to me.

Is that an app on the edgy eft live disk? Did it load when I installed the OS? Does it need to be extracted from somewhere? Downloaded? (the machine is not online, so that option is unavailable).

Wow. More questions now, than when I posted.:confused:

But thanks for tryin' anyway.............

Anybody help me get this drive wiped/formatted? I just need a few lines of code.

Anybody?

Yes download their LiveCD from the link in my signature, not necessarily using your Ubuntu machine: you're not installing anything so it doesn't matter. Burn the .iso to CD and boot from it just like you did with the Ubuntu install CD. Once it's up and running open GParted (the GNOME partition editor) and you should be able to see the drive. Delete all the partitions you can see on there to completely wipe the drive, then reformat it as ext3. That should be all you need to do. GParted will be present on the Edgy LiveCD if that's the CD you have, but their own LiveCD is a much newer, more improved version, which is why I suggest using it.

Sorry to sound short, but I posted the suggestion and instead of saying you didn't understand you reposted something you had already posted and said the problem was unchanged- I thought you were just ignoring me! It would appear that the problem can't be solved with "just a few lines of code" because your system is trying to use the disk for something, preventing you from unmounting the disk, therefore we want to try and wipe it in an environment where your system isn't present, thus the suggestion of using the LiveCD.

---

### Post by buccaneere on 2007-11-15
> **jw5801 said:**
> Yes download their LiveCD from the link in my signature, not necessarily using your Ubuntu machine: you're not installing anything so it doesn't matter. Burn the .iso to CD and boot from it just like you did with the Ubuntu install CD. Once it's up and running open GParted (the GNOME partition editor) and you should be able to see the drive. Delete all the partitions you can see on there to completely wipe the drive, then reformat it as ext3. That should be all you need to do. GParted will be present on the Edgy LiveCD if that's the CD you have, but their own LiveCD is a much newer, more improved version, which is why I suggest using it.

Sorry to sound short, but I posted the suggestion and instead of saying you didn't understand you reposted something you had already posted and said the problem was unchanged- I thought you were just ignoring me! It would appear that the problem can't be solved with "just a few lines of code" because your system is trying to use the disk for something, preventing you from unmounting the disk, therefore we want to try and wipe it in an environment where your system isn't present, thus the suggestion of using the LiveCD.

A very good answer, AND explanation!

I got the disk re-formatted in ext3 format. One partition still will not delete (in use)(I deleted one partition and re-formatted from terminal).

The disk WILL now unmount and mount. It is now an ownership issue, to gain write access, I believe...

---

### Post by jw5801 on 2007-11-16
Ok, so is the disk mounting automatically? If it is then you should be able to right click on it and go to properties, then look at the permissions tab to alter this.

If you've used the command line to mount it, then you'll have to edit /etc/fstab in order to tell the system that you are allowed to own the device. Open the file with:```
gksu gedit /etc/fstab
```and you'll need to add a line at the end that looks like the following:```

/dev/sdb1 */wherever/you/want/your/mountpoint/to/be* ext3 user,auto,exec 0 0
```Note that you'll want to replace the italics with the directory of your choice and that this directory must exist and be empty, something like ~/Desktop/storage would probably work nicely. After this is set up, you can mount the device with a simple:```
sudo mount /dev/sdb1
```

*NOTE: I am assuming the device is still reporting itself as /deb/sdb as it was earlier in this thread, and that the partition you want is labelled /dev/sdb1. If this isn't the case then you'll need to edit what I've written above for your own purposes. You can check what it is labelled as with a simple* ```
sudo fdisk -l
```

---

### Post by buccaneere on 2007-11-16
> **jw5801 said:**
> Ok, so is the disk mounting automatically? If it is then you should be able to right click on it and go to properties, then look at the permissions tab to alter this.

If you've used the command line to mount it, then you'll have to edit /etc/fstab in order to tell the system that you are allowed to own the device. Open the file with:```
gksu gedit /etc/fstab
```and you'll need to add a line at the end that looks like the following:```

/dev/sdb1 */wherever/you/want/your/mountpoint/to/be* ext3 user,auto,exec 0 0
```Note that you'll want to replace the italics with the directory of your choice and that this directory must exist and be empty, something like ~/Desktop/storage would probably work nicely. After this is set up, you can mount the device with a simple:```
sudo mount /dev/sdb1
```

*NOTE: I am assuming the device is still reporting itself as /deb/sdb as it was earlier in this thread, and that the partition you want is labelled /dev/sdb1. If this isn't the case then you'll need to edit what I've written above for your own purposes. You can check what it is labelled as with a simple* ```
sudo fdisk -l
```

It was, then I did something to stop auto-mount.:confused:

The problem is solved by workaround=D>. I still would like to know what wasn't done right.

One day, I will. 

In the meantime, I fed the Live CD into a fourth laptop, and attempted to install to the same external disk. A file system insufficiency prevented this, and had to be fixed with gpart. I rolled a few dice, picked some #'s, and proceeded with the install, not knowing what partitions I've created. I wasn't sure even that I was installing on the external drive, till afterward...

The install was successful. I created a directory I think), unplugged the USB drive, booted the third laptop back up, plugged in the USB drive (at the same time), and created a folder into which to unload the files from the third laptop, onto the external drive.

I don't even know if I booted from the external drive, or the local drive. Both have the same user name, and password. (What problems will that cause???:confused:)

Now let's get one of the linux boxes online...:roll:

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-23
haha

you wanted to install linux on your external drive ?

oh never mind i got it you just found a work around

---

### Post by buccaneere on 2007-11-24
> **jw5801 said:**
> Ok, so is the disk mounting automatically? If it is then you should be able to right click on it and go to properties, then look at the permissions tab to alter this.

If you've used the command line to mount it, then you'll have to edit /etc/fstab in order to tell the system that you are allowed to own the device. Open the file with:```
gksu gedit /etc/fstab
```and you'll need to add a line at the end that looks like the following:```

**[COLOR="Red"]/dev/sdb1 */wherever/you/want/your/mountpoint/to/be* ext3 user,auto,exec 0 0[/COLOR]**
```Note that you'll want to replace the italics with the directory of your choice and that this directory must exist and be empty, something like ~/Desktop/storage would probably work nicely. After this is set up, you can mount the device with a simple:```
sudo mount /dev/sdb1
```

*NOTE: I am assuming the device is still reporting itself as /deb/sdb as it was earlier in this thread, and that the partition you want is labelled /dev/sdb1. If this isn't the case then you'll need to edit what I've written above for your own purposes. You can check what it is labelled as with a simple* ```
sudo fdisk -l
```

What exactly will this code be?

Is there a '#' in front of the text line? As in '#  /dev/sdb1'    xxx    xxx    x x?

If I enter 'sdb1', will that give me ownership of the entire device (HDD)?

To gain ownership of the entire drive, would I enter '/dev/usb' ?  Or /dev/usbdisk?

---

### Post by KIAaze on 2007-11-24
This might help you: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

> **buccaneere said:**
> What exactly will this code be?
analyzing "/dev/sdb1 /wherever/you/want/your/mountpoint/to/be ext3 user,auto,exec 0 0"

device: /dev/sdb1
mount point: /wherever/you/want/your/mountpoint/to/be ext3
filesystem: ext3
-user: allows normal users to mount it
-auto: will be mounted automatically at boot or when "mount -a" is issued
-exec: you can run binaries from this disk
first zero: don't back it up
second zero: don't check it with fsck

> **buccaneere said:**
> Is there a '#' in front of the text line? As in '#  /dev/sdb1'    xxx    xxx    x x?
No. The "#" in front of lines means those lines are commented, i.e. not active.

> **buccaneere said:**
> If I enter 'sdb1', will that give me ownership of the entire device (HDD)?
default option is rw=read/write and the fstab line given contains "user", so as far as I know, yes, it should allow you to mount and use it normally as a user.

> **buccaneere said:**
> To gain ownership of the entire drive, would I enter '/dev/usb' ?  Or /dev/usbdisk?
You just have to enter the correct name of the device which you can see if you run "sudo fdisk -l".
For usb, it will probably be something like /dev/sdaX, not /dev/usb or /dev/usbdisk.

---

### Post by buccaneere on 2007-11-24
> **KIAaze said:**
> This might help you: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)


analyzing "/dev/sdb1 /wherever/you/want/your/mountpoint/to/be ext3 user,auto,exec 0 0"

device: /dev/sdb1
mount point: /wherever/you/want/your/mountpoint/to/be ext3
filesystem: ext3
-user: allows normal users to mount it
-auto: will be mounted automatically at boot or when "mount -a" is issued
-exec: you can run binaries from this disk
first zero: don't back it up
second zero: don't check it with fsck


No. The "#" in front of lines means those lines are commented, i.e. not active.


default option is rw=read/write and the fstab line given contains "user", so as far as I know, yes, it should allow you to mount and use it normally as a user.


You just have to enter the correct name of the device which you can see if you run "sudo fdisk -l".
For usb, it will probably be something like /dev/sdaX, not /dev/usb or /dev/usbdisk.

THANKS KIA!

I got the tuxfile link in favorites, while waiting for some more input here. I tried a couple of fstab entries similar to the formatting in that link, with interesting results mind you, but none that changed what I've got.

And what I've got might be a clue also... I **can **write to the disk, even tho' permissions for any file says I can't change them, **BUT**, the available space to which to write in any file, is not equivalent to the unused space on the disk.

What does that tell me???

EDIT: It tells me to check to see if the disk really does have only 1.3G left on the drive for writing!!! Which there was. Recycled had 30G of stuff.

Really solved this time!!!!!!!!!!!!

---

### Post by buccaneere on 2007-11-25
> **jw5801 said:**
> Ok, so is the disk mounting automatically? If it is then you should be able to right click on it and go to properties, then look at the permissions tab to alter this.

**[COLOR="Red"]If you've used the command line to mount it, then you'll have to edit /etc/fstab in order to tell the system that you are allowed to own the device.[/COLOR]** Open the file with:```
gksu gedit /etc/fstab
```and you'll need to add a line at the end that looks like the following:```

/dev/sdb1 */wherever/you/want/your/mountpoint/to/be* ext3 user,auto,exec 0 0
```Note that you'll want to replace the italics with the directory of your choice and that this directory must exist and be empty, something like ~/Desktop/storage would probably work nicely. After this is set up, you can mount the device with a simple:```
sudo mount /dev/sdb1
```

*NOTE: I am assuming the device is still reporting itself as /deb/sdb as it was earlier in this thread, and that the partition you want is labelled /dev/sdb1. If this isn't the case then you'll need to edit what I've written above for your own purposes. You can check what it is labelled as with a simple* ```
sudo fdisk -l
```

Another good answer!

A good teacher indeed!

Executing a command from the command line does NOT necessarily mean the GUI will respond in kind...

---

