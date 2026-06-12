---
title: "I can't mount my NFTS USB Harddrives"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mkirkelund on 2007-10-24
Hi all.

I've just installed ubuntu 7.10. But I can't mount my NTFS usb harddrives (I have two). How do I mount them so I can read and write?
When tried Fiesty Fawn, I could perfectly see them.

What do I do so I can see my harddrives?

/Mkirkelund

---

### Post by chamberlain2006 on 2007-10-24
When you connect the drive, does an icon show up on the desktop?

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> When you connect the drive, does an icon show up on the desktop?

No. I dont. Should it?

---

### Post by chamberlain2006 on 2007-10-24
That's surprising.  Can you please type "fdisk -l" when the drive is connected, and post the output?

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> That's surprising.  Can you please type "fdisk -l" when the drive is connected, and post the output?

where should I write that? In the teminal?

(I kind of new to linux :))

---

### Post by chamberlain2006 on 2007-10-24
yes, sorry, should have mentioned that.  Go to "Applications>Accessories>Terminal" to do so.

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> That's surprising.  Can you please type "fdisk -l" when the drive is connected, and post the output?


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7db897d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
michael@michael-laptop:~$ 

Here is the output

---

### Post by chamberlain2006 on 2007-10-24
Ok.  The disks ARE recognized.  Try typing this in the terminal:

```

sudo mkdir /media/external
sudo mount /dev/sdb1 -t ntfs /media/mount

```

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> Ok.  The disks ARE recognized.  Try typing this in the terminal:

```

sudo mkdir /media/external
sudo mount /dev/sdb1 -t ntfs /media/mount

```

Ehm. I don't understand this: 
michael@michael-laptop:~$ sudo mkdir /media/external
mkdir: cannot create directory `/media/external': File exists
michael@michael-laptop:~$ sudo mount /dev/sdb1 -t ntfs /media/mount
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/mount -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/mount ntfs-3g defaults,force 0 0
michael@michael-laptop:~$ 

?

---

### Post by chamberlain2006 on 2007-10-24
Try this then...

```

sudo mount -t ntfs-3g -o force /dev/sdb1 /media/external

```

---

### Post by chamberlain2006 on 2007-10-24
Beware though, NTFS on Linux is still a bit iffy.  Use at your own risk !

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> Try this then...

```

sudo mount -t ntfs-3g -o force /dev/sdb1 /media/external

```

Perfect. That worked for one of then. How about the other?

---

### Post by chamberlain2006 on 2007-10-24
For the next one, do the following (remember the warning though :P)

```

sudo mkdir /media/external2
sudo mount -t ntfs-3g -o force /dev/sdc1 /media/external2

```

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> For the next one, do the following (remember the warning though :P)

```

sudo mkdir /media/external2
sudo mount -t ntfs-3g -o force /dev/sdc1 /media/external2

```

Okay. Thanks for the help.

I have an other problem. I can't seem to start some programs like: Pidgin and Azureus. 
And I can't download with the bittorrent og ktorrent? It just makes a failure.

---

### Post by chamberlain2006 on 2007-10-24
First of all, to make those changed permanent, in terminal, type

```
gksudo gedit /etc/fstab
```

and add 

```

/dev/sdb1	/media/external ntfs-3g	rw,user,noauto,force	0	0
/dev/sdc1	/media/external2 ntfs-3g	rw,user,noauto,force	0	0

```

to the end.

---

### Post by chamberlain2006 on 2007-10-24
Ok.  Let's see what we can do with Pidgin. In terminal, type pidgin and post the output, please.

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> Ok.  Let's see what we can do with Pidgin. In terminal, type pidgin and post the output, please.

Done and pidgin works fine suddenly :).

Do you know if there is a driver for the trackpoint on my Lenovo T61? It's so that I can use the scroll button. I don't know if you know this?

---

### Post by chamberlain2006 on 2007-10-24
According to [http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html](http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html) the trackpoint should work.  In terminal, try this:

```
cat /dev/mouse0
```

and try touching the trackpoint.  Warning though, this will produce a lot of output and beeps, thats ok.  Just close the window when you're done.  If nothing shows up, try changing mouse0 to mouse1.

---

### Post by chamberlain2006 on 2007-10-24
Sorry that should be "sudo cat /dev/input/mouse0"

---

### Post by chamberlain2006 on 2007-10-24
Oh do you mean the scroll doesn't work?

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> According to [http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html](http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html) the trackpoint should work.  In terminal, try this:

```
cat /dev/mouse0
```

and try touching the trackpoint.  Warning though, this will produce a lot of output and beeps, thats ok.  Just close the window when you're done.  If nothing shows up, try changing mouse0 to mouse1.

Nothing happends when i write that?

And an other thing. I've just plugged in a USB mouse, but nothing happens?

---

### Post by chamberlain2006 on 2007-10-24
I didn't read that properly.  Did you mean that the scroll doesn't work?

---

### Post by mkirkelund on 2007-10-24
Yes. I can use the trackpoint perfect, just not the scroll.
Notice I mean the TRACKPOINT and not the mousepad.

---

### Post by chamberlain2006 on 2007-10-24
Ok that makes more sense. All you have to do is edit a file.  In terminal, type this:

```
gksudo gedit /etc/fstab
```

Find the section that says 	

Section "InputDevice"
Identifier      "Configured Mouse"

Put a "#" in front of the line that says "Option          "Emulate3Buttons"      "true""

And add the following lines right afterwards.

		Option          "EmulateWheel"          "true"
		Option          "EmulateWheelTimeOut" "200"
		Option          "EmulateWheelButton"    "2

Save the file.  Then restart the X server (all of your programs will be closed, so make sure anything important is saved)  then type CTRL+ALT+Backspace.

---

### Post by mkirkelund on 2007-10-24
I can't find that. I just copy-paste:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2da1d500-6a32-4a72-b013-371a0141e2c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=D6245BD2245BB3E9 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=c0b6ef9b-c93f-4c4c-9b4b-95589783aa3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1	/media/external ntfs-3g	rw,user,noauto,force	0	0
/dev/sdc1	/media/external2 ntfs-3g	rw,user,noauto,force	0	0

Btw. I just restarted, and i wrote that in the terminal you said, but I can't see the harddrives again?

---

### Post by chamberlain2006 on 2007-10-24
I'm sorry, I said the wrong file.  Delete those lines again.  The proper file was "/etc/X11/xorg.conf"

---

### Post by mkirkelund on 2007-10-24
> **chamberlain2006 said:**
> I'm sorry, I said the wrong file.  Delete those lines again.  The proper file was "/etc/X11/xorg.conf"

Hm.. Wierd:
michael@michael-laptop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
michael@michael-laptop:~$

---

### Post by chamberlain2006 on 2007-10-24
You have to type "gksudo gedit /etc/X11/xorg.conf"

---

