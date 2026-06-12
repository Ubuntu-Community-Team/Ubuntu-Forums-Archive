---
title: "more trouble mounting cd rom drive"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by itsdevivi on 2007-07-25
I am using a pc, not a laptop
and i typed in the terminal (with the cd in and everything)

: 

sudo mount/media/cdrom0

then i have to give it a password
i tried typing in my username login password but that did not work
then i pressed enter and went down a line then tried typing in my pw but it still did not work
im trying to install new software and help will be helpful :)

---

### Post by sad_iq on 2007-07-25
The command is ```
sudo mount /media/cdrom
``` Note the space after mount??

---

### Post by jcarlock on 2007-07-25
Well first off is that your syntax for that command is incorrent.

sudo mount <device> <location>

So assuming that your cdrom 'device' is located at /dev/cdrom and your would like to mount your cdrom to the /media/cdrom directory...

First make sure the /media/cdrom directory exists,  You can do this by typing...

ls /media

and you should see a directory, or symbolic link to cdrom, or cdrom0.

if not you will have to run...

sudo mkdir /media/cdrom

Then enter your password when prompted (this assumes you are the admin on the PC).  

Once you have created the directory (using mkdir - make directory) then your run the command...

sudo mount /dev/cdrom /media/cdrom

Then type your password when prompted.  Now ubuntu should automatically mount your cdrom once inserted, so I have questions in general about the validity of your setup.

Hope that helps.

JC

---

### Post by sad_iq on 2007-07-25
> **jcarlock said:**
> Well first off is that your syntax for that command is incorrent.
sudo mount <device> <location>
JC
I believe that mount will look at /etc/fstab and /etc/mtab first ... so if there is an entry that points to /media/cdrom (location) it will have an entry to /dev/cdrom(device) and use that...so there is no need to supply the <device> unless there is no <location> entry in any of these files(could be wrong thou!!!)

---

### Post by jcarlock on 2007-07-25
I was making a generalization, but I think the issue may still be syntax...

Note his command...


sudo mount/media/cdrom0

should be, at the very least,

sudo mount /media/cdrom0

He may have forgotten the space between mount and /media

Also, I am very new to these forums, not to linux, thats why I started in the beginners section.

JC

---

### Post by itsdevivi on 2007-07-25
great i did all of that now i have password troubles i cant type it in!

---

### Post by sad_iq on 2007-07-25
You can type it...it just won't print anything...security stuff :)

> I was making a generalization, but I think the issue may still be syntax...
  Note his command...
  sudo mount/media/cdrom0
  should be, at the very least,
  sudo mount /media/cdrom0
  He may have forgotten the space between mount and /media
  Also, I am very new to these forums, not to linux, thats why I started in the beginners section. 

 I allready stated the space thing...also sorry for my bad posting(all that /etc/fstab thing)...didn't mean anything bad...this is not a war :) ...  in this case i just replied because I thought it was the right answer, in another case...your answer is the right one...if it's not..please correct me...I just try to help others and learn more things!!! :)

---

### Post by itsdevivi on 2007-07-25
lol okay i just felt stupid there anyways (i am new)
 "no mount found" comes up
after i typed in sudo mount /media/cdrom0
even though i confirmed that i have those files cdrom and cdrom0

so do i type in

sudo mount /dev/cdrom /media/cdrom 

????

---

### Post by itsdevivi on 2007-07-25
do i have to mount the cd rom then once its mounted then go to directory then click it to start loading the files from the cd

OR

is there anyway i can (without mounting) type in the terminal something to start loading the files if not please help me im having trouble mounting

it says something like no mount found and the file/directory (cdrom , cdrom0) already exists plzzzzzzz help!:confused:

---

### Post by sad_iq on 2007-07-25
let's use this command to see where how your cd gets mounted: ```
cat /etc/fstab |grep cdrom
```
 It will print something like **/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0**(yours will not be the same)...but it's the /dev/scd0 that we'll need...so your mount command will be **sudo mount /dev/scd0 /media/cdrom0** (replace **scd0** with what you get from the previous command)!!!

---

### Post by annda on 2007-07-25
i'm not sure which update broke automounting, but until someone wiser comes along can you find which device your cdrom is assigned to?

```
sudo lshw -class disk
```

this should show you what to mount manually. for example, if your cdrom is /dev/sr0 you can mount it like that:

```
sudo mount /dev/sr0 /media/cdrom
```

i hope it works. if it doesn't, please post the errors.

---

### Post by cody50 on 2007-07-29
I am having trouble auto mounting as well with the cd drive. In my fstab it says that it should be /dev/scd0

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=80b844fb-5070-4cd1-9c72-428456eb3767 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d3a7ecbd-bd6f-4c6b-b3e1-6f3ba7adbd58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/storage ext3    defaults,errors=remount-ro 0       1

```

my output from the command ```
sudo lshw -class disk

```

is

```
 *-disk:0                
       description: SCSI Disk
       product: WDC WD600AB-22CB
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 04.0
       serial: WD-WMAA61429531
       size: 55GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 54GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1474MB
          capacity: 1474MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1474MB
             capabilities: nofs
  *-disk:1
       description: SCSI Disk
       product: WDC WD400BB-75AU
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 18.2
       serial: WD-WMA6R2544070
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.1.0,1
          logical name: /dev/sdb1
          capacity: 37GB
          capabilities: primary

```

no cdrom in sight. when I browse around /dev I do not see anything that In my experience that would be a cdrom drive. there is no scd or cdrom.  anyone have any ideas?

---

### Post by cody50 on 2007-08-04
Is it possible that an update caused this? have other people found that an update broke automounting?

---

