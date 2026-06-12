---
title: "SATA hotswap - Drive only detected if i reboot with it in"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by spamalam on 2006-08-19
I'm having this problem with ubuntu that i didn't have with windows.  Its regarding hot-swap sata drives i use with several internal hotswap bays.  In windows when i plug in a drive, it is detected and mounted.  However, in ubuntu, it isn't detected and doesn't appear on the list of devices.  If however i reboot with the drive in, it then appears under the list of devices.

How can i get ubuntu to detect my drives that I switch in and out whilst the pc is running?

Here's an example.  I boot my machine with no device in the bay.  I then plug in my SATA drive into one of the bays.

% ls /dev/sd*
/dev/sda  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdc

The device is not appearing.  Now if i leave the drive in, and then reboot my machine, i get this:

% ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdc

So ubuntu can obviously find the drive, but it doesn't seem to be loading it when i plug it in, which windows does with no problems.

Now the thing is, if i do this:

% dmesg
[  435.174694] nv_sata: Primary device added

So its obviously detecting that a device is being plugged in but it is not being listed as a dev.

---

### Post by em3raldxiii on 2006-08-20
As far as I know, you need to "tell" the computer to mount a drive when you are using Linux. It's not really a "failing" of sorts, it's more of a security thing I beleive.
 
Now, there are probably really easy fixes for this and/or a little package you can install to actively detect and mount your drive. In the meantime, you may want to find out if you can make your computer treat it like a different kind of drive. For example, your optical drives only actively mount when there is media in the drive - so your fstab has the entry but doesn't mount it unless there's media. The same may be possible for a hotswap drive.
 
Do some searches here in the forums for hotswap and you might find the answer. Let me know if you find a solution so we can help others with the same concerns. :D
 
*EDIT:  I was just thinking, perhaps you can create a script to mount the drive once it's connected to the computer.  Something to the effect of **mount -a** ... except that that command will only work for drives in your fstab as far as I know.*

---

### Post by TuxCrafter on 2006-08-21
I now what you mean I have a sil 3112 and a sil 3512 and via chip on my en12000 that don't support hot plug of the hard drives under linux (there is also something of hot plug of the pci chip).

[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)
[http://home-tj.org/wiki/index.php/Libata-tj-stable](http://home-tj.org/wiki/index.php/Libata-tj-stable)

[http://www.addonics.com/support/faqs/pmsupport_server.pdf#search=%22libata-tj-2.6.17.4-20060710.tar%22](http://www.addonics.com/support/faqs/pmsupport_server.pdf#search=%22libata-tj-2.6.17.4-20060710.tar%22)

I will compile the linux-2.6.17.4 kernel with the libata-tj-2.6.17.4-20060710 patch and hope my new sil 3512 will have hotswap support for the harddrive's.

```
libata now handle all cold/warm/hot plugging through single hotplug
path.  All converted drivers support warm plugging whether the port
is SATA or PATA.

Warmplug can be requested with the following command.

  # echo 0 DEV_ID 0 > /sys/class/scsi_host/hostHOST_ID/scan

You can find out HOST/DEV_ID by reading the boot log or
/proc/scsi/scsi.

  # cat /proc/scsi/scsi
  Attached devices:
  Host: scsi9 Channel: 00 Id: 00 Lun: 00
    Vendor: ATA      Model: Maxtor 6B080M0   Rev: BANC
    Type:   Direct-Access                    ANSI SCSI revision: 05
  ...

'-' serves as wildcard, so the following command requests scan of all
devices on host0.

  # echo 0 - 0 > /sys/class/scsi_host/host0/scan

Similary, warm unplugging is requested by

  # echo 1 > /sys/class/scsi_device/0\:0\:1\:0/device/delete

If you have a controller which supports hotplugging.  You wouldn't
need any of above.  Just plug and unplug those damn things.
```

---

### Post by spamalam on 2006-09-03
> As far as I know, you need to "tell" the computer to mount a drive when you are using Linux. It's not really a "failing" of sorts, it's more of a security thing I beleive.
Is there a command I can type to force linux to recheck what hardware is attached?  Like what must happen at startup.  I mean if i start up with it plugged in it finds it, so is there a command i can type so it rechecks all of the /dev/sd* to see what's attached hardware wise?  Manually mounting i have no problems with, but i can't do that until the device is seen. :(

I keep lots of backed up files on these hdd, they are permanant, i usually just plug them in, copy some files across, then unplug them and put them back in storage.

I really wouldn't know how to patch the kernal, or if that would work :(  Did that work for you TuxCrafter?

---

### Post by TuxCrafter on 2006-09-04
No the hotswap support is not yet fully implented. Its a shame i now use 2.6.17.11 as my kernel. I have 3 types of sata chips and two of them should have hot swap support but linux doent have the correct drivers. It is even so bad that my SIL 3512 is working but it is unstable if i mount my 320G disk on this chip with reiserfs and i give it a hard time they crash. (ata time outs)

I will geep trying to use the latest kernels, because there is a lot of hardware thats not working with linux. (dolby surround)

---

### Post by bluntu on 2006-09-13
I just bought SATA HDD and inserted into my comp. It detected and I managed to formatted as Extended3.

Its access path is /media/MYBACKUP and I can access it, it's blank with a link "lost+found" and I can't create files in this new SATA drive. What do I have to do to be able to read/write?

---

### Post by TuxCrafter on 2006-09-14
wat is you question? If it works you can use is as a normal hdd

---

### Post by em3raldxiii on 2006-09-14
You **may** have to change the permissions for the drive.

I am not 100% sure, but perhaps you could try this in your console:

```

sudo chmod 777 /media/MYBACKUP

```

I don't know if that would work, but it's worth a try.

Alternatively, there may be something you can do in your FSTAB file:

```

gksudo gedit /etc/fstab

```

Then you look for your specific drive (make sure you have the right entry!) and I believe it's the UMASK number you want to change to something like 777 (you should get confirmation from someone else - I am not a linux guru).

---

### Post by TuxCrafter on 2006-09-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       		<dump>  <pass>
proc            /proc           proc    	defaults        		0       0
/dev/hda1       /               reiserfs 	notail,noatime	        	0       1
/dev/hda2       none            swap    	sw              		0       0
/dev/hda3	/mnt/hda3 	reiserfs 	rw,noatime,data=writeback 	0	0
#/dev/hdd	/media/cdrom0   udf,iso9660 	user,noauto    	 		0       0
```

Example!

PS i did not see your question in my previous post :-k  :)

But this question doesn't have to do anything with the ability to hot swap a sata drive under Linux :-D

---

### Post by em3raldxiii on 2006-09-14
Hey 'crafter, 2 things I am wondering:  1) I assume you are pointing to your **hda3** entry in the fstab, correct?  2) Outa curiousity, why **reiserfs**?  I've yet to understand which formats are good for what ... :D

---

### Post by TuxCrafter on 2006-09-14
> **em3raldxiii said:**
> Hey 'TuxCrafter, 2 things I am wondering:  1) I assume you are pointing to your **hda3** entry in the fstab, correct?  2) Outa curiousity, why **reiserfs**?  I've yet to understand which formats are good for what ... :D

Yes indeed, the world of file systems is hard to get a good grep of.

I use reiserfs because it is out of the somewhat box faster than ext3 (that is because the way the journalling is working)

Reiserfs is also some what faster for high IO on small files.

However it does do a journalling write every 4 seconds. This mains the hard drive must be active al the time, unlike ext3. So its not so good for laptops or systems that power down hard drives.

I write this information out of my head so I am nog sure it is totally correct so please correct me if possible.

information: man mount
/dev/hda3(device link)	/mnt/hda3 (place were to mount) reiserfs(file system) 	rw (read an write access), defaults

---

