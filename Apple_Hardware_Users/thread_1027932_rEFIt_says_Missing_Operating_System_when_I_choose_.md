---
title: "rEFIt says Missing Operating System when I choose Linux..."
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by Virtualboxbuntu on 2009-01-01
I installed Ubuntu Intrepid as a dualboot with OS X on my MacBook. I installed rEFIt and I have two options at boot: Macintosh and Legacy OS. Legacy OS is obviously Ubuntu, but it says "Missing Operating System" when I choose it.

When I installed Ubuntu, it said that GRUB had an error and couldn't install, so I reinstalled with GRUB unchecked. Could this have something to do with it?

---

### Post by Virtualboxbuntu on 2009-01-02
Hi, I got a brand-new MacBook and want to dual-boot Ubuntu. I've done everything up to the bootloader.

I have the rEFIt bootloader and it lets me choose Mac OS X normally, but the other option is Legacy OS and when I choose it, it says "Missing Operating System."

I'm experienced with using Linux on PCs but never on Macs. Any help is appreciated, thanks.

---

### Post by cyberdork33 on 2009-01-02
> **Virtualboxbuntu said:**
> I installed Ubuntu Intrepid as a dualboot with OS X on my MacBook. I installed rEFIt and I have two options at boot: Macintosh and Legacy OS. Legacy OS is obviously Ubuntu, but it says "Missing Operating System" when I choose it.

When I installed Ubuntu, it said that GRUB had an error and couldn't install, so I reinstalled with GRUB unchecked. Could this have something to do with it?

yep. See this post that was in the FAQ:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by cyberdork33 on 2009-01-02
Please do not double post, it makes helping you with your problem very difficult.
See reply here:
[http://ubuntuforums.org/showthread.php?t=1027932](http://ubuntuforums.org/showthread.php?t=1027932)

---

### Post by Virtualboxbuntu on 2009-01-02
> **cyberdork33 said:**
> Please do not double post, it makes helping you with your problem very difficult.
See reply here:
[http://ubuntuforums.org/showthread.php?t=1027932](http://ubuntuforums.org/showthread.php?t=1027932)

Sorry, I didn't mean to. I posted the first thread and then I couldn't find it after. I thought it was deleted or something, so I made another one. My apologies.

---

### Post by Virtualboxbuntu on 2009-01-02
I tried to reinstall again, with GRUB installing to /dev/sda3, my Ubuntu partition. When the installer reaches 94%, it says 

Executing 'grub-install /dev/sda3' failed.
This is a fatal error.

I tried running sudo grub-install /dev/sda3 manually in the terminal, and I got

Probing devices to get BIOS drivers. This may take a long time.
Could not find device for /boot. Not found or not a block device.

And trying to reinstall GRUB didn't work, because it wasn't installed in the first place.

---

### Post by pxwpxw on 2009-01-02
> **Virtualboxbuntu said:**
> I tried to reinstall again, with GRUB installing to /dev/sda3, my Ubuntu partition. When the installer reaches 94%, it says 

Executing 'grub-install /dev/sda3' failed.
This is a fatal error.

I tried running sudo grub-install /dev/sda3 manually in the terminal, and I got

Probing devices to get BIOS drivers. This may take a long time.
Could not find device for /boot. Not found or not a block device.

And trying to reinstall GRUB didn't work, because it wasn't installed in the first place.

1. Restart to refit and run the Partition Tool and sync the MBR.
2. Using the Desktop installer rescue option, just reinstall grub
3. Restart using the Option key and select refit then linux. If it doesn't work first time, try again, also without the Option key.
3. If you get stuck at a grub> commandline then check where your installed ubuntu root is according to grub.
Should be (hd0,2) if it is sda3
```

grub> find /vmlinuz

```
Come back here if you need to boot using grub>  commandline.

---

### Post by Virtualboxbuntu on 2009-01-05
> **pxwpxw said:**
> 1. Restart to refit and run the Partition Tool and sync the MBR.
2. Using the Desktop installer rescue option, just reinstall grub
3. Restart using the Option key and select refit then linux. If it doesn't work first time, try again, also without the Option key.
3. If you get stuck at a grub> commandline then check where your installed ubuntu root is according to grub.
Should be (hd0,2) if it is sda3
```

grub> find /vmlinuz

```
Come back here if you need to boot using grub>  commandline.

Sorry, but I'm not quite *that* experienced with Linux. What's the Desktop installer rescue option?

I've synced the MBR already.

---

### Post by pxwpxw on 2009-01-06
> **Virtualboxbuntu said:**
> Sorry, but I'm not quite *that* experienced with Linux. What's the Desktop installer rescue option?

I've synced the MBR already.

I was referring to the Alternate install CD, I see that there is no rescue option in the Desktop CD, you would have to mount the root partition and find out what is there and then re-install grub. It is not worth the trouble of getting the Alternate install CD, and may not fix it.

I assume you tried to restart ubuntu after MBR sync and it still failed.

So - after syncing the MBR,  do a full re-install.
 
But this time let it do the default grub installation to the MBR (hd0) = /dev/sda
and if it reports an error, just complete the installation - it will do that.

At the restart, use the refit partition tool once again to sync the MBR.

Restart using the Option key and select refit then linux. If it doesn't work first time, try again, also without the Option key, and with shutting down and restarting.

If it does not work by then call for more help, you will have to use the Desktop CD to locate the problem (with help).

---

### Post by Virtualboxbuntu on 2009-01-06
> **pxwpxw said:**
> I was referring to the Alternate install CD, I see that there is no rescue option in the Desktop CD, you would have to mount the root partition and find out what is there and then re-install grub. It is not worth the trouble of getting the Alternate install CD, and may not fix it.

I assume you tried to restart ubuntu after MBR sync and it still failed.

So - after syncing the MBR,  do a full re-install.
 
But this time let it do the default grub installation to the MBR (hd0) = /dev/sda
and if it reports an error, just complete the installation - it will do that.

At the restart, use the refit partition tool once again to sync the MBR.

Restart using the Option key and select refit then linux. If it doesn't work first time, try again, also without the Option key, and with shutting down and restarting.

If it does not work by then call for more help, you will have to use the Desktop CD to locate the problem (with help).

Hmm... The last time I let it do the default, it gave me the same error and didn't continue installing. But I'll give it a try anyway, and let you know what happens.

---

### Post by Virtualboxbuntu on 2009-01-06
pxwpxw, in your signature, there's something about a "grub2 efi bootloader." Do you think I should give that a try instead of rEFIt?

---

### Post by Virtualboxbuntu on 2009-01-06
Leaving GRUB as default doesn't work. It gets to 94% and says it has the fatal error, then the installer quits. When I sync the MBR and shutdown and all that stuff, then choose Legacy OS, it says 

Missing Operating System
_

---

### Post by TreeHugger52 on 2009-01-06
I recently had the same problem with rEFIt giving me options to boot into OSX or "legacy OS", which just lead to "Operating System Missing". A full re-install of ubuntu fixed it nicely for me.

---

### Post by pxwpxw on 2009-01-07
> **Virtualboxbuntu said:**
> pxwpxw, in your signature, there's something about a "grub2 efi bootloader." Do you think I should give that a try instead of rEFIt?

Could be useful if your MacBook is model 2,1 or earlier, but not now, there is something wrong with your install I don't understand, needs checking.

When the install fails on grub, you say it quits, you mean it quits before you can do anything?
It should just stop, and let you use a Back button to choose to continue without grub.

Was there any other problem you had with the install, particularly with partitioning, before it got to that stage?

Can you start up the Desktop CD, and mount your Ubuntu installed root partiton to see what you have there (I think it was sda3).

We are looking for the linux root files and the /boot/grub files, to see if you have a usable installed system.

Also, but from Macosx terminal, can you post the partition info from diskutil and the result from a hexdump of your MBR (512 bytes)
```

 diskutil list
 sudo hexdump -Cn512 /dev/disk0

```

Any of the above you can answer will help.

---

### Post by emmary on 2009-01-07
China GPS Navigation System Wholesale  
GPS is the acronym of Global Positioning System which uses a constellation of at least 24 satellites that transmit accurate microwave signals that tell GPS receivers their location, speed, direction, and time. The unit helps you keep on track during the travel. While the navigation capability is cool, it's also impressive that our products are all-in-one devices. You'll appreciate the appealing extras, including music player, video player, and e-book browser.

Related Categories:Digital Cameras Digital Camcorders Digital Photo Frames MP4 Player Bluetooth Adapters
 
 
 
 
Displaying 1 to 2 (of 2 products) Result Pages:  1  
 
    Product Name  
  


 4.3" TFT Touch Panel, MP3, Movie, Photo and E-Book, Voice Turn-by-Turn guidance [GNS-013-2BK]
M.O.Q.: None

Qty  Sample 1+ 3+ 7+ 15+ 
Price  US$123.18 US$113.20 Login Login 
 more... 
 
  


 4.3" TFT Touch Panel, MP3, Movie, Photo and E-Book, Voice Turn-by-Turn guidance [GNS-011-2SV]
M.O.Q.: None

Qty  Sample 1+ 3+ 7+ 15+ 
Price  US$123.18 US$113.20 Login Login 
 more...

---

### Post by Virtualboxbuntu on 2009-01-08
> **pxwpxw said:**
> Could be useful if your MacBook is model 2,1 or earlier, but not now, there is something wrong with your install I don't understand, needs checking.

When the install fails on grub, you say it quits, you mean it quits before you can do anything?
It should just stop, and let you use a Back button to choose to continue without grub.

Was there any other problem you had with the install, particularly with partitioning, before it got to that stage?

Can you start up the Desktop CD, and mount your Ubuntu installed root partiton to see what you have there (I think it was sda3).

We are looking for the linux root files and the /boot/grub files, to see if you have a usable installed system.

Also, but from Macosx terminal, can you post the partition info from diskutil and the result from a hexdump of your MBR (512 bytes)
```

 diskutil list
 sudo hexdump -Cn512 /dev/disk0

```

Any of the above you can answer will help.

My MacBook is model 4,1.

The install just quits before I can do anything. It says that grub-install failed and there's an only an OK button. I click it, and the install closes.

```

$ diskutil list
/dev/disk0
#:     TYPE NAME               SIZE       IDENTIFIER
0:     GUID_partition_scheme   *111.8 Gi  disk0
1:     EFI                     200.0 Mi   disk0s1
2:     Apple_HFS Macintosh HD  50.9 Gi    disk0s2
3:     Microsoft Basic Data    59.6 Gi    disk0s3
4:     Linux Swap              1024.8 Mi  disk0s4

```

3 is the Linux / partition.

I'm not on my MacBook right now, I'm on my desktop, but the MacBook is next to me. I'm going to copy and paste the other command's output (from my MacBook) because it gives me too much to type.

I'll also mount the partition from the LiveCD and see what's there.

---

### Post by Virtualboxbuntu on 2009-01-08
Here's the output of sudo hexdump -Cn512 /dev/disk0

```

$ sudo hexdump -Cn512 /dev/disk0
00000000  fa 31 c0 8e d8 8e c0 8e  d0 bc 00 7c fb fc 89 e6  |?1?.?.?.&#1084;.|??.?|
00000010  bf 00 06 b9 00 01 f3 a5  ea 1d 06 00 00 88 16 00  |?..?..??.......|
00000020  08 b4 08 cd 13 31 c0 88  f0 40 a3 f0 06 80 e1 3f  |.?.?.1?.?@??..??|
00000030  88 0e f2 06 be be 07 31  c0 b9 04 00 f6 04 80 74  |..?.??.1??..?..t|
00000040  03 40 89 f7 83 c6 10 e2  f3 83 f8 01 75 73 8a 16  |.@.?.?.??.?.us..|
00000050  00 08 b8 00 41 bb aa 55  31 c9 30 f6 f9 cd 13 72  |..?.A??U1?0???.r|
00000060  23 81 fb 55 aa 75 1d f6  c1 01 74 18 57 be e0 06  |#.?U?u.??.t.W??.|
00000070  8b 5d 08 89 5c 08 8b 5d  0a 89 5c 0a 8a 16 00 08  |.]..\..]..\.....|
00000080  b4 42 eb 2a 57 8b 45 08  8b 55 0a f7 36 f2 06 42  |?B?*W.E..U.?6?.B|
00000090  89 d1 31 d2 f7 36 f0 06  88 c5 d1 e8 d1 e8 24 c0  |.?1??6?..?????$?|
000000a0  08 c1 88 d6 8a 16 00 08  bb 00 7c b8 01 02 cd 13  |.?.?....?.|?..?.|
000000b0  72 16 5e 81 3e fe 7d 55  aa 75 08 fa ea 00 7c 00  |r.^.>?}U?u.??.|.|
000000c0  00 77 05 be f4 06 eb 03  be 0f 07 ac 20 c0 74 0c  |.w.??.?.?..? ?t.|
000000d0  b4 0e 8a 3e 62 04 b3 07  cd 10 eb ef eb fe 00 00  |?..>b.?.?.????..|
000000e0  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000000f0  00 00 00 00 4d 69 73 73  69 6e 67 20 6f 70 65 72  |....Missing oper|
00000100  61 74 69 6e 67 20 73 79  73 74 65 6d 0d 0a 00 4f  |ating system...O|
00000110  70 65 72 61 74 69 6e 67  20 73 79 73 74 65 6d 20  |perating system |
00000120  6c 6f 61 64 69 6e 67 20  65 72 72 6f 72 0d 0a 00  |loading error...|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |...............?|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |??????....'@...?|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 5c 06 80 fe  |??????(@....\..?|
000001e0  ff ff 83 fe ff ff 00 48  66 06 40 59 73 07 00 fe  |??.???.Hf.@Ys..?|
000001f0  ff ff 82 fe ff ff 40 a1  d9 0d 6b a6 1f 00 55 aa  |??.???@??.k?..U?|
00000200

```

---

### Post by Virtualboxbuntu on 2009-01-08
Here are some commands executed from the terminal in the LiveCD:

```


$ cd /media/disk #I've already mounted the disk

$ ls
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var

$ ls ./boot
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

$ ls ./boot/grub
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

```

If there's anything else you need to know, just say so.

---

### Post by cyberdork33 on 2009-01-08
> **Virtualboxbuntu said:**
> Here are some commands executed from the terminal in the LiveCD:

```


$ cd /media/disk #I've already mounted the disk

$ ls
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var

$ ls ./boot
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

$ ls ./boot/grub
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

```If there's anything else you need to know, just say so.
Those files are of the liveCD's filesystem though, not those on your mac.

If you have rEFIt on your Mac, you can use the partition Inspector Application in /Applications/Utilities to get a report about your disk, including any boot code installed on the various partitions.

---

### Post by Virtualboxbuntu on 2009-01-08
Sorry, I believe you misunderstood me. I mounted the Ubuntu partition on my Mac and that partition is what you see. If I were to execute

```

$ cd /media/disk
$ ls ./home

```

then I would see the home directory for the user I created during installation.

---

### Post by pxwpxw on 2009-01-09
> **Virtualboxbuntu said:**
> Here's the output of sudo hexdump -Cn512 /dev/disk0

```

$ sudo hexdump -Cn512 /dev/disk0
00000000  fa 31 c0 8e d8 8e c0 8e  d0 bc 00 7c fb fc 89 e6  |?1?.?.?.&#1084;.|??.?|
00000010  bf 00 06 b9 00 01 f3 a5  ea 1d 06 00 00 88 16 00  |?..?..??.......|
00000020  08 b4 08 cd 13 31 c0 88  f0 40 a3 f0 06 80 e1 3f  |.?.?.1?.?@??..??|
00000030  88 0e f2 06 be be 07 31  c0 b9 04 00 f6 04 80 74  |..?.??.1??..?..t|
00000040  03 40 89 f7 83 c6 10 e2  f3 83 f8 01 75 73 8a 16  |.@.?.?.??.?.us..|
00000050  00 08 b8 00 41 bb aa 55  31 c9 30 f6 f9 cd 13 72  |..?.A??U1?0???.r|
00000060  23 81 fb 55 aa 75 1d f6  c1 01 74 18 57 be e0 06  |#.?U?u.??.t.W??.|
00000070  8b 5d 08 89 5c 08 8b 5d  0a 89 5c 0a 8a 16 00 08  |.]..\..]..\.....|
00000080  b4 42 eb 2a 57 8b 45 08  8b 55 0a f7 36 f2 06 42  |?B?*W.E..U.?6?.B|
00000090  89 d1 31 d2 f7 36 f0 06  88 c5 d1 e8 d1 e8 24 c0  |.?1??6?..?????$?|
000000a0  08 c1 88 d6 8a 16 00 08  bb 00 7c b8 01 02 cd 13  |.?.?....?.|?..?.|
000000b0  72 16 5e 81 3e fe 7d 55  aa 75 08 fa ea 00 7c 00  |r.^.>?}U?u.??.|.|
000000c0  00 77 05 be f4 06 eb 03  be 0f 07 ac 20 c0 74 0c  |.w.??.?.?..? ?t.|
000000d0  b4 0e 8a 3e 62 04 b3 07  cd 10 eb ef eb fe 00 00  |?..>b.?.?.????..|
000000e0  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000000f0  00 00 00 00 4d 69 73 73  69 6e 67 20 6f 70 65 72  |....Missing oper|
00000100  61 74 69 6e 67 20 73 79  73 74 65 6d 0d 0a 00 4f  |ating system...O|
00000110  70 65 72 61 74 69 6e 67  20 73 79 73 74 65 6d 20  |perating system |
00000120  6c 6f 61 64 69 6e 67 20  65 72 72 6f 72 0d 0a 00  |loading error...|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |...............?|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |??????....'@...?|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 5c 06 80 fe  |??????(@....\..?|
000001e0  ff ff 83 fe ff ff 00 48  66 06 40 59 73 07 00 fe  |??.???.Hf.@Ys..?|
000001f0  ff ff 82 fe ff ff 40 a1  d9 0d 6b a6 1f 00 55 aa  |??.???@??.k?..U?|
00000200

```

Ok , no grub bootcode there, can you do same for your ubuntu root partition, I think its /dev/disk0s3, see whats there.

---

### Post by pxwpxw on 2009-01-09
> **Virtualboxbuntu said:**
> Here are some commands executed from the terminal in the LiveCD:

```


$ cd /media/disk #I've already mounted the disk

$ ls
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var

$ ls ./boot
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

$ ls ./boot/grub
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
etc                          vmcoreinfo-2.6.27-7-generic
grub                         vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic

```

If there's anything else you need to know, just say so.

Something strange there, about grub. Can you repeat, this time using
```

 ls -la ./boot
 ls -la ./boot/grub

```
Should show what's going on with the grub item. 

When you re-installed, did you delete/reformat the ubuntu partitions to get rid of any garbage?
Could be something left over causing trouble.

& see also my previous post

---

### Post by Virtualboxbuntu on 2009-01-10
```

$ sudo hexdump -Cn512 /dev/disk0s3
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
$

```
I left the LiveCD at my workplace by accident, I have to wait until tomorrow to go get it, so I can't tell you about anything on the Ubuntu partition. But I did reformat the partition before installing it again. And grub did NOT install properly, in case I was misunderstood.

---

### Post by Virtualboxbuntu on 2009-01-10
OK, I got the LiveCD back.
```

$ cd /media/disk #I've already mounted the disk

$ ls -la ./boot
total 12660
drwxr-xr-x  4 root root    4096 2009-01-07 02:05 .
drwxr-xr-x 20 root root    4096 2009-01-07 02:05 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  3 root root    4096 2008-11-08 15:19 etc
drwxr-xr-x  2 root root    4096 2009-01-07 02:05 grub
-rw-r--r--  1 root root 8900539 2009-01-07 02:05 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

$ ls -la ./boot/grub
total 224
drwxr-xr-x 2 root root   4096 2009-01-07 02:05 .
drwxr-xr-x 4 root root   4096 2009-01-07 02:05 ..
-rw-r--r-- 1 root root    197 2009-01-07 02:05 default
-rw-r--r-- 1 root root     15 2009-01-07 02:05 device.map
-rw-r--r-- 1 root root   8896 2009-01-07 02:05 e2fs_stage1_5
-rw-r--r-- 1 root root   8448 2009-01-07 02:05 fat_stage1_5
-rw-r--r-- 1 root root   7616 2009-01-07 02:05 iso9660_stage1_5
-rw-r--r-- 1 root root   9344 2009-01-07 02:05 jfs_stage1_5
-rw-r--r-- 1 root root   7776 2009-01-07 02:05 minix_stage1_5
-rw-r--r-- 1 root root  10496 2009-01-07 02:05 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 02:05 stage1
-rw-r--r-- 1 root root 123306 2009-01-07 02:05 stage2
-rw-r--r-- 1 root root  10216 2009-01-07 02:05 xfs_stage1_5

```

---

### Post by Virtualboxbuntu on 2009-01-10
Sorry, I double-posted by accident.

---

### Post by pxwpxw on 2009-01-11
> **Virtualboxbuntu said:**
> Sorry, I double-posted by accident.

The ./boot/etc/ directory should not be there, but anyway you might be able to get grub working -
as below -  

This next will show you what the installer did with grub, it seems to have got the job half done.
As before with the installed hd ubuntu mounted  -
```

$ cd /media/disk
$ sudo less ./var/log/installer/syslog | grep grub

```

Post for comment if you need to, else continue -

Before trying this grub setup, recheck MBR with rEFIt Partion Tool and Update MBR if needed.
 
Then restart to the  Desktop CD command line - (example includes grub messages)

```

$ sudo grub

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
### possibly (hd0,2), use your result in next line
grub> root (hd0,2)
root (hd0,2)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> 
grub> quit
quit
$ 

```

As there is no menu.lst yet, make a small one and put it in the HD ubuntu /media/disk/boot/grub/ directory.

Assuming sda3 is root.
```

## small menu.lst
timeout		13

color red/cyan white/blue

title	sda3 single,rw
root	(hd0,2)
kernel	/vmlinuz root=/dev/sda3 rw single
initrd	/initrd.img

title	sda3, GUI
root	(hd0,2)
kernel	/vmlinuz root=/dev/sda3 ro 
initrd	/initrd.img

title 	reboot
reboot

```

Retart..

Use the menu default single mode in case there are graphics issues.

For a big menu.lst (but you will have to edit it, comment out ##hiddenmenu).
Backup a copy of menu.lst.

From the console you can run as root
```

# update-grub

```
It writes a new menu.lst for the current system. Check it.

If all that fails, try a new start with another install cd, there is something strange going on.

---

### Post by Virtualboxbuntu on 2009-01-11
I used this CD on a PC only a few days ago, and GRUB works fine on it, so I don't think anything is wrong with the CD.

Anyway:
```

$ cd /media/disk
$ sudo less ./var/log/installer/syslog
No such file or folder

```
After examining a bit more closely, I discovered that there's no folder called installer in ./var/log. But there's a file called syslog in ./var/log so I used:
```

$ sudo less ./var/log/syslog

```
I restarted, rEFIt says the tables are synced. I then restarted once more into the LiveCD. I ran all the grub commands, the output was identical to what you wrote. I copied your small menu.lst and saved it as [ /media/disk/boot/grub/menu.lst ]. I restarted, and rEFIt said:

rEFIt

Boot Mac OS X from HD | Boot Linux from HD

"Linux" replaced "Windows," so something happened. I chose Linux and it hung on the Linux logo. I'll try changing the menu.lst a bit.

EDIT:
I changed the menu.lst entry for Ubuntu to match the one on my other computer (installed it with the same CD). It still freezes when I choose Linux.

---

### Post by pxwpxw on 2009-01-11
> **Virtualboxbuntu said:**
> I used this CD on a PC only a few days ago, and GRUB works fine on it, so I don't think anything is wrong with the CD.

rEFIt

Boot Mac OS X from HD | Boot Linux from HD

"Linux" replaced "Windows," so something happened. I chose Linux and it hung on the Linux logo. I'll try changing the menu.lst a bit.

EDIT:
I changed the menu.lst entry for Ubuntu to match the one on my other computer (installed it with the same CD). It still freezes when I choose Linux.

It does that to me sometimes after some change, and I restart or shutdown, try the Option key a few times and it goes. But I suppose you did that.

The missing /var/log/installer/syslog just confirms that the install did not finish - for some unknown reason.

I dont know what to suggest, you could do those hexdumps again to see if grub did get installed to the MBR.

Changing the grub menu.lst wont help, if grub is not getting started it cant get as far as the menu

Can't suggest anything much more - maybe an issue with your Mac model, see if anyone else has had a problem with that model, or if you have any non-standard configuration.

---

### Post by Virtualboxbuntu on 2009-01-11
> **pxwpxw said:**
> It does that to me sometimes after some change, and I restart or shutdown, try the Option key a few times and it goes. But I suppose you did that.

The missing /var/log/installer/syslog just confirms that the install did not finish - for some unknown reason.

I dont know what to suggest, you could do those hexdumps again to see if grub did get installed to the MBR.

Changing the grub menu.lst wont help, if grub is not getting started it cant get as far as the menu

Can't suggest anything much more - maybe an issue with your Mac model, see if anyone else has had a problem with that model, or if you have any non-standard configuration.

It's a near brand-new MacBook, the only things I've changed are making Firefox the default browser and installing Neverball. But you did suggest something that might help - the CD might be corrupted somehow. 

I tried a few tests on a PC with the same LiveCD, and there were a few things on the LiveCD that didn't work, yet on my desktop (installed from that CD) they do. So the CD must be scratched or something.

I'm going to try my Hardy CD and see what happens.

---

### Post by pxwpxw on 2009-01-11
Yes  try something different.
The odd thing is that it is possible to install and boot grub to its menu, using 
```

grub-install --root-directory xxx /dev/sda

```
xxx being where you mount the grub root partition. (check man grub-install, quoting from memory).
 - without any operating system - just an ext2 or ext3 partition for grub root , and grub stage1 on the mbr, so hard to see why you cant get grub to boot as far as the menu unless the grub files in your /dev/sda3/boot (i think thats it) e.g. stage1 is corrupted.

---

### Post by Virtualboxbuntu on 2009-01-12
> **pxwpxw said:**
> Yes  try something different.
The odd thing is that it is possible to install and boot grub to its menu, using 
```

grub-install --root-directory xxx /dev/sda

```
xxx being where you mount the grub root partition. (check man grub-install, quoting from memory).
 - without any operating system - just an ext2 or ext3 partition for grub root , and grub stage1 on the mbr, so hard to see why you cant get grub to boot as far as the menu unless the grub files in your /dev/sda3/boot (i think thats it) e.g. stage1 is corrupted.

I tried it and just like Intrepid, it insisted that grub install failed. I think I'll try the approach you mentioned, if you can clear up something: there are already four primary partitions on the disk. If I try to create a logical partition, it refuses and says it can't.

---

### Post by Virtualboxbuntu on 2009-01-12
Wait a minute - read this:

[http://www.linuxmint.com/forum/viewtopic.php?p=8954]("http://www.linuxmint.com/forum/viewtopic.php?p=8954")

On Step 9, it says that you have to enter a certain command in the terminal before the install reaches 94%, which is where mine gets messed up! What do you think?

---

### Post by cyberdork33 on 2009-01-12
> **Virtualboxbuntu said:**
> Wait a minute - read this:

[http://www.linuxmint.com/forum/viewtopic.php?p=8954](http://www.linuxmint.com/forum/viewtopic.php?p=8954)

On Step 9, it says that you have to enter a certain command in the terminal before the install reaches 94%, which is where mine gets messed up! What do you think?
possibly. good find on that anyway, as Mint users come in here every once in awhile asking about that.

---

### Post by pxwpxw on 2009-01-13
> **Virtualboxbuntu said:**
> I tried it and just like Intrepid, it insisted that grub install failed. I think I'll try the approach you mentioned, if you can clear up something: there are already four primary partitions on the disk. If I try to create a logical partition, it refuses and says it can't.

When using gparted, if you have a GUID/GPT partitioned disk (I assumed you did), you just leave it showing the 'primary' tag and create as many partitions as you want, there are no logical partitions.
On the other hand if you have an MSDOS partitioning system,  that requires a different approach entirely.
Might be a good idea to clarify the current situation.

---

### Post by pxwpxw on 2009-01-13
> **Virtualboxbuntu said:**
> Wait a minute - read this:

[http://www.linuxmint.com/forum/viewtopic.php?p=8954]("http://www.linuxmint.com/forum/viewtopic.php?p=8954")

On Step 9, it says that you have to enter a certain command in the terminal before the install reaches 94%, which is where mine gets messed up! What do you think?

Well, maybe, but a bit off the track I think, IDK.

However, installing ubuntu810 on imac8,1 I used the linux refit package to gptsync before restarting, and used the macosx refit gptsync (Partitoning tool) frequently before and after.

There were a lot of problems with an amd64 installation including grub, in fact in the end I had to pull the whole thing down, do an SMC reset, wipe the drive and partiton it manually with Leopard Disk Utility, then reinstall MacOSX10.5 and xubuntu 810 i386.

Are you using the amd64 install.

---

### Post by Virtualboxbuntu on 2009-01-14
> Are you using the amd64 install.
No, it's the x86 disc. I thought the MacBook processor was only x86...

I think I'll try the method from the link I posted, since it certainly can't cause any harm, right?

---

### Post by Virtualboxbuntu on 2009-01-17
That didn't work either.

When I first tried this, I tried to do it with Boot Camp. After I partitioned it, I inserted the Ubuntu CD and rebooted. I added a swap partition before completing the install, I later found out that the partitions have to remain the same for Boot Camp to continue.

I'm now going to try using a swap file instead of a swap partition with Boot Camp and see how that goes.

---

### Post by cyberdork33 on 2009-01-17
> **Virtualboxbuntu said:**
> That didn't work either.

When I first tried this, I tried to do it with Boot Camp. After I partitioned it, I inserted the Ubuntu CD and rebooted. I added a swap partition before completing the install, I later found out that the partitions have to remain the same for Boot Camp to continue.

I'm now going to try using a swap file instead of a swap partition with Boot Camp and see how that goes.
I don't think that Boot Camp cares actually. after you partition with boot camp, boot the Ubuntu LiveCD, start gparted and delete the new partition. Then start the installer, and tell it to install to the largest free space. that's it. It will create a swap partition itself.

---

### Post by Virtualboxbuntu on 2009-01-20
> **cyberdork33 said:**
> I don't think that Boot Camp cares actually. after you partition with boot camp, boot the Ubuntu LiveCD, start gparted and delete the new partition. Then start the installer, and tell it to install to the largest free space. that's it. It will create a swap partition itself.

That didn't seem to help, unfortunately. It still either gets an error when installing grub or says there's a missing operating system if I don't install grub.

I'm going to check out the links in your signature - Multi-boot Mactel and EFI-MBR madness and see if there's anything useful there.

From what I can tell on the first one, rEFIt actually just chain-loads a Linux bootloader such as GRUB. Am I wrong there?

---

### Post by cyberdork33 on 2009-01-20
> **Virtualboxbuntu said:**
> That didn't seem to help, unfortunately. It still either gets an error when installing grub or says there's a missing operating system if I don't install grub. Well I still think that is a different problem. "Missing Operating System" with no GRUB installed makes sense. rEFIt sees the partition and that it has an OS on it, but it cannot boot it because there is no bootcode.

> **Virtualboxbuntu said:**
> I'm going to check out the links in your signature - Multi-boot Mactel and EFI-MBR madness and see if there's anything useful there.
That will help you understand the difference between the EFI and BIOS side of things. It is good knowledge to have when working with these machines.

> **Virtualboxbuntu said:**
> From what I can tell on the first one, rEFIt actually just chain-loads a Linux bootloader such as GRUB. Am I wrong there?basically, yes. refit is just a gui to the Mac EFI that allows you to pick a bootable device. You can theoretically launch EFI executabled directly from EFI (like grub-efi), but that is a bit shaky. rEFIt is actually an EFI executable that the EFI firmware launches...

---

### Post by Virtualboxbuntu on 2009-01-20
> **cyberdork33 said:**
> Well I still think that is a different problem. "Missing Operating System" with no GRUB installed makes sense. rEFIt sees the partition and that it has an OS on it, but it cannot boot it because there is no bootcode.

So what do you think the problem is? Is GRUB not installing because Macs use EFI, or is it something else?

> **cyberdork33 said:**
> basically, yes. refit is just a gui to the Mac EFI that allows you to pick a bootable device. You can theoretically launch EFI executabled directly from EFI (like grub-efi), but that is a bit shaky. rEFIt is actually an EFI executable that the EFI firmware launches...

Well, I'm installing it once again, this time after installing grub-efi via apt (before starting the installation). So as far as I know, the normal grub package has been replaced by the EFI one, which will be used by Ubiquity in the install. I told it to install GRUB to /dev/sda3. I'll let you know what happens.

---

### Post by pxwpxw on 2009-01-20
> **Virtualboxbuntu said:**
> So what do you think the problem is? Is GRUB not installing because Macs use EFI, or is it something else?



Well, I'm installing it once again, this time after installing grub-efi via apt (before starting the installation). So as far as I know, the normal grub package has been replaced by the EFI one, which will be used by Ubiquity in the install. I told it to install GRUB to /dev/sda3. I'll let you know what happens.

The grub-efi 1.96 i386 or amd64 packages are a x86 build which according to tests wont go on a MacBook4,1.
For that, you need a x86_64 build, and there is a test version grub.efi you can try which will show if that is a possibility - not my x86 version. I dont have the link, I will get it.
For grub-efi, you probbly need to install the grub.efi bootloader manually by copying from linux to a hfsplus partition, not sure what the ubuntu installer might do, I think it will just install grub- legacy as before.

I wil get that link to the test prog - Details on the grub-efi thread
[http://ubuntuforums.org/showthread.php?p=6588944#post6588944](http://ubuntuforums.org/showthread.php?p=6588944#post6588944)

---

### Post by cyberdork33 on 2009-01-21
> **Virtualboxbuntu said:**
> So what do you think the problem is? Is GRUB not installing because Macs use EFI, or is it something else?I am not sure, you have a unique problem as the rest of us install grub all the time.

> **Virtualboxbuntu said:**
> So as far as I know, the normal grub package has been replaced by the EFI one, which will be used by Ubiquity in the install. I told it to install GRUB to /dev/sda3. I'll let you know what happens.Not sure what you mean by this, but grub-efi is part of GRUB2 with is not used by default in any distro that I know of.

---

### Post by Virtualboxbuntu on 2009-01-21
> **cyberdork33 said:**
> Not sure what you mean by this, but grub-efi is part of GRUB2 with is not used by default in any distro that I know of.

I mean that since, according to aptitude when I installed grub-efi, it had to remove grub-gfxboot because they both provided grub, that would cause Ubiquity to use the EFI grub instead.

Anyway, it worked! I installed grub to /dev/sda3 and it actually works, it even boots up:p

EDIT: Unfortunately, when I use isight-firmware-tools, it never extracts the firmware from /MacOSX/System/.../AppleUSBVideoSupport. It claims that it's an unknown driver. Is there anywhere I could download the firmware without having to extract it?

---

### Post by pxwpxw on 2009-01-21
> **Virtualboxbuntu said:**
> I mean that since, according to aptitude when I installed grub-efi, it had to remove grub-gfxboot because they both provided grub, that would cause Ubiquity to use the EFI grub instead.

Anyway, it worked! I installed grub to /dev/sda3 and it actually works, it even boots up:p

Magic

---

### Post by Virtualboxbuntu on 2009-01-21
> **pxwpxw said:**
> Magic

But see my edit above.

---

### Post by cyberdork33 on 2009-01-22
make sure you have the latest version of IFT from the mactel-support PPA.

If it still doesn't work, consider filing a bug to let the developer know. It may be that your file is just newer that the software knows what to do with.
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

PS, this is really a separate issue so you should start a new thread

---

### Post by Virtualboxbuntu on 2009-01-22
> **cyberdork33 said:**
> make sure you have the latest version of IFT from the mactel-support PPA.

If it still doesn't work, consider filing a bug to let the developer know. It may be that your file is just newer that the software knows what to do with.
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

PS, this is really a separate issue so you should start a new thread

Well, it did work!

Thanks for all your help, everybody! Now I can enjoy my new MacBook with the ease of use and open source software that only Linux can provide.

Now I just have to decide what theme to use... but that's another story. Good-bye! :KS

---

