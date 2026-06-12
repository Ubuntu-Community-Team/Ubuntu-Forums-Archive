---
title: "USB flash drive not mounting"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Prime_Numbers on 2007-01-13
My USB flash drives were working fine and now they have stopped mounting.  I went into Computer and try to manually mount it and I recieve and error message:  "unable to mount the selected volume"  error: could not execute pmount.
Then I right clicked on the device and went to properties, permissions and only the READ box is selected for owner, group and others.  I tried to select the WRITE and EXECUTE boxes and I get an error message:  "The permissions could not be changed". 
Has anyone experienced this before?

---

### Post by Prime_Numbers on 2007-01-13
Giving this post a little bump

---

### Post by SuperMike on 2007-01-14
Seems the OS is unstable somehow. Try looking in your ~/.bash_history and /root/.bash_history to see what you might have done?

Also, what happens when you do:

$ sudo tail -f /var/log/messages
<insert drive on USB port now>

Does a new entry appear, describing your drive? That's a good clue if so.

What happens when you try to manually mount the devices with:

$ sudo mount /dev/sda /media/usb

or

$ sudo mount /dev/sdb /media/usb

and then try to visit '/media/usb' with your File Browser?

---

### Post by Mimsy on 2007-01-14
I had a similar problem around Thanksgiving, when my USB drive suddenly refused to mount. I posted a desperate plea for help and, as usual in this forum, help was readily available. Here's the thread with my posts and the excellent solution provided by a very patient taurus:
[http://ubuntuforums.org/showthread.php?t=304420](http://ubuntuforums.org/showthread.php?t=304420)

/Mimsy

---

### Post by Prime_Numbers on 2007-01-14
> **SuperMike said:**
> Seems the OS is unstable somehow. Try looking in your ~/.bash_history and /root/.bash_history to see what you might have done?

Also, what happens when you do:

$ sudo tail -f /var/log/messages
<insert drive on USB port now>

Does a new entry appear, describing your drive? That's a good clue if so.

What happens when you try to manually mount the devices with:

$ sudo mount /dev/sda /media/usb

or

$ sudo mount /dev/sdb /media/usb

and then try to visit '/media/usb' with your File Browser?



I get this:

krash@Krash:~$ /root/.bash_history
bash: /root/.bash_history: Permission denied
krash@Krash:~$ sudo tail -f /var/log/messages
Jan 13 22:02:34 Krash gconfd (krash-4702): Resolved address "xml:readonly:/etc/g conf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 13 22:02:34 Krash gconfd (krash-4702): Resolved address "xml:readwrite:/home /krash/.gconf" to a writable configuration source at position 1
Jan 13 22:02:34 Krash gconfd (krash-4702): Resolved address "xml:readonly:/etc/g conf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 13 22:02:34 Krash gconfd (krash-4702): Resolved address "xml:readonly:/var/l ib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 13 22:02:34 Krash gconfd (krash-4702): Resolved address "xml:readonly:/var/l ib/gconf/defaults" to a read-only configuration source at position 4
Jan 13 22:02:42 Krash gconfd (krash-4702): Resolved address "xml:readwrite:/home /krash/.gconf" to a writable configuration source at position 0
Jan 13 22:22:01 Krash -- MARK --
Jan 13 22:42:01 Krash -- MARK --
Jan 13 23:02:01 Krash -- MARK --
Jan 13 23:22:02 Krash -- MARK --
Jan 13 23:25:10 Krash kernel: [ 5071.627133] usb 1-2.3: new full speed USB devic e using uhci_hcd and address 4
Jan 13 23:25:10 Krash kernel: [ 5071.748160] hub 1-2.3:1.0: USB hub found
Jan 13 23:25:10 Krash kernel: [ 5071.750080] hub 1-2.3:1.0: 1 port detected
Jan 13 23:25:11 Krash kernel: [ 5072.058951] usb 1-2.3.1: new full speed USB dev ice using uhci_hcd and address 5
Jan 13 23:25:11 Krash kernel: [ 5072.592665] SCSI subsystem initialized
Jan 13 23:25:11 Krash kernel: [ 5072.619387] Initializing USB Mass Storage drive r...
Jan 13 23:25:11 Krash kernel: [ 5072.620875] scsi0 : SCSI emulation for USB Mass  Storage devices
Jan 13 23:25:11 Krash kernel: [ 5072.622193] usbcore: registered new driver usb- storage
Jan 13 23:25:11 Krash kernel: [ 5072.622395] USB Mass Storage support registered .
Jan 13 23:25:16 Krash kernel: [ 5077.621570]   Vendor: USB 2.0   Model: Flash Di sk        Rev: 1.00
Jan 13 23:25:16 Krash kernel: [ 5077.621614]   Type:   Direct-Access           ANSI SCSI revision: 00
Jan 13 23:25:16 Krash kernel: [ 5077.737990] Driver 'sd' needs updating - please  use bus_type methods
Jan 13 23:25:16 Krash kernel: [ 5077.744535] SCSI device sda: 4005888 512-byte h dwr sectors (2051 MB)
Jan 13 23:25:16 Krash kernel: [ 5077.749448] sda: Write Protect is off
Jan 13 23:25:16 Krash kernel: [ 5077.764596] SCSI device sda: 4005888 512-byte h dwr sectors (2051 MB)
Jan 13 23:25:16 Krash kernel: [ 5077.770416] sda: Write Protect is off
Jan 13 23:25:16 Krash kernel: [ 5077.770614]  sda: sda1
Jan 13 23:25:16 Krash kernel: [ 5077.779116] sd 0:0:0:0: Attached scsi removable  disk sda
Jan 13 23:25:16 Krash kernel: [ 5077.822914] sd 0:0:0:0: Attached scsi generic s g0 type 0

---

### Post by Prime_Numbers on 2007-01-14
> **Mimsy said:**
> I had a similar problem around Thanksgiving, when my USB drive suddenly refused to mount. I posted a desperate plea for help and, as usual in this forum, help was readily available. Here's the thread with my posts and the excellent solution provided by a very patient taurus:
[http://ubuntuforums.org/showthread.php?t=304420](http://ubuntuforums.org/showthread.php?t=304420)

/Mimsy


I read the thread and I think Im having a slightly different problem.  I cannot execute pmount.

---

### Post by Mimsy on 2007-01-14
That's a bummer. It's probably because the reason it wouldn't mount is different in your case and mine.

Good luck, I hope you find a solution!

/Mimsy

---

### Post by Prime_Numbers on 2007-01-14
> **Mimsy said:**
> That's a bummer. It's probably because the reason it wouldn't mount is different in your case and mine.

Good luck, I hope you find a solution!

/Mimsy

Thanks for your help though!

---

### Post by SuperMike on 2007-01-14
Prime_Numbers: to look at bash_history, it's:

$ sudo gedit /root/.bash_history

and

$ sudo gedit ~/.bash_history

One looks at the bash_history for the root account, and the other one looks at your own bash_history.

Also, on the /var/log/messages, I see your device mounts as 'sda1'. Therefore, try this:

$ sudo mkdir /mnt/testusb
$ sudo chmod a+rw /mnt/testusb
$ sudo mount   /dev/sda1   /mnt/testusb

Now take your File Browser (aka Nautilus) and visit /mnt/testusb. Do you see files? Can you read/write to them?

---

### Post by Prime_Numbers on 2007-01-14
Well just in case there is someone else out there who has the same problem, here's what finally worked for me:

Go to System, Administration, Users & Groups

highlight the user (YOU) and click Properties

Click the User Privileges tab and select "ENABLE ACCESS TO EXTERNAL STORAGE AUTOMATICALLY".  Close window.

REBOOT

Insert your flash drive and the computer will automatically recognize it and an icon will pop-up on your desktop.

Right click your flash icon and go to Properties

Select READ WRITE EXECUTE boxes.

And that should be it.  At least it was what worked for me :cool:

---

### Post by SuperMike on 2007-01-14
Interesting. So it was a security issue all along. Wonder how that got messed up.

---

