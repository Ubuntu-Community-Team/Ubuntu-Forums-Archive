---
title: "USB thumb drive problems."
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by gyga on 2006-03-20
I put some files on a thumb drive (Sandisk Cruzer Mini 512MB)

The file names are there but have no information (they are empty). I also can no longer write or delete from the drive. When I try it says it is a read only drive.
:confused: :confused: 
Help me please.

---

### Post by Pragmatist on 2006-03-20
Type this when the thumb drive is not plugged in:
```
tail -f /var/log/messages
```
Now plug in the thumb drive and watch for any messages.  Post those messsages here.  When your done just type:
```
CTRL-C
```
Also, please post the output of these commands with the drive plugged in:
```
ls -l /media
```
```
mount
```
```
cat /etc/fstab
```

---

### Post by gyga on 2006-03-20
```

Mar 20 13:24:58 localhost syslogd 1.4.1#17ubuntu3: restart.
Mar 20 13:45:02 localhost -- MARK --
Mar 20 14:05:06 localhost -- MARK --
Mar 20 14:25:17 localhost -- MARK --
Mar 20 14:29:31 localhost kernel: [4299021.445000] usb 1-2: USB disconnect, addr ess 5
Mar 20 14:29:31 localhost kernel: [4299021.472000] sda : READ CAPACITY failed.
Mar 20 14:29:31 localhost kernel: [4299021.472000] sda : status=0, message=00, h ost=0, driver=04
Mar 20 14:29:31 localhost kernel: [4299021.472000] sda : sense not available.
Mar 20 14:29:31 localhost kernel: [4299021.472000] sda: Write Protect is off
Mar 20 14:29:31 localhost kernel: [4299021.472000]  /dev/scsi/host2/bus0/target0 /lun0: unknown partition table
Mar 20 14:29:42 localhost kernel: [4299032.611000] usb 1-2: new full speed USB d evice using uhci_hcd and address 6
Mar 20 14:29:42 localhost kernel: [4299032.711000] scsi3 : SCSI emulation for US B Mass Storage devices
Mar 20 14:29:42 localhost usb.agent[10158]:      usb-storage: already loaded
Mar 20 14:29:47 localhost kernel: [4299037.719000]   Vendor: SanDisk   Model: Cr uzer Mini       Rev: 0.1
Mar 20 14:29:47 localhost kernel: [4299037.719000]   Type:   Direct-Access                 ANSI SCSI revision: 02
Mar 20 14:29:47 localhost kernel: [4299037.729000] SCSI device sda: 1000944 512- byte hdwr sectors (512 MB)
Mar 20 14:29:47 localhost kernel: [4299037.732000] sda: Write Protect is off
Mar 20 14:29:47 localhost kernel: [4299037.749000] SCSI device sda: 1000944 512- byte hdwr sectors (512 MB)
Mar 20 14:29:47 localhost kernel: [4299037.752000] sda: Write Protect is off
Mar 20 14:29:47 localhost kernel: [4299037.752000]  /dev/scsi/host3/bus0/target0 /lun0: p1
Mar 20 14:29:47 localhost kernel: [4299037.762000] Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
Mar 20 14:29:47 localhost scsi.agent[10207]:      sd_mod: loaded sucessfully (fo r disk)
```

```
total 28
lrwxrwxrwx  1 root  root      6 2005-12-29 20:19 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2005-12-29 20:19 cdrom0
drwxr-xr-x  2 root  root   4096 2005-12-29 20:19 cdrom1
lrwxrwxrwx  1 root  root      7 2005-12-29 20:19 floppy -> floppy0
drwxr-xr-x  2 root  root   4096 2005-12-29 20:19 floppy0
drwx------  4 jared jared 16384 1969-12-31 19:00 usbdisk
```

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Is that what you wanted?

---

### Post by Pragmatist on 2006-03-20
yes, that is what I wanted. thanks.  Ok, a couple of questions:
1.) 
> drwx------  4 jared jared 16384 1969-12-31 19:00 usbdisk
Did you make this directory? (i.e. /media/usbdisk)

2.) What if you try and handle the files as root (put **sudo** before every command)?

3.) What kind of files (text, audio, video, etc...)? Give extensions if you have (.exe .swf .mp3 etc...)

4.) Where did the files come from? Windows?  Which one?

5.) What happens if you do this?:

```
sudo umount /dev/sda1
```
```
sudo mkdir /media/test
```
```
sudo mount -t auto /dev/sda1 /media/test
```
```
sudo cp -r /media/test/* /home/jared
```
Assuming your home directory is /home/jared

---

### Post by virgule on 2006-03-20
This look funky to me. 
```

drwx------  4 jared jared 16384 1969-12-31 19:00 usbdisk

```
Did you create this directory yourself ( at year 1969?!?!) or does it show up when you plug the usb in? My point is I have no such directory on /media and my usb stuffs load and work fine. **ivman** (code: man ivman for infos..) is the little guy who is responsible of  *mounting medias as they are inserted/attached to the system*. In theory, you should not need much interaction if at all. 

PS: ooh Pragmatist beat me to this. He replied as I was typing this message. ;) I am sure the 'usbdisk' directory is our culprit.

---

### Post by gyga on 2006-03-20
[QUOTE=Pragmatist]
1.) 

Did you make this directory? (i.e. /media/usbdisk)[/QUOTE]
No it is just what pops up when I use a thumb drive.

[QUOTE=Pragmatist]
2.) What if you try and handle the files as root (put **sudo** before every command)?[/QUOTE]
Not sure what you mean, I handle the files with the GUI (I rarely use the Terminal)

[QUOTE=Pragmatist]
3.) What kind of files (text, audio, video, etc...)? Give extensions if you have (.exe .swf .mp3 etc...)[/QUOTE] .txt, .png, .xcf, .html, .css, .js, .mp3, they have no information in them though.

[QUOTE=Pragmatist]
4.) Where did the files come from? Windows?  Which one?[/QUOTE]
All came off this computer (Ubuntu 5.10)

[QUOTE=Pragmatist]
5.) What happens if you do this?:

```
sudo umount /dev/sda1
```
```
sudo mkdir /media/test
```
```
sudo mount -t auto /dev/sda1 /media/test
```
```
sudo cp -r /media/test/* /home/jared
```
Assuming your home directory is /home/jared[/QUOTE]

```

jared@ubuntu:~$ sudo umount /dev/sda1
Password:
jared@ubuntu:~$ sudo mkdir /media/test
jared@ubuntu:~$ sudo mount -t auto /dev/sda1 /media/test
```
The thumb drive window poped up with the title "test"
```

jared@ubuntu:~$ sudo cp -r /media/test/* /home/jared
cp: cannot stat `/media/test/junk/Sound Files/Fark': Input/output error
cp: cannot stat `/media/test/junk/webtempletes': Input/output error
jared@ubuntu:~$

```
Also when I open the regular USB window it has little locks on the files now.

---

### Post by epedersen on 2006-03-20
Howdy,

I'm having a similar problem with my USB key/MP3 player.  Somehow I screwed up during the process of copying files to it/deleting old stuff.  The only thing that I can surmise is that it got unplugged during an active file transfer, which corrupted the FAT table.  (One of the tests suggests that the two FATs are different.)

I've tried to "dd if=/dev/zero of=/dev/sda1" to wipe it out completely, and many other utilities (Disk management and Norton Disk Doctor on XP; testdisk and sformat on Ubuntu) all with _no_ luck.

When I plug my key in, I can see some file folders, but some have a lock icon.  The file system shows up as being 'read-only', even if I unmount it and remount it.

Eric

---

### Post by gyga on 2006-03-20
[QUOTE=virgule]This look funky to me. 
```

drwx------  4 jared jared 16384 1969-12-31 19:00 usbdisk

```
Did you create this directory yourself ( at year 1969?!?!) or does it show up when you plug the usb in?[/QUOTE]

No I did not create it (I wasn't even alive in 1969). It just shows up.

---

### Post by Pragmatist on 2006-03-20
> 
[QUOTE]Quote:
Originally Posted by Pragmatist
2.) What if you try and handle the files as root (put sudo before every command)?
Not sure what you mean, I handle the files with the GUI (I rarely use the Terminal)[/QUOTE]
Yes, but for troubleshooting let's use the terminal.  Once we find out what is going on we can deal with the GUI part of things.

Now that your able to mount it at **/media/test**  give me the result of:
```
sudo ls -l /media/test
```

---

### Post by gyga on 2006-03-20
[QUOTE=Pragmatist]
Now that your able to mount it at **/media/test**  give me the result of:
```
sudo ls -l /media/test
```[/QUOTE]

```

total 32
-rwxr-xr-x   1 root root     0 2006-03-17 16:49 Future.txt
drwxr-xr-x  12 root root 16384 2006-03-17 16:49 junk
drwxr-xr-x   3 root root 16384 2006-03-17 16:49 proposed domains
-rwxr-xr-x   1 root root     0 2006-03-17 16:49 roundedcorner.html
-rwxr-xr-x   1 root root     0 2006-03-17 16:49 teachtofish.txt

```

---

### Post by epedersen on 2006-03-20
I fixed my own problem - but (I'm sorry to say) with the Windows utility for my MP3 player.

I remain interested in the solution to your situation.

---

### Post by Pragmatist on 2006-03-20
Backup your /etc/fstab file:
```
sudo cp /etc/fstab /etc/fstab_BACKUP
```

Open /etc/fstab in the editor called gedit
```
sudo gedit /etc/fstab
```

Put this as the last line of the /etc/fstab file.  Then save the file and exit gedit
```
/dev/sda1        /media/test  vfat    rw,user,noauto  0       0
```

Also, try this:
```
sudo umount /dev/sda1
```
```
sudo mount -t vfat /dev/sda1 /media/test
```

Then see if you can access any of the files.

---

### Post by gyga on 2006-03-21
It still doesn't work.

What if I changed this
```
/dev/sda1        /media/test  vfat    rw,user,noauto  0       0
```
to
```
/dev/sda1        /media/test  vfat    rw,**jared**,noauto  0       0
```
because my account is "jared". Or would that mess my comp up even more?

---

### Post by Pragmatist on 2006-03-21
> What if I changed this
```
/dev/sda1 /media/test vfat rw,user,noauto 0 0

```
to
```
/dev/sda1 /media/test vfat rw,jared,noauto 0 0

```


"**user**" refers to everybody.

---

### Post by Pragmatist on 2006-03-21
> It still doesn't work.

What error messages did you get?

---

### Post by gyga on 2006-03-21
[QUOTE=Pragmatist]What error messages did you get?[/QUOTE]
None, it just won't let me write to it.

---

### Post by Pragmatist on 2006-03-21
If you got no error message in response to:
```
sudo mount -t vfat /dev/sda1 /media/test
```
Then it mounted the drive.  Do this again:
```
sudo umount /dev/sda1
```
```
sudo mount -t vfat /dev/sda1 /media/test
```

And now....
```
mount
```

And give us the output of these commands.

---

### Post by gyga on 2006-03-21
[QUOTE=Pragmatist]If you got no error message in response to:
```
sudo mount -t vfat /dev/sda1 /media/test
```
Then it mounted the drive.  Do this again:
```
sudo umount /dev/sda1
```
```
sudo mount -t vfat /dev/sda1 /media/test
```[/QUOTE]

I got this error right here
```
mount: special device /dev/sda1 does not exist

```

---

### Post by Pragmatist on 2006-03-21
Try this with the drive unplugged:
```
tail -f /var/log/messages
```
Now plug in the drive and watch the terminal for new messages.  In those messages, you'll see a file location like /dev/sdxy where x represents some letter and y represents some number (/dev/sda1 is an example, so is /dev/sdc5 and so on...)

After you find out which file, then try the commands I gave in my last post, substituting this file in place of /dev/sda1

---

### Post by gyga on 2006-03-21
This is what I got.

```
Mar 21 20:45:56 localhost kernel: [4302480.456000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Mar 21 20:45:57 localhost kernel: [4302480.557000] scsi1 : SCSI emulation for USB Mass Storage devices
Mar 21 20:45:57 localhost usb.agent[10201]:      usb-storage: already loaded
Mar 21 20:46:02 localhost kernel: [4302485.566000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
Mar 21 20:46:02 localhost kernel: [4302485.566000]   Type:   Direct-Access                 ANSI SCSI revision: 02
Mar 21 20:46:02 localhost kernel: [4302485.577000] SCSI device sda: 1000944 512-byte hdwr sectors (512 MB)
Mar 21 20:46:02 localhost kernel: [4302485.580000] sda: Write Protect is off
Mar 21 20:46:02 localhost kernel: [4302485.597000] SCSI device sda: 1000944 512-byte hdwr sectors (512 MB)
Mar 21 20:46:02 localhost kernel: [4302485.600000] sda: Write Protect is off
Mar 21 20:46:02 localhost kernel: [4302485.600000]  /dev/scsi/host1/bus0/target0/lun0: p1
Mar 21 20:46:02 localhost kernel: [4302485.611000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Mar 21 20:46:02 localhost scsi.agent[10250]:      sd_mod: loaded sucessfully (for disk)


```
What am I looking for in that? I don't see any dev/sdx#.
I see lots of "sda"s but no number at the end.

---

### Post by virgule on 2006-03-22
I think you just need to re-setup the permissions has they should be. They are owned by 'root' that is why you don't get access to much at all, not even file sizes. As to why they are messed up.... It could be the teddy bear's fault for what I know.. The stick might be dead too. These have a limited, quite extensive, lifespan but still limited. On a related note, mine is from 1969 too.. but WTF group 'audio'?!?:-k 
```
 
   [virgule @ ~ ]# ls -l /media
total 28
lrwxrwxrwx  1 root    root      6 2006-03-13 02:33 cdrom -> cdrom0
drwxr-xr-x  2 root    root   4096 2006-03-13 02:33 cdrom0
drwxr-xr-x  2 root    root   4096 2006-03-13 02:33 cdrom1
lrwxrwxrwx  1 root    root      7 2006-03-13 02:33 floppy -> floppy0
drwxr-xr-x  2 root    root   4096 2006-03-13 02:33 floppy0
drwx------  4 virgule audio 16384 1969-12-31 19:00 sdd1

```

Now see my ls -l output the content is owned by me not root:
```

   [virgule @ /media/sdd1 ]# ls -l
total 28
drwx------  2 virgule audio  4096 2026-01-29 18:16 MaxSettings
-rwx------  1 virgule audio 23892 1980-01-01 00:00 virgule_STRC_5_(1-13-290)-NTSC.max

```

The permissions.. it must the permissions. If not I don't know better.

---

### Post by Pragmatist on 2006-03-22
Is there any information that you need on this thumb drive?   If not, we can start from scratch.

---

### Post by Pragmatist on 2006-03-22
Ok, here is what we want:
[http://nst.sourceforge.net/nst/docs/user/ch04s04.html](http://nst.sourceforge.net/nst/docs/user/ch04s04.html)

Start with device unplugged then type this:
```
tail -f /var/log/messages
```
Now plug in the drive and look for /dev/sdxy If it just has /dev/sdx that is fine too.

Now, if it is /dev/sda again (probably is, but when you do the above we're sure). type this:
```
ls -l /dev/sda*
```
If you don't get anything, show us the result of this:
```
ls -l /dev/sd*
```
Once we know which device file it is, do this:
```
 mount -t vfat /dev/sda1 /media/test
```
Now this:
```
df -khT /media/test
```

Note: It is essential for us to help you that you paste here ALL the output that you get to each of these commands.

---

### Post by gyga on 2006-03-22
[QUOTE=Pragmatist]Ok, here is what we want:
[http://nst.sourceforge.net/nst/docs/user/ch04s04.html](http://nst.sourceforge.net/nst/docs/user/ch04s04.html)

Start with device unplugged then type this:
```
tail -f /var/log/messages
```
Now plug in the drive and look for /dev/sdxy If it just has /dev/sdx that is fine too.

Now, if it is /dev/sda again (probably is, but when you do the above we're sure). type this:
```
ls -l /dev/sda*
```
If you don't get anything, show us the result of this:
```
ls -l /dev/sd*
```
Once we know which device file it is, do this:
```
 mount -t vfat /dev/sda1 /media/test
```
Now this:
```
df -khT /media/test
```

Note: It is essential for us to help you that you paste here ALL the output that you get to each of these commands.[/QUOTE]

I ran into an error
```

jared@ubuntu:~$ tail -f /var/log/messages
Mar 22 16:20:58 localhost kernel: [4296930.381000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
Mar 22 16:20:58 localhost kernel: [4296930.381000]   Type:   Direct-Access                 ANSI SCSI revision: 02
Mar 22 16:20:58 localhost kernel: [4296930.401000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
Mar 22 16:20:58 localhost kernel: [4296930.403000] sdb: Write Protect is off
Mar 22 16:20:58 localhost kernel: [4296930.443000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
Mar 22 16:20:58 localhost kernel: [4296930.451000] sdb: Write Protect is off
Mar 22 16:20:58 localhost kernel: [4296930.451000]  /dev/scsi/host3/bus0/target0/lun0: p1
Mar 22 16:20:58 localhost kernel: [4296930.469000] Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun 0
Mar 22 16:20:58 localhost scsi.agent[9762]:      sd_mod: loaded sucessfully (for disk)
Mar 22 16:21:58 localhost kernel: [4296990.352000] usb 1-2: USB disconnect, address 6
Mar 22 16:22:11 localhost kernel: [4297004.268000] usb 1-2: new full speed USB device using uhci_hcd and address 7
Mar 22 16:22:12 localhost kernel: [4297004.370000] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 22 16:22:12 localhost usb.agent[9973]:      usb-storage: already loaded
Mar 22 16:22:16 localhost kernel: [4297009.382000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
Mar 22 16:22:16 localhost kernel: [4297009.382000]   Type:   Direct-Access                 ANSI SCSI revision: 02
Mar 22 16:22:16 localhost kernel: [4297009.394000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
Mar 22 16:22:16 localhost kernel: [4297009.398000] sdb: Write Protect is off
Mar 22 16:22:16 localhost kernel: [4297009.416000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
Mar 22 16:22:16 localhost kernel: [4297009.419000] sdb: Write Protect is off
Mar 22 16:22:16 localhost kernel: [4297009.419000]  /dev/scsi/host4/bus0/target0/lun0: p1
Mar 22 16:22:16 localhost kernel: [4297009.429000] Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
Mar 22 16:22:17 localhost scsi.agent[10022]:      sd_mod: loaded sucessfully (for disk)

jared@ubuntu:~$ ls -l /dev/sda*
ls: /dev/sda*: No such file or directory
jared@ubuntu:~$ ls -l /dev/sd*
brw-r-----  1 root plugdev 8, 16 2006-03-22 16:22 /dev/sdb
brw-r-----  1 root plugdev 8, 17 2006-03-22 16:22 /dev/sdb1
jared@ubuntu:~$ mount -t vfat /dev/sda1 /media/test
mount: only root can do that
jared@ubuntu:~$ sudo mount -t vfat /dev/sda1 /media/test
Password:
mount: special device /dev/sda1 does not exist
jared@ubuntu:~$


```

should i use sdb1 instead of sda1?

---

### Post by Pragmatist on 2006-03-22
> Originally Posted by: **gyga**
[QUOTE]brw-r-----  1 root plugdev 8, 16 2006-03-22 16:22 /dev/sdb
brw-r-----  1 root plugdev 8, 17 2006-03-22 16:22 /dev/sdb1
jared@ubuntu:~$ mount -t vfat /dev/sda1 /media/test
*should i use sdb1 instead of sda1?*[/QUOTE]

Absolutely!  Don't worry about the fact that everytime you plug it in the device filename is different.  That is very easily taken care of.  But first I want to make sure your device is working right.  So now you know how to find out which device file is being assigned right? (i.e the tail -f /var/log/messages  technique)

You want there to a be a number in the device filename (/dev/sdb1 as opposed to just /dev/sdb).  The 1 at the end means it is the first partition.  Just like your hard drive is typically /dev/hda  but the partitions are /dev/hda1 /dev/hda2 and so on...  The instructions in the link I gave in my previous post are very thorough.  In fact I remember when I was trying to get various SD cards to work that the solution frequently had to do with there being no partitions on the card/drive or the partition being of the wrong filesystem type.  He gives this command:
```
df -k /media/test
```
I add the -T switch to find out the filesystem type of the partition.  I add the -h switch to make the numbers "human" readable (so it will say 20MB instead of 20 and a bunch of zeros).

So, once your able to mount the drive as I've explained, go ahead and run the df command as described and give us the results.

---

### Post by gyga on 2006-03-22
```

jared@ubuntu:~$ df -khT /media/test
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     vfat    489M   48M  441M  10% /media/test
jared@ubuntu:~$

```

Is that what you want? All the files claim to be 0bytes, I don't see how they can be 48M


I have learned more about linux in these last few days than in the months I have used it.:)

---

### Post by Pragmatist on 2006-03-22
> Originally Posted by **gyga**
Is that what you want? All the files claim to be 0bytes, I don't see how they can be 48M

That is exactly what I wanted. :)  

I'm sure there is some logical explanation for why those files say 0 bytes and why df reports 48MB used...I just don't know what it is :)  It does sound vaguely familiar, so if necessary we can work it out.

In the meantime, **if your sure you don't need anything on the disk**, try removing the files and then running df again to see what it reports.  That should give us some clues.

I think what happened is that somehow your filesystem got corrupted when you made you tried to copy the files over initially.  This would explain why the files are just names without content and why df reports 48MB of usage.  The filesystem is just like a bookkeeper, among other things, so if it thinks it is there, it reports it as there.  This is why I'm recommending rewriting the filesystem (takes one command and a few seconds)  However, if the files that are "on" the drive are your only copies, then we should be certain they are empty before proceeding.

Incidentally, try this: Do everything as in my previous post, but when you get up to the part where you'd run the df command (in other words, when you've mounted the drive), try this:

```
fdisk /dev/sdb
```
Note: This assumes the device is on /dev/sdbx where x is a number.  We DON'T use the number in this case since here we want to see the partition table.  When we ran df, we were looking at the filesystem usage of one partition--in our case /dev/sdb1.  However, since we are questioning the validity of the filesystems records, we need to look one step higher--the partition table of which it is a member.

---

### Post by garner_nc on 2006-03-22
Is it possible you removed the flash drive before the system finished writing the files? I imagine this would be similar to removing a mounted floppy before unmounting which flushes the data stream to the floppy before it's physically unmounted.

Just my 2 cents.

All the Best,
Doug White
Garner NC USA

---

### Post by Pragmatist on 2006-03-22
> Originally Posted by: **garner_nc**
*Is it possible you removed the flash drive before the system finished writing the files? I imagine this would be similar to removing a mounted floppy before unmounting **which flushes the data stream to the floppy before it's physically unmounted.***

What would the result of that be?

---

### Post by gyga on 2006-03-22
[QUOTE=Pragmatist]That is exactly what I wanted. :)  

I'm sure there is some logical explanation for why those files say 0 bytes and why df reports 48MB used...I just don't know what it is :)  It does sound vaguely familiar, so if necessary we can work it out.

In the meantime, **if your sure you don't need anything on the disk**, try removing the files and then running df again to see what it reports.  That should give us some clues.

Incidentally, try this: Do everything as in my previous post, but when you get up to the part where you'd run the df command (in other words, when you've mounted the drive), try this:

```
fdisk /dev/sdb
```[/QUOTE]

I have no valuable data on this drive.


I got this output?
```

jared@ubuntu:~$ fdisk /dev/sdb
You will not be able to write the partition table.

Command (m for help):


```

---

### Post by Pragmatist on 2006-03-22
Good!  Ok, if you press 'm' you'll see a list of commands.  Among those is 'p' for 'print partition table' So, **press p**  Then paste the result here.

---

### Post by gyga on 2006-03-23
```
jared@ubuntu:~$ fdisk /dev/sdb
You will not be able to write the partition table.

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500355+   6  FAT16

Command (m for help):

```

---

### Post by Pragmatist on 2006-03-23
Try these instructions which I got from here: [http://www.mobymemory.com/Content/HOWTO.Repairing.corrupted.cards.via.Linux.1178.html](http://www.mobymemory.com/Content/HOWTO.Repairing.corrupted.cards.via.Linux.1178.html)

This will allow you to start over (**again, this assumes you have nothing you need on the drive--cause its getting wiped out!**

```
fdisk /dev/sdb
```
```
p
```

now you should have what you had before:
> Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500355+   6  FAT16

Command (m for help):

```
d
```
```
n
```
```
p
```
```
1
```
```
<ENTER>
```
```
<ENTER>
```
```
t
```
```
6
```
```
p
```
Check that you now have a partition called /dev/sdb1 just like you did before. and then continue...
```
w
```
```
mkdosfs -F 16 /dev/sdb1
```

---

### Post by gyga on 2006-03-23
```

jared@ubuntu:~$ fdisk /dev/sdb
You will not be able to write the partition table.

Command (m for help): p

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500355+   6  FAT16

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-993, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-993, default 993):
Using default value 993

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): p

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500440+   6  FAT16

Command (m for help): w

Unable to write /dev/sdb
jared@ubuntu:~$ mkdosfs -F 16 /dev/sdb1
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: /dev/sdb1 contains a mounted file system.
jared@ubuntu:~$

```

Did I mess up somewhere (last two steps maybe)?

---

### Post by Pragmatist on 2006-03-23
> jared@ubuntu:~$ fdisk /dev/sdb
You will **not be able to write **the partition table.

I think you need to run **fdisk** with **sudo** So just make the first step:
```
sudo fdisk /dev/sdb
```

You will probably need to do the same with the last command (mkdosfs):
```
sudo mkdosfs -F 16 /dev/sdb1
```

---

### Post by gyga on 2006-03-23
```

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error **16: Device or resource busy.**
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
jared@ubuntu:~$ sudo mkdosfs -F 16 /dev/sdb1
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: /dev/sdb1 contains a mounted file system.
jared@ubuntu:~$

```

Is this what is suppose to happen? Should I unmount it or something?

---

### Post by Pragmatist on 2006-03-23
Try it!  Probably you are right.  I've solved this problem for myself before, but it was awhile ago and took a little tinkering.    It makes sense that to alter a partition, the drive needs to be unmounted.

---

### Post by gyga on 2006-03-23
It is fixed! thank you for all your help.

---

### Post by Pragmatist on 2006-03-23
Good job! :)

---

### Post by McLogic on 2006-04-02
[QUOTE=gyga]I put some files on a thumb drive (Sandisk Cruzer Mini 512MB)

The file names are there but have no information (they are empty). I also can no longer write or delete from the drive. When I try it says it is a read only drive.
:confused: :confused: 
Help me please.[/QUOTE]

I have almost the same problem with my USB disk -- a 128mb iRiver mp3/ogg player. I CAN write to and delete off the disk fine, but I get the zero-length files when I disconnect and reconnect the drive. 

It worked fine under 5.04, but it is not working under 5.10. It happens on a nforce desktop and a Intel 855 laptop -- WTF?  :? 

When I first "cp" the files, they say they are the right size. I can open them just fine.  If I navigate into, and then out of the copied folders, I come up to the parent folder of the files that I copied onto the disk. The player/disk says it has no files when I unplug it.

If I unplug the disk and plug it back in, the documents are of zero length. 

I think that cp is making some kind of link. This idea is supported by the short time "cp" takes to copy the files (much too fast). :mad:

---

### Post by Pragmatist on 2006-04-02
Please make a new thread.  You are much more likely for people to see your problem that way.

---

