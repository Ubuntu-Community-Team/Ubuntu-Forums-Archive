---
title: "NTFS Write permissions"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Andy-T on 2007-05-22
Guess this is a commonly asked newbie question but I've searched around and following information in other threads doesn't appear to work for me.

I can mount NTFS by using the following within /etc/fstab/:

```
/dev/sdb1 /home/newdrive ntfs umask=222,utf8 0 0
```

However, when I try to use the NTFS configuration tool it changes the entry to

```
/dev/sdb1 /home/newdrive ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

Attempting to mount now gives me the error:

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /home/andrew/newdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /home/andrew/newdrive ntfs-3g defaults,force 0 0

```

I don't have windows so can't use choice 1. When I try choice 2 I get an error saying reset $LogFile and nothing else seems to happen.

Is there anything else I can try to write to the drive?

Andy

---

### Post by Happy_Man on 2007-05-22
```
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /media/newdrive
```

Or, if you don't want to do that....
```
sudo apt-get install ntfs-config
```

Will give you a GUI frontend to ntfs-3g.

---

### Post by Inxsible on 2007-05-22
After changing to ntfs-3g, try to reboot. Dont know if that will help though !
 
If this is an external drive you should use pmount and pumount. There is no need to put in entries in the fstab for external drives or it will give you errors if you boot without connecting them.
 
```

pmount /dev/sdb1 <MOUNT_POINT>

```
 
Note: pmount requires you to create a new mount point, i.e. it wont let you mount into an existing folder

---

### Post by Andy-T on 2007-05-22
Thanks for reply Happy_Man.

I've already installed ntfs-config. It still gives me the same error as using the CLI.

Do I need to chown the mount point, or give it any special permissions?

Andy

---

### Post by Andy-T on 2007-05-22
It's an internal drive im using.

Tried restarting after using ntfs-config.. Still won't mount the drive.

Also attempted to start over by removing the fstab entry which ntfs-config left and running the program again.. It now just gives me the error

```
Error : An error occured when trying to configure
 /media/newdrive, please retry. Thanks.
```

Seems odd that it will mount read only when I manually insert entry in fstab but the GUI won't let me mount the drive at all.

Any other idea's?

---

### Post by AlexenderReez on 2007-05-22
> **Andy-T said:**
> It's an internal drive im using.

Tried restarting after using ntfs-config.. Still won't mount the drive.

Also attempted to start over by removing the fstab entry which ntfs-config left and running the program again.. It now just gives me the error

```
Error : An error occured when trying to configure
 /media/newdrive, please retry. Thanks.
```

Seems odd that it will mount read only when I manually insert entry in fstab but the GUI won't let me mount the drive at all.

Any other idea's?

how about mount manually using ntfs-config . . .its application under ---> applications --> system --> ntfs-config

refer this --->

> [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

---

### Post by Inxsible on 2007-05-22
> **Andy-T said:**
> It's an internal drive im using.
 
Tried restarting after using ntfs-config.. Still won't mount the drive.
 
Also attempted to start over by removing the fstab entry which ntfs-config left and running the program again.. It now just gives me the error
 
```
Error : An error occured when trying to configure
 /media/newdrive, please retry. Thanks.
```
 
Seems odd that it will mount read only when I manually insert entry in fstab but the GUI won't let me mount the drive at all.
 
Any other idea's?
 
Having an entry in fstab only helps in auto-mounting the drive (normally ;) ). Most people want their internal drives mounted automatically. So you would need to put the entry back. Try this link
 
[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by Andy-T on 2007-05-22
ok, still really don't know where im going wrong here! Just tried re-installing and updating ntfs-config The gui  won't configure the drive still giving me the error:

```
Error : An error occured when trying to configure
 /media/newdrive, please retry. Thanks.
```

and then giving me the config screen with enable write support option greyed out.

So, I've setup fsconfig manually, entry looks like this:

```
Error : An error occured when trying to configure
 /media/newdrive, please retry. Thanks.
```

Now running ntfs-config gives me no errors, settings look correct (enable write support for internal devices is checked)

However, this is what i end up with..

```

andrew@andrew-desktop:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/newdisk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/newdisk ntfs-3g defaults,force 0 0

```

Everything I've read & learnt so far seems to suggest that this should be working by now.

---

### Post by Andy-T on 2007-05-22
```
 mount -t ntfs-3g /dev/sdb1 /media/newdisk -o force
```

Gives me another error about unclean dismount and reset $Logfile, maxes my processor for about 10 seconds and then the computer locks up :(

Andy

---

### Post by ugm6hr on 2007-05-22
Sorry - can't help with the problem, but was intrigued as to why someone who doesn't have Windows would have a HD formatted with NTFS.  

But more importantly, why would you want to keep it with NTFS?  I would have thought the best long-term solution would be to back the drive up (which if less than half full could be done with GParted on the same drive) and then reformat.  Or am I missing something?

---

### Post by Andy-T on 2007-05-22
```
$mount -t ntfs-3g /dev/sdb1 /media/newdisk -o force
$Logfile indicates unclean shutdown (0,0)
Warning: Forced mount, reset $Logfile
fusermount:failed to acces mountpoint /media/newdisk: No Such file or directory
FUSE mountpoint creation failed
unmounting /dev/sdb1 (newdrive
```

Just to clarify, despite what the error msg says, /media/newdisk definitely exists. It appears as an empty folder at the moment.

Could this be a hardware issue?

A

---

### Post by Andy-T on 2007-05-22
It's a fair question ugm6hr, Had used the drive in Windows for storing music/video's etc..so it's pretty full and I don't have another disk big enough to back it up..

Thinking about backup solutions though, I could probably move some of the stuff onto my main drive to get it under 50% full. Will have a look into GParted. Cheers.

Andy

---

### Post by Andy-T on 2007-05-23
Any idea's on what I could try in the shorter term though?

---

### Post by trickyzach on 2007-07-24
Andy

I finally figured this out.

With the drives UNMOUNTED (even with just read access)

sudo mv /media/newdrive /medianewdrive1

Then run the NTFS-Config again and it will work, it may warn you thought that the drive needs to be checked. Just copy paste the command into terminal and your good to go.

whew i was pullin out my hair :)

Zach

---

