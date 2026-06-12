---
title: "Ubuntu 14.04 does not boot on Mac Mini when usb drive is plugged in"
date: 2015-06-01
forum: Apple Hardware Users
---

### Post by Tim_Johnson on 2015-06-01
OS X 10.7.5 on 2011 Mac Mini.
Ubuntu 14.04 installed on partition of hard drive.
rEFInd installed.
External USB backup drive.

I can not boot ubuntu when the USB drive is attached.

If I disconnect the USB drive the ubuntu partition and bootable thumb drive (if attached) will be recognized by both Boot Manager and rEFInd.

If the USB drive *is* connected the ubuntu partition and bootable thumb drive (if attached) will *not* be recognized by Boot Manager and rEFInd.

It _seems_ as if when the USB drive is attached, that the machine recognizes only that drive, thinks it bootable and attempts to boot it, not seeing the real bootable devices at all.

This problem has seemed to "come and go" in the past. Any and all advice is welcomed.

---

### Post by este.el.paz on 2015-06-02
> **Tim_Johnson said:**
> OS X 10.7.5 on 2011 Mac Mini.
Ubuntu 14.04 installed on partition of hard drive.
rEFInd installed.
External USB backup drive.

I can not boot ubuntu when the USB drive is attached.

If I disconnect the USB drive the ubuntu partition and bootable thumb drive (if attached) will be recognized by both Boot Manager and rEFInd.

If the USB drive *is* connected the ubuntu partition and bootable thumb drive (if attached) will *not* be recognized by Boot Manager and rEFInd.

It _seems_ as if when the USB drive is attached, that the machine recognizes only that drive, thinks it bootable and attempts to boot it, not seeing the real bootable devices at all.

This problem has seemed to "come and go" in the past. Any and all advice is welcomed.


Is GRUB installed?  Do you see the GRUB window when the system is trying to boot?

e..

---

### Post by Tim_Johnson on 2015-06-02
> **este.el.paz said:**
> Is GRUB installed?  Do you see the GRUB window when the system is trying to boot?

e..
[COLOR=#000080]No. [/COLOR]The GRUB window is **not **active. Also, keyboard input is not accepted.

Thanks for the reply. 
- tj -

---

### Post by este.el.paz on 2015-06-02
> **Tim_Johnson said:**
> [COLOR=#000080]No. [/COLOR]The GRUB window is **not **active. Also, keyboard input is not accepted.

Thanks for the reply. 
- tj -

@tj:

OK.  It is a little hard to know entirely what is going on, are you saying that Ubuntu 14 will boot if no usb devices are plugged in?  If so, what happens if you plug these devices in **after** you boot Ubuntu?  Seems like a **simple** fix . . . there are some "difficulties" in terms of getting linux to run on apple hardware, like potentially needing rEFInd to help kick start linux . . . and so forth.  On my MBPro '09 model, I need rEFInd && GRUB installed to be able to get linux to boot up . . . and the automatic installer would say "install successful" . . . but when I went to boot it, did not work . . . .  I have to use "manual" and set up a 10MB partition labeled as "bios_grub" . . . and then the "/" partition and swap.  Also, couldn't "add" that partition or install GRUB after the install . . . had to wipe several installs and start fresh to get the GRUB items that would then boot linux . . . . 

So, either you need to plug in your usb devices after you boot ubuntu, minor issue; or, if ubuntu isn't booting at all, install GRUB . . . and then try again.

e..

---

### Post by Tim_Johnson on 2015-06-03
Ubuntu 14 will NOT boot when a usb drive is plugged in. There are numerous other USB drives plugged in, such as keyboard, keypad, pointing device and camera. 
Those non-storage devices do not seem to interfere. Plugging in the USB drive after Ubuntu boots has been successful.
But it has gotten worse. Now, when I unplug the USB drive, I get the GRUB window, but now it is unresponsive.
Furthermore, the install thumbdrive won't boot either.
As I said before, these events "come and go"....
So I'm going to quote your synopsis from your latest post:
> So, either you need to plug in your usb devices after you boot ubuntu,  minor issue; or, if ubuntu isn't booting at all, install GRUB . . . and  then try again.
This raises my question : How do I install GRUB (or repair it) if I can't boot ubuntu (either from the already installed partition or the original install flash drive)?

Frankly, I can do anything on OS X that I can on ubuntu, just less efficiently (in most cases). I'm inclined to just not buy another mac. Lot of minis on the market now since 2011 without (hopefully) all the proprietory BS.
Thanks for hanging in with my here. It is late where I am. And I will run the DiskUtil verify function against all partitions and try again tomorrow and report what I find.
cheers.
- tim -

---

### Post by este.el.paz on 2015-06-03
> **Tim_Johnson said:**
> Ubuntu 14 will NOT boot when a usb drive is plugged in. T
Those non-storage devices do not seem to interfere. Plugging in the USB drive after Ubuntu boots has been successful.
But it has gotten worse. Now, when I unplug the USB drive, I get the GRUB window, but now it is unresponsive.
As I said before, these events "come and go"....
So I'm going to quote your synopsis from your latest post:
This raises my question : How do I install GRUB (or repair it) if I can't boot ubuntu (either from the already installed partition or the original install flash drive)?
Frankly, I can do anything on OS X that I can on ubuntu, just less efficiently (in most cases). I'm inclined to just not buy another mac. Lot of minis on the market now since 2011 without (hopefully) all the proprietory BS.
- tim -

@tj:

On this "comes and goes" issue, I tend to post in waves and say the same thing each time, so I lose track of what I've said in a thread, but possibly this might be an "xorg.conf" issue??  Have you configured an xorg.conf file for your computer?  If not, find the instructions online or on the PowerPCFAQ to  "sudo Xorg -configure" . . . [not sure if that is accurate] and then "mv" the "xorg.conf.new"  to  /etc/X11/xorg.conf . . . you have to "stop lightdm" beforehand . . . there are xorg.conf files available online, but it is easy enough to do in a TTY . . . if you try it in the GUI when you "stop lightdm" the screen goes black and you have to type in the black . . . can and has been done.  TTY is easier.

Try doing that with your usb drive plugged in and you can "nano" the xorg.conf file and see if it shows anything . . . or, just "sudo reboot" and see if it boots Ubuntu.

Other option, try another flavor of Ubuntu or Linux for that matter . . . test the liveDVD and see which one works best for you.  If the GRUB window opens when you unplug the drive then GRUB is installed, but there is SuperGRUB2 which you can burn to a CD and can try to repair the boot items, for me it has worked to boot an installed system where GRUB failed to install . . . but, like I said the repairs didn't work.

Last thought, are you "unmounting" the drive **before** unplugging???  Linux does seem to be a little sensitive to drives being pulled w/o "ejecting" or "unmounting" and, if a drive was just unplugged before, then it might set up an "error" that would prevent the system from mounting.  I have had something like that happen with ext FW drives.  I had to boot OSX and use OSX to "eject" the drive, then back in linux it worked OK.

But, indeed, OSX is perfectly fine for running apple machines . . . .

e..

---

### Post by Tim_Johnson on 2015-06-03
@[**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965"):
I think your first paragraph refers to PowerPC machines. Mine is 2.3 GHz Intel Core i5. I don't see the same filesystem configuration that you refer to. No /etc/X11, but /usr/X11 and /usr/X11/lib/xorg. No Xorg command that I can locate. I have two "Live CDs" of Ubuntu 14.04 - the full version and the minimal version. Both created using DD. Earlier they could both be booted from. Now, neither even gets to GRUB.

I've been unplugging the USB drive when the machine turns off during reboot. I'm going to follow your suggestion about "unmounting" before reboot. I'll report back after I do that.

thanks & cheers
tim

---

### Post by este.el.paz on 2015-06-03
Sure, a Mac mini is not going to be PPC . . . it's just where I think there is data on how to set up the xorg.conf file is located.  And, it may or may not be necessary to do that . . . I don't have one on my MBPro LM 17.1 install . . . but, then I'm not plugging in a bunch of stuff either.

But, I have had issues with 15.04 installs and downloads that get corrupted . . . other question, did you check the "md5sum" number **before** burning or dd-ing your iso?  If the numbers do not match then the file is corrupted . . . begin again.

e..

---

### Post by Tim_Johnson on 2015-06-03
I did run md5sum to verify. All was good. As you recommended, I unmounted the USB drive before rebooting and trying to boot ubuntu. Same issue: GRUB screen, nonresponsive. 

The next thing I'll try is removing rEFInd. I'll get to that after researching whether there might be some "gotchas". Then I will post results.

I've been here before. Last year I installed 12.04 and ran that for about six months. Loved it! So much better performance and far less memory usage than OS X. But, at the end, had same problem as
I describe here with 14.04. I gave it up, went back to OS X and found that the problem went away a couple of months ago. And it has now resurfaced.

Gotta say : OS X is probably the best choice for this mac mini ...

---

### Post by este.el.paz on 2015-06-03
> **Tim_Johnson said:**
> I did run md5sum to verify. All was good. As you recommended, I unmounted the USB drive before rebooting and trying to boot ubuntu. Same issue: GRUB screen, nonresponsive. 

The next thing I'll try is removing rEFInd. I'll get to that after researching whether there might be some "gotchas". Then I will post results.

I've been here before. Last year I installed 12.04 and ran that for about six months. Loved it! So much better performance and far less memory usage than OS X. But, at the end, had same problem as
I describe here with 14.04. I gave it up, went back to OS X and found that the problem went away a couple of months ago. And it has now resurfaced.

Gotta say : OS X is probably the best choice for this mac mini ...

@tj:

I vaguely remember that I might have posted on yr thread, but, yeah, 12.04 has been the most friendly version to date . . . .  I don't think rEFInd would be the problem . . . if the rEFInd boot loader window shows up, that's all it does . . . .

Couple points, just "unmounting" on the linux side **might** not be enough to get it "re-set" . . . I had to use OSX to get it cycled back into proper order.  Also if "GRUB is 'unresponsive'"  possibly the SuperGRUB2 app might work as far as "repairing GRUB" goes . . . free utility . . . pretty handy to have around . . . main purpose is to boot available systems . . . so another way to check if it would boot linux . . . it has "recovery" which also GRUB offers . . . if you can run "recovery" mode . . . .

Also, did these problems begin after an update/upgrade?  New kernel?  You could try to boot the old kernel "Linux old" and see if that works . . . or, try to run another update/upgrade and see if the updated system will "fix" the problem . . . sometimes it does . . . a little patience can be a time saver.

e..

---

### Post by Tim_Johnson on 2015-06-03
I believe that it might have started after an upgrade, but I don't recall if there was a new kernel. Since GRUB is unresponsive, I can't access the previous kernel. However, I will try SuperGRUB2.

I've downloaded super_grub2_disk_2.02s3.zip and unzipped it. Which .iso should I use?

thanks
tj

---

### Post by este.el.paz on 2015-06-03
> **Tim_Johnson said:**
> I believe that it might have started after an upgrade, but I don't recall if there was a new kernel. Since GRUB is unresponsive, I can't access the previous kernel. However, I will try SuperGRUB2.

I've downloaded super_grub2_disk_2.02s3.zip and unzipped it. Which .iso should I use?

thanks
tj

Been awhile since I got it, so no answer . . . the ***right***one??  If it's unzipped what file format is the file?  I have found that intel Mac can burn .iso to CD/DVD . . . changing it to .dmg  then PPC Disk Utility can burn the file . . . .  I haven't messed around with USB drive options to make bootable drive enough to know how to do that . . . .

e..

---

### Post by Tim_Johnson on 2015-06-03
The following .iso files were unzipped:
super_grub2_disk_hybrid_2.02s3.iso    super_grub2_disk_i386_pc_2.02s3.iso    super_grub2_disk_x86_64_efi_2.02s3.iso

I presume it is the first, and I have used DD in the past (use with care!). I've tried the CD/DVD route with a standalone CD/DVD player (mini 2011 doesn't have one built-in).
This mini has never booted anything from a CD.

I will make a bootable stick using the instructions from here : [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
As soon as I have time and then will report back.
In the meantime - I beginning to suspect that this is a problem with OS X, not with the alternative bootable media. But I will give SuperGRUB2 a try. I'd love to be wrong. :)
tj

---

### Post by Tim_Johnson on 2015-06-03
Used super_grub2_disk_hybrid_2.02s3.iso to make bootable thumbdrive using **dd**
I was able to boot into SuperGRUB2, select the ubuntu 14.04 partition and boot it. Ubuntu 14.04 still won't boot on its own.
I'm going to do a little research and see what I need to do to repair.

Thanks for the help [**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965"), I'm going to play with SuperGrub2 tomorrow and will report what I find.
cheers

---

### Post by Tim_Johnson on 2015-06-06
I was able to boot SuperGRUB2 and from there. Boot into the Ubuntu 14.04 partition. From there I installed and ran boot-repair.
Now, I get the grub menu before rEFInd when I start/restart. The first item boots ubuntu successfully. Many menu items do not.
Now I have to get into Boot Manager to boot the Mac partition (press and hold Alt/Option key while starting).

Clearly there are other issues. But thanks to the help of [**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965") I have ubuntu back.
I'm going to mark this thread as solved and open another thread to analyze the pastebin data. 
Thanks very much for the help.

---

### Post by este.el.paz on 2015-06-06
> **Tim_Johnson said:**
> 
Now, I get the grub menu before rEFInd when I start/restart. The first item boots ubuntu successfully. Many menu items do not.
Now I have to get into Boot Manager to boot the Mac partition (press and hold Alt/Option key while starting).
Clearly there are other issues. But thanks to the help of [**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965") I have ubuntu back.
I'm going to mark this thread as solved and open another thread to analyze the pastebin data. 
Thanks very much for the help.

@Tim:

Thanks very kindly for the thumb's up and marking as solved, appreciate that . . . glad SG2 came in handy for you, it has for me.  I probably won't be able to help on the pastebin data, but, in terms of what you are saying about the order of what shows up, that **might** explain some possible issues, or not . . . usually OSX should be stacked first in the disk partitions, then the other systems added in subsequent partitions . . . .  

I have my MBPro set up for triple boot, two OSX disks, and the third for linux.  I have rEFInd installed in the second OSX partition, so if I reboot w/o holding option key it goes to the first OSX disk automatically; previously I had dual boot and if I rebooted it first loaded rEFInd, showed me the options, then if I picked linux, then the GRUB window would open, which would show the linux kernels up top and the OSX choices below.

Now, to get to linux I do have to reboot holding option key, which loads the apple boot manager, and then I select "windows" for linux and that ***should*** then load the rEFInd window, but because I added a security update to OSX that "broke" the blessing of rEFInd, so it just goes to GRUB, and then loads linux . . . .  In the past I found the rEFInd instructions on how to "re-bless" in the OSX Terminal, but I've done it a number of times and now the system still boots linux, so all I would need rEFInd for is if I needed to get to "single user" or something from the drop down menu ***in the second OSX disk*** . . . .

So, perhaps getting GRUB fixed has "un-blessed" rEFInd . . . as it should be loading first . . . but, my rule of thumb is, if it's working then let it alone.  But, if you have GParted or know how to check your partitions in the console, it should be the OSX items (it has its own boot partition very first), then the linux disks (grub/home/swap) with rEFInd loaded into the OSX "directory" . . . .  Zat what you did?

e..

---

### Post by Tim_Johnson on 2015-06-06
Here's diskutil dump : ```

linus:~ tim$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Linus                   359.2 GB   disk0s2
   3:       Microsoft Basic Data                         41.9 GB    disk0s3
   4:       Microsoft Basic Data                         68.9 GB    disk0s4
   5:       Microsoft Basic Data                         20.9 GB    disk0s5
   6:       Microsoft Basic Data                         8.4 GB     disk0s6
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *500.1 GB   disk1
   1:                      Linux UbuntuBackup            125.8 GB   disk1s1
   2:                 DOS_FAT_32 OsXchng                 62.9 GB    disk1s2
   3:                  Apple_HFS MacBackup               311.4 GB   disk1s3

```
It's not hard to boot Mac by invoking Boot Manager and picking the first icon,
which is labeled "EFI Boot". That brings up the rEFInd menu with the Mac OS X as an item.
Still, I intend to post the pastebin data in another thread for my own edification.
Cheers
tim

---

### Post by este.el.paz on 2015-06-06
Thanks, yeah, looks OK in disk 0 . . . with the EFI up front and Apple HFS next . . . but, don't see any "linux" partitions there??  Are these two internal drives?

Someone with more chops might be able to comment about disk1 and whether the order there should also be OSX up front, if that is where you are booting ubuntu from??

Anyway, be happy, any time you get linux running on apple you are doing something right . . . and there is always another install coming . . . .

c u on the forum . . . .
e..

---

### Post by Tim_Johnson on 2015-06-06
The Linux partitions are on the partitions list out as "Microsoft Basic Data"
they should be / (root), home, usr/local and swap.

---

### Post by este.el.paz on 2015-06-06
@tim-j:

Ah, OK, thanks for the answer to my idle question; I usually look at that stuff using GParted, where I believe it says "linux" or shows the labels of the partitions . . . I couldn't remember if the last time I used the terminal for diskutil it showed "microsoft" . . . .  

But, indeed in the OSX boot manager it shows linux as "windows" . . . .  Seems like you have enough space for "stuff" in linux, continuing on the idle comment front, I usually just do 3 partitions . . . from something dating back to when "primary" and "secondary"???? partition count seemed to be important--seemingly it isn't any more.

The four partition scheme, the separate "home" is better if you want to have several linux systems installed, you can share the home that way . . . haven't had the need for that . . . if I get bored then adding DEs gives me enough variety in linux.

e..

---

