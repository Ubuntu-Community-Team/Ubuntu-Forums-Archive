---
title: "Swap file question"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-08-22
Hello, I find that when my SWAP file gets above 1% used, my computer gets really slow...and if I open way too many tabs on Swiftfox/Firefox/Swiftweasel or too large of a page (like all 49 pages of my Photobucket images)...the SWAP file will sometimes jump to 10% used or slightly more.


So...my question is this:

After closing all the tabs and applications/browsers, is there a way to clear the SWAP file so I don't have to restart my computer to work faster?


I would like to be able to clear the SWAP file back to 0%, just like it is when I start the computer.


I figure there is probably a simple command to do it, I just haven't found it yet.

---

### Post by lloyd_b on 2007-08-22
> **crimesaucer said:**
> Hello, I find that when my SWAP file gets above 1% used, my computer gets really slow...and if I open way too many tabs on Swiftfox/Firefox/Swiftweasel or too large of a page (like all 49 pages of my Photobucket images)...the SWAP file will sometimes jump to 10% used or slightly more.


So...my question is this:

After closing all the tabs and applications/browsers, is there a way to clear the SWAP file so I don't have to restart my computer to work faster?


I would like to be able to clear the SWAP file back to 0%, just like it is when I start the computer.


I figure there is probably a simple command to do it, I just haven't found it yet.

First off, there is something wrong if using swap makes your machine run slower.  Question: where is the swap partition located?  If it's on a slow device, then I could see it having that effect.  But if it's a regular partition on your hard drive, then something is wrong.


As to your actual question - in a terminal window:
```
sudo swapoff -a
sudo swapon -a
```
This will disable the swap space, and then re-enable it, and will have the effect of "clearing" your swap space back to 0 used.

Lloyd B.

---

### Post by crimesaucer on 2007-08-22
Thank you.

I was under the impression that a SWAP file is slower because it is on your hard disk, and accessing it is slower than my 512MB of RAM....

...so if Swiftfox moves over to my SWAP, there is a noticeable slowness to my browser which is usually very fast.

My SWAP is an extended logical SWAP area of 1GB of my Hard Disk.

---

### Post by Arthur Archnix on 2007-08-22
You know, I've been a bit displeased with my own swap performance and your post made me wonder if it's because the last time I partitioned, I moved my swap to an extended partition. Previously it was a primary partition at the start of the hard-drive. I'm sure it makes a bit of a difference, but I doubt that it would be noticeable and the difference is probably psychological, but still, you've got me wondering.

---

### Post by crimesaucer on 2007-08-22
Well, I thought SWAP was always slower than regular RAM, which is why people set there vm.swappiness to = 0 or 5....


I do notice a huge difference when it gets used.

Try this picture: [http://www.harlem-13-gigapixels.com/](http://www.harlem-13-gigapixels.com/)


Try that page above, open the page (which is a panoramic picture of Harlem)...let it stay on you Firefox for a while, click around on it to zoom in and out and side to side for different views of Harlem from the end of Central Park (it actually is a cool picture)...maybe open some other large pages along with it.


Then check out your SWAP file to see how much is being used now...hopefully at least 5% after playing with the picture a bit...see how slow everything gets?


Then close all of the tabs, and close Firefox completely. Then open it up and see how slow it is compared to a fresh start of Firefox with 0% or 1% SWAP being used.

---

### Post by lloyd_b on 2007-08-22
> **crimesaucer said:**
> Thank you.

I was under the impression that a SWAP file is slower because it is on your hard disk, and accessing it is slower than my 512MB of RAM....

...so if Swiftfox moves over to my SWAP, there is a noticeable slowness to my browser which is usually very fast.

My SWAP is an extended logical SWAP area of 1GB of my Hard Disk. 

The swap space shouldn't be holding anything that your web browser is actively using - the "pages" that are moved to swap are those that aren't actively required at the moment.

Where swapping will slow things down is when the swap space is "thrashing" - i.e. it's constantly trying to bring things back into RAM, with the consequence that it's constantly moving other things out to swap to make room, then has to bring those other things back in...

If swap space *is* thrashing, it will be very noticeable - there will be almost constant hard drive activity.

But in your example, you talk about 1%-10% of swap being used.  With 1GB of swap space, that's 10-100Mb.  For swapping out 10Mb, most likely Swiftfox is never swapped at all - generally, it'll swap out inactive daemons, inactive programs in other workspaces, etc, before it starts swapping out pieces of an active application.  When you get up to 100Mb, it might have to swap out parts of an active application, but even then it shouldn't be any "in-use" parts.

A question: what kind of video card do you have?  If it's an Intel 9xx device (or any other device that uses system RAM for video memory) then it may be you have much less than 512Mb actually available to begin with, which can cause problems when running memory intensive programs (and a web browser with lots of images qualifies as memory intensive).

A test: After booting up, open up a terminal window, and type "free" - this will give you a good breakdown of your "base" memory usage.  If this is a large percentage of total RAM, then the "swap slowdown" you're seeing may just be a reflection of insufficient RAM.

Lloyd B.

---

### Post by Tyke91 on 2007-08-22
i dunno... i never have this problem because i have a beastly amount of ram (and accidentally, swap too)

even when im opening tons of files and such, my swap doesnt move at all and my ram only goes to maybe 40% ...everything is still fast if i open gimp/amarok/harlempicture/googleearth/and neverwinter nights... 

although i could never do that on windows... so... YAY LINUX :D

---

### Post by crimesaucer on 2007-08-22
For Example:

I have 4 tabs open in my Swiftfox, 1.) with that panoramic photo , 2.) Ubuntu Forum's Community Screenshots, 3.) this post, and 4.) my xhtml/css Chef's resume (which is a resume small page)...., and my SWAP is all the way up to 7% used now, and my whole Swiftfox browser is very slow.

Ubuntu Forums "Absolute Beginner Talk" usually takes 5.5 seconds to fully load on my Fasterfox timer...but now it takes 15.5 seconds....and this post took 11.538s to fully load. 

I just opened my 5th tab with Surfline.com which usually takes 9 seconds to fully load and it took 12.444s...

and then playing with the panoramic photo, I'm now up to 9% SWAP after about 15 minutes.

---

### Post by crimesaucer on 2007-08-22
> **lloyd_b said:**
> The swap space shouldn't be holding anything that your web browser is actively using - the "pages" that are moved to swap are those that aren't actively required at the moment.

Where swapping will slow things down is when the swap space is "thrashing" - i.e. it's constantly trying to bring things back into RAM, with the consequence that it's constantly moving other things out to swap to make room, then has to bring those other things back in...

If swap space *is* thrashing, it will be very noticeable - there will be almost constant hard drive activity.

But in your example, you talk about 1%-10% of swap being used.  With 1GB of swap space, that's 10-100Mb.  For swapping out 10Mb, most likely Swiftfox is never swapped at all - generally, it'll swap out inactive daemons, inactive programs in other workspaces, etc, before it starts swapping out pieces of an active application.  When you get up to 100Mb, it might have to swap out parts of an active application, but even then it shouldn't be any "in-use" parts.

A question: what kind of video card do you have?  If it's an Intel 9xx device (or any other device that uses system RAM for video memory) then it may be you have much less than 512Mb actually available to begin with, which can cause problems when running memory intensive programs (and a web browser with lots of images qualifies as memory intensive).

A test: After booting up, open up a terminal window, and type "free" - this will give you a good breakdown of your "base" memory usage.  If this is a large percentage of total RAM, then the "swap slowdown" you're seeing may just be a reflection of insufficient RAM.

Lloyd B.

at the current moment of 25 minutes with those 5 pages open and nothing else:

```

blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        486          8          0          2         57
-/+ buffers/cache:        426         68
Swap:         1898        204       1693


```

I think you have a point about the "Thrashing" because it seemed that the tabs were very sticky and slow when changing them at first with in the first 10 minutes, but now after 30 minutes, the tabs are very easy to change back and forth to.

And I do have an Intel embedded video card.

---

### Post by crimesaucer on 2007-08-22
Ok, I definitely think it was the "Thrashing", because I started to open as many apps and more pages on Swiftfox and performance was only a slight bit slower (1 more second per page)...

...and these were the results from free -m:

```

blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        486          8          0          2         57
-/+ buffers/cache:        426         68
Swap:         1898        204       1693
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        448         46          0          4         79
-/+ buffers/cache:        364        130
Swap:         1898        303       1594
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        484         11          0          3         80
-/+ buffers/cache:        400         94
Swap:         1898        306       1591
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        357        137          0          5        103
-/+ buffers/cache:        248        246
Swap:         1898        127       1770
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        420         74          0          9        147
-/+ buffers/cache:        263        231
Swap:         1898        127       1770
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        387        107          0          9        146
-/+ buffers/cache:        231        263
Swap:         1898        127       1770
blah@blah-blah:~$ sudo swapoff -a
Password:
blah@blah-blah:~$ sudo swapon -a
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        467         27          0          9        182
-/+ buffers/cache:        275        219
Swap:          949          0        949
blah@blah-blah:~$ 




```



Thanks for the help, and I guess there isn't really a problem, it's just the "Thrashing" with my Intel embedded card and less than 512MB RAM.


Thanks for the commands lloyd_b,
-c.

---

### Post by crimesaucer on 2007-08-22
After taking a second look at my original SWAP file, it seems that I hadn't noticed that my 1GB SWAP was registering as 1898MB of SWAP...when it should of been 949MB of SWAP...


...so maybe that was a bit of the problem?

---

### Post by lloyd_b on 2007-08-22
> **crimesaucer said:**
> at the current moment of 25 minutes with those 5 pages open and nothing else:

```

blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        486          8          0          2         57
-/+ buffers/cache:        426         68
Swap:         1898        204       1693


```

I think you have a point about the "Thrashing" because it seemed that the tabs were very sticky and slow when changing them at first with in the first 10 minutes, but now after 30 minutes, the tabs are very easy to change back and forth to.

And I do have an Intel embedded video card.

I have one machine with a similar configuration (512Mb RAM, Intel video) - immediately after booting up, it had 385Mb of memory used, which only left 127Mb for my applications.  When I started digging, it turned out that almost all of that memory was being used by "Xorg", which represents the base window system (including the memory used by the video driver)..

I dropped the video resolution down a notch, and switched to a simple background (rather than the nice high-res jpep I originally had) - the "base" memory usage dropped from 385Mb down to 210Mb, and the overall responsiveness of the system went way up.

512Mb is more than enough for an Ubuntu system, provided that all of it is actually available.  With those Intel video chips, the amount of memory available can very easily be reduced to below the level needed for decent performance.

Please remember one thing - programs do *not* run from swap.  In order to run, they have to be moved into RAM.  So if your RAM is limited, system performance will suffer considerably, regardless of how much swap space you have.  

In addition, having limited RAM restricts the system's ability to buffer/cache files, which further reduces the performance of the system.  

Lloyd B.

---

### Post by crimesaucer on 2007-08-22
> **lloyd_b said:**
> I have one machine with a similar configuration (512Mb RAM, Intel video) - immediately after booting up, it had 385Mb of memory used, which only left 127Mb for my applications.  When I started digging, it turned out that almost all of that memory was being used by "Xorg", which represents the base window system (including the memory used by the video driver)..

I dropped the video resolution down a notch, and switched to a simple background (rather than the nice high-res jpep I originally had) - the "base" memory usage dropped from 385Mb down to 210Mb, and the overall responsiveness of the system went way up.

512Mb is more than enough for an Ubuntu system, provided that all of it is actually available.  With those Intel video chips, the amount of memory available can very easily be reduced to below the level needed for decent performance.

Please remember one thing - programs do *not* run from swap.  In order to run, they have to be moved into RAM.  So if your RAM is limited, system performance will suffer considerably, regardless of how much swap space you have.  

In addition, having limited RAM restricts the system's ability to buffer/cache files, which further reduces the performance of the system.  MB

Lloyd B.

Very good points, I'll do some research on my system and see what I can do...and right now I am using a very weighty .png desktop wallpaper and .png skydome...so I'll check out the difference when I try a new wallpaper (right now I'm in love with my eye candy so I'll look into the video resolution first...but I love my wallpapers and Compiz Fusion so much, I most likely won't change a thing...) 

Anyway, thanks for those 2 commands because I think it corrected a problem I hadn't noticed before (having only 1GB of SWAP registering as 1898MB...)

Thanks again,
-c.

---

### Post by crimesaucer on 2007-08-22
So that strange problem seems to happen again after a restart:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-32.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-33.png[/IMG]

---

### Post by lloyd_b on 2007-08-22
I did a search through the forums (I *thought* I remembered seeing this issue before).  Read through this thread and see if the info in it applies to you:
[Is my swap mounted twice]("http://ubuntuforums.org/showthread.php?t=444288")

Lloyd B.

---

### Post by crimesaucer on 2007-08-22
After reading through a few of those threads, I see that many people had a similar problem...

this is cat /proc/swaps:

Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-34.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-34.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-34-14.png[/IMG]


I'm going to read up on it some more, but if anybody knows the simple answers, then please let me know, thanks for the links,
-c.

---

### Post by crimesaucer on 2007-08-22
These are my results if there are any experts out there:

```

blah@blah-blah:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       971860  0       -1
/dev/mapper/sda5                        partition       971860  0       -2
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        487          7          0         12        197
-/+ buffers/cache:        277        217
Swap:         1898          0       1898
blah@blah-blah:~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229        7052    14651280   83  Linux
/dev/sda3            7053        7296     1959930    5  Extended
/dev/sda5            7053        7173      971869+  82  Linux swap / Solaris
/dev/sda6            7175        7296      979965    b  W95 FAT32
blah@blah-blah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/sda2 :
UUID=c0350aef-c485-4cf5-9571-33f17d4558c8 / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
# Entry for /dev/mapper/sda1 :
UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=222,utf8 0 0
UUID=A24D-C169 /windows vfat defaults 0 0
# Entry for /dev/mapper/sda6 :
UUID=d2f30561-9793-4485-9fd7-9dccfae2af4f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
blah@blah-blah:~$ free
             total       used       free     shared    buffers     cached
Mem:        506932     492908      14024          0      13844     180340
-/+ buffers/cache:     298724     208208
Swap:      1943720          0    1943720
blah@blah-blah:~$ 


```

---

### Post by crimesaucer on 2007-08-22
Ok, I think this is my problem:

```

blah@blah-blah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/sda2 :
UUID=c0350aef-c485-4cf5-9571-33f17d4558c8 / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
# Entry for /dev/mapper/sda1 :
UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=222,utf8 0 0
UUID=A24D-C169 /windows vfat defaults 0 0
# Entry for /dev/mapper/sda6 :
UUID=d2f30561-9793-4485-9fd7-9dccfae2af4f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

```


right here:

```

# Entry for /dev/mapper/sda6 :
UUID=d2f30561-9793-4485-9fd7-9dccfae2af4f none swap sw 0 0

```

where as it states that sda6 is for FAT32 here:

```

blah@blah-blah:~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229        7052    14651280   83  Linux
/dev/sda3            7053        7296     1959930    5  Extended
/dev/sda5            7053        7173      971869+  82  Linux swap / Solaris
/dev/sda6            7175        7296      979965    b  W95 FAT32


```


...I think when I asked for help right after upgrading from edgy to feisty (right when it went stable), I think I might have been given the wrong directions in a thread and I didn't notice it because everything seemed to work normally.


Any ideas on how to fix this?

---

### Post by crimesaucer on 2007-08-23
Ok...I'm going to start a new thread because I think no one is paying attention to this one anymore...but I think I found the problem...but I'm not sure about the proper way to fix this...

All righty....here it goes...the long version:

```

blah@blah-blah:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       971860  0       -1
/dev/mapper/sda5                        partition       971860  0       -2
blah@blah-blah:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        487          7          0         12        197
-/+ buffers/cache:        277        217
Swap:         1898          0       1898
blah@blah-blah:~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229        7052    14651280   83  Linux
/dev/sda3            7053        7296     1959930    5  Extended
/dev/sda5            7053        7173      971869+  82  Linux swap / Solaris
/dev/sda6            7175        7296      979965    b  W95 FAT32
blah@blah-blah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/sda2 :
UUID=c0350aef-c485-4cf5-9571-33f17d4558c8 / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
# Entry for /dev/mapper/sda1 :
UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=222,utf8 0 0
UUID=A24D-C169 /windows vfat defaults 0 0
# Entry for /dev/mapper/sda6 :
UUID=d2f30561-9793-4485-9fd7-9dccfae2af4f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
blah@blah-blah:~$ free
             total       used       free     shared    buffers     cached
Mem:        506932     492908      14024          0      13844     180340
-/+ buffers/cache:     298724     208208
Swap:      1943720          0    1943720
blah@blah-blah:~$ sudo fdisk -l /dev/hda
Password:
blah@blah-blah:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229        7052    14651280   83  Linux
/dev/sda3            7053        7296     1959930    5  Extended
/dev/sda5            7053        7173      971869+  82  Linux swap / Solaris
/dev/sda6            7175        7296      979965    b  W95 FAT32
blah@blah-blah:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G   11G  2.5G  82% /
varrun                248M  104K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
procbususb            248M  128K  248M   1% /proc/bus/usb
udev                  248M  128K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.20-16-386/volatile
/dev/mapper/sda1       41G   39G  1.4G  97% /media/hda1
/dev/mapper/sda6      956M  204K  955M   1% /windows
blah@blah-blah:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-08-22 23:15 A24D-C169 -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-08-22 23:15 B444EE8344EE47A6 -> ../../sda1
lrwxrwxrwx 1 root root 17 2007-08-22 23:00 c0350aef-c485-4cf5-9571-33f17d4558c8 -> ../../mapper/sda2
lrwxrwxrwx 1 root root 17 2007-08-22 23:00 d2f30561-9793-4485-9fd7-9dccfae2af4f -> ../../mapper/sda5
blah@blah-blah:~$ 


```


.....Now, I'm wondering if I messed something up (back in April), and things got symbolically linked and mixed up? Like this part:

```

blah@blah-blah:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-08-22 23:15 A24D-C169 -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-08-22 23:15 B444EE8344EE47A6 -> ../../sda1
lrwxrwxrwx 1 root root 17 2007-08-22 23:00 c0350aef-c485-4cf5-9571-33f17d4558c8 -> ../../mapper/sda2
lrwxrwxrwx 1 root root 17 2007-08-22 23:00 d2f30561-9793-4485-9fd7-9dccfae2af4f -> ../../mapper/sda5

```

I had been instructed to order 2 of my partitions with this code April 22, 2007:

```
sudo fdisk /dev/sda
```

...and afterwards sda5 and sda6 switched places...


My short summary is that I have sda5 and sda6 crossed up somehow (and I don't know if that is what it is, but it seems that way to a beginner like me)...

...and that might not even be why I am showing this as 2 SWAP files for only 1GB of SWAP:

```

blah@blah-blah:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       971860  0       -1
/dev/mapper/sda5                        partition       971860  0       -2

```

Sorry for yet another confusing post from me...any help?

---

### Post by anewguy on 2007-08-23
Okay, I'm going to ask a dumb question - are you running 32 bit or 64 bit Ubuntu?

Thanks:)

---

### Post by crimesaucer on 2007-08-23
regular xubuntu 2.6.20-16-386 oni686

dual boot with Windows Xp

1GB FAT32

1GB SWAP

---

