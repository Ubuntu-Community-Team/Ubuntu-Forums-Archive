---
title: "Gedit shows no info for docs... more NTFS woes"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-06-20
I made this post yesterday: [http://ubuntuforums.org/showthread.php?t=478868](http://ubuntuforums.org/showthread.php?t=478868)

and got my drive mounted.

Now, when I try to open the drive, it tells me I don't have permission to mount the drive.  I did change the fstab file as it told me to, but I thought I might want to change it back since I'm having these other problems.  The issue is, I can open it through the file system, but I can't edit it because I don't have permission to do so.

BUT, when I run this

> sudo gedit etc/fstab

the file shows no data, totally blank inside the gedit window. 

Is there a way to auto-mount my external HD so that I don't have to go through this every time I restart Ubuntu?  I'd like it if the drive was just, well... there.

---

### Post by Inxsible on 2007-06-20
etc/fstab is VERY DIFFERENT than /etc/fstab.
 
Notice the / in front of the etc

---

### Post by Inxsible on 2007-06-20
if its an external drive you should use pmount to mount it.
 
you can install pmount by
```
sudo aptitude install pmount
```

---

### Post by nothinghead on 2007-06-20
See, I know it should have the / in front of the etc, yet somehow I mistyped that EVERY time I did it, man I feel dumb sometimes.

I've edited fstab back to how it was before I went monkeying around with it and now I'll try what you said regarding mounting...

---

### Post by Inxsible on 2007-06-20
> **nothinghead said:**
> See, I know it should have the / in front of the etc, yet somehow I mistyped that EVERY time I did it, man I feel dumb sometimes.
 
I've edited fstab back to how it was before I went monkeying around with it and now I'll try what you said regarding mounting...
 
Happens to the best of us !!
 
you can mount external drives by
 
```
sudo pmount <device name> <mount point>
```
 
mount point can be something like MyDrive or Seagate or whatever else you want to call it. Make sure you DO NOT already have a folder with that name under /media. pmount actually creates the folder for you under /media.

---

### Post by nothinghead on 2007-06-20
I got the drive mounted using pmount, but when I restart, I have to do that again, is there a way to make it mount on startup?

---

### Post by Inxsible on 2007-06-20
pmount mounts my drives automatically. All i do now is connect my drive and I am good to go !
 
Also I have no entries in the fstab for my external drives

---

### Post by scrooge_74 on 2007-06-20
Everyday I learn something new thanks lnxsible.  I did a check and pmount is already install by default

---

### Post by Inxsible on 2007-06-20
> **scrooge_74 said:**
> Everyday I learn something new thanks lnxsible. I did a check and pmount is already install by default
No problem. Glad to have helped !

---

### Post by nothinghead on 2007-06-20
It's mounted, I see it if I "sudo nautilus" but it tells me I don't have permissions to access it just as me.  

It's an NTFS drive which I think has something to do with it, because through "sudo nautilus" i tried to edit permissions/ownership and read/write access but it wouldn't let me do that.  

I don't know if you need more info or if this is at all helpful, I'm been pondering and trying things, but no luck so far.

EDIT: I've installed ntfs-3g but I feel like maybe pmount and ntfs-3g aren't playing nice together?

---

### Post by logos34 on 2007-06-20
> It's an NTFS drive which I think has something to do with it, because through "sudo nautilus" i tried to edit permissions/ownership and read/write access but it wouldn't let me do that.
...
EDIT: I've installed ntfs-3g but I feel like maybe pmount and ntfs-3g aren't playing nice together?

Get the gui package

sudo apt-get install ntfs-config

Click "enable write support for external device".  It should edit fstab for you so it mounts with permissions.  might have to restart.

---

### Post by Inxsible on 2007-06-20
pmount has no problems playing nice with ntfs-3g. I know coz I do that all the time.
Have you tried changing the permissions/ownership on the mount point?
 
```
sudo chown -R <your username>:<your group> <device mount point>
```

---

### Post by nothinghead on 2007-06-20
I'm really sorry, I've been running Ubuntu for two days and I think this is the only thing left that I just can't get working correctly.

Upon startup, double-clicking on my external HD gives me the error:
> Volume is scheduled for check. Please boot into Windows TWICE, or use the 'force' mount option. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/Media -o force. Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/Media ntfs-3g defaults.force 0 0

If I force the mount I can access the drive and have read-write access to it as myself.

If I use pmount, I can only access the drive as root and do not have read-write access.

Both of these seem to reset when I restart and I am back to square one with the above "Cannot mount volume" error.  

Oh, and even when ntfs-config says that I have write access to the drive, when using pmount, I don't.

---

### Post by logos34 on 2007-06-20
i'd get the ntfs-3g utility pkg and run a check on that.  And/or CHKDSK with repair option in windows.

sudo apt-get install ntfsprogs

run the program 'ntfsfix' on it (unmounted)

---

### Post by nothinghead on 2007-06-20
I don't have windows installed, and I've previously run ntfsfix, before I couldn't mount it under any circumstances, running it again doesn't change any of the above.

---

### Post by Inxsible on 2007-06-20
> **nothinghead said:**
> I'm really sorry, I've been running Ubuntu for two days and I think this is the only thing left that I just can't get working correctly.
 
Upon startup, double-clicking on my external HD gives me the error:
 
 
If I force the mount I can access the drive and have read-write access to it as myself.
 
If I use pmount, I can only access the drive as root and do not have read-write access.
 
Both of these seem to reset when I restart and I am back to square one with the above "Cannot mount volume" error. 
 
Oh, and even when ntfs-config says that I have write access to the drive, when using pmount, I don't.
 
Have you tried commenting out the entry for that /dev/sdb1 in fstab?
 
I never keep entries for external drives in fstab. Additionally try logging into windows and do the 'Safely Remove Hardware' thing. Sometimes Windows creates a lock on the filesystem if the drive isnt cleanly removed.

---

### Post by Inxsible on 2007-06-20
> **nothinghead said:**
> I don't have windows installed, and I've previously run ntfsfix, before I couldn't mount it under any circumstances, running it again doesn't change any of the above.
 
Too late. Is there any other Windows computer you could connect it to ?

---

### Post by nothinghead on 2007-06-20
The fstab entry is gone.  I was able to edit that out thanks to your help.

I could try one of those thumb drive windows bootable installs or take the drive with me to work tomorrow and try it there.

Are all of my problems based on that?

---

### Post by nothinghead on 2007-06-20
Holy crap I fixed it myself!

When I ran that command to force mount, it worked fine, gave me read/write access as me (no need to sudo), I just didn't want to have to manually run that at every startup, so I found another post regarding editing the local.rc file, so I edited that, added the line to my boot routines, and now Ubuntu starts up giving me full access to my drive at the user level!

Do you know how exciting it is to figure something out for myself like that?

I got my printer installed today, and now this, awesome!

Thanks for all your help.

---

