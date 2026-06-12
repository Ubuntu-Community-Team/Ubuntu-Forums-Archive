---
title: "Saving Open Office files to FAT32"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by andyb.uk on 2006-09-11
I've just installed a second hard disk,and formatted it as FAT32, intending to use it for all my data files- shared between XP and Kubuntu.I used the guide here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite), but was then unable to write Open Office documents to this drive.

Other documents appear to save fine- it's just OO docs.  The message I get is "Saving using protocol"media" is not supported"

I've read around quite a few other threads, and played around with the fstab settings, but little seems to make much difference!

Currently my settings are:

/dev/hdb5 /media/windows vfat  iocharset=utf8,exec,umask=000  0    0

Thanks in advance

---

### Post by kidders on 2006-09-12
OpenOffice is intended to be platform independent, so you have to be careful sometimes about what you ask it to do. If you ask it to save to a funny URL (like one that starts with "media://"), that only Gnome or KDE understand, it will fail. Browse to your disk's mount point and save your stuff there.

Incidentally, about your /etc/fstab... are you certain a umask of "000" is what you want? It allows *any* user to modify/delete/read everything on the entire disk by default! Also, to maintain compatibility with windows, you should be using a Microsoft character set, rather than UTF, strictly speaking.

---

### Post by coffeecat on 2006-09-12
I've just created an OO Writer file and saved it to a mounted vfat partition. No error, so I should imagine it is your fstab line that is the problem.

This is my fstab line:

```
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=000  0    1
```


Suggest you adapt to your mountpoint and see how it goes.

And in reply to kidders, I've found that umask=000 works fine, so long as you are the only user! :) It seems to avoid problems in a multiboot for reasons I've never worked out.

---

### Post by kidders on 2006-09-12
Hi guys,

Both your fstabs are effectively the same, but coffeecat should really switch the "1" at the end of his quoted line for a zero or a two, so things behave as expected in the event of root filesystem corruptions. If andyb does like you do and navigates to the FAT filesystem's mount point, things will come alive for him too :-)

With regard to umasks, if you're the only user on your PC, then there's no reason to be concerned. If not however, you need to rethink your security strategy! Linux won't protect your files from hackers/other users if you explicitly instruct it not to.

Hope that helps.

---

### Post by andyb.uk on 2006-09-12
Thanks for all the responses!

I've managed to get it working so that I can save files to /media/windows from OO.  It's a bit of a nuisance, as you need to navigate there from the address bar at the top of the save as dialogue (I was trying to do it via "Storage Media" before, which doesn't work).

Is there any way of putting a shortcut to the FAT disk into the dialogue- or of setting a default "save" location?  I've had a good root around through the OO settings, but nothing doing.  Obviously this method works, but can I train my daughter to do this?

Kidders- you said that there may be a problem with certain URLs.  My fstab line now reads: "/dev/hdb5 /media/windows     vfat    defaults,utf8,umask=000  0    0"  is there some better way of achieving access?  I'm the only user, so I'm quite happy with umask=000 (I think!)

Coffeecat- I tried to use /dev/hdb5 /media/hdb5 in the fstab, but the drive then failed to mount.  Was that what you were suggesting I did?

Thanks again for your help/patience.  I only just about understand what I'm doing here!

---

### Post by coffeecat on 2006-09-12
> **kidders said:**
> Both your fstabs are effectively the same

Except that mine lets OOWriter save a file to a vfat partition. :wink:

> **kidders said:**
> coffeecat should really switch the "1" at the end of his quoted line for a zero or a two, so things behave as expected in the event of root filesystem corruptions.

Maybe, but here's the fstab line that the Ubuntu installer automagically set up for me:

```
# /dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46  0    1
``` 
I've commented it out so that I could experiment with the other version. You'll see that the Ubuntu devs seem to prefer a 1 in the last field. Who am I to argue with the Ubuntu devs? :wink: I removed the gid=46 (plugdev group) and changed the umask value because I'm multibooting with Fedora 5 and SuSE (and Windows :().

> **kidders said:**
> With regard to umasks, if you're the only user on your PC, then there's no reason to be concerned. If not however, you need to rethink your security strategy! Linux won't protect your files from hackers/other users if you explicitly instruct it not to.

I live alone and any cracker (not hacker :shock:) who manages to break through my router firewall, NAT and Ubuntu firewall/IPtables deserves to be able to read my extremely boring personal files. :)

---

### Post by coffeecat on 2006-09-12
> **andyb.uk said:**
> Coffeecat- I tried to use /dev/hdb5 /media/hdb5 in the fstab, but the drive then failed to mount.  Was that what you were suggesting I did?

No, because I did say to adapt to your mountpoint, so what you need for the first two fields is what is in your original line, namely:

/dev/hdb5  /media/windows

Probably the best way of making a shortcut to the vfat partition is to have a symlink folder in your home partition. A symlink is the Linux version (more or less) of a Windows shortcut. OO will see it as a folder through which you can navigate in the ordinary way.

Creating a symlink via the terminal is fairly easy, but less so in a GUI in this situation because your mount point will be owned by root and you'll run into permission problems. Post back if you need help.

**Edit:**Ok. A quick experiment to see if it works, and here's one way of doing it. Open a terminal and do:

```
sudo ln -s /media/windows
```

A symlink folder will appear in your home folder, named 'windows'. You can right click on it to rename it if you want even though it is owned by root. Bizarrely, anything owned by root in your home folder you can delete, rename or whatever. If you now open OO and 'save as', you'll find the symlink folder appears as an ordinary folder in your home and you can save in it.

I've set up a more elegant (but much more of a fiddle to set up) version in one of my multiboots. I have the folders 'Documents', 'Pictures', and so on in the shared data partition, with symlinks 'Documents', 'Pictures', etc to them in home. It all works transparently as though I am navigating through folders in home.

---

### Post by andyb.uk on 2006-09-12
Brilliant!  All working happily now.  Thanks again for your help.  All I need to do now is find the best format for saving OO docs for reading in windows (the default isn't readable.  I'll have a play (guess that's OT anyway)

---

### Post by coffeecat on 2006-09-12
If you mean reading in MS Office/Word under Windows, then .doc (MS Word) or .rtf (Rich Text Format) will do the trick. You can set your default file save type in Tools > Options > Load/Save in OO if you need to exchange files with people using other word processors.

---

### Post by andyb.uk on 2006-09-12
Thanks Coffeecat- that works!!

---

### Post by kidders on 2006-09-12
```
Kidders- you said that there may be a problem with certain URLs. My fstab line now reads: "/dev/hdb5 /media/windows vfat defaults,utf8,umask=000 0 0" is there some better way of achieving access?
```

/etc/fstab entries have no effect whatsoever on OpenOffice's behaviour with regard to the media:/ protocol (not to be confused with the /media/ directory.) I was referring here to URLs that start media:/ ... OpenOffice doesn't like them.

Glad to see you've solved your problem :-)

---

### Post by DougS on 2006-12-26
Thanks for this very useful thread which (now I see it, of course!) has allowed me to save files to FAT32 Data partition which I want to be acessible from both Kubuntu and Windows
This means I can use either system and gradually learn more about Linux with a view to reudcing dependance on Windows.

INVALUABLE!

Doug S

---

### Post by DougS on 2006-12-26
Hold the bus...

I can now save files to the Data partition either in Konqueror or OO Writer but...

When I go to Windows Explorer, there don't seem to be any files there!

Any ideas:

Does the utf entry make any difference as I  have 
/dev/hda4 /media/Data vfat user,fmask=0111,dmask=0000 0 0

I don't understand the fine details of this so please be gentle!
I am so keen to get a dual system up and running so that I can access and write to a Data partition using either OS.

Thanks in advance...

Doug (again)

---

### Post by DougS on 2006-12-26
Oh and if I save files to the partition using Windows hey CAN be seen and edited in OO under Kubuntu.

Doug

---

### Post by DougS on 2006-12-26
Solved my own thread ;-)

Create symlink in /home (as above) must have saved original docs into wrong place
Once this done can create new folders and files accessible under both systems (I hope)

I'll probably be back...

---

### Post by DougS on 2007-02-06
I AM back, with the same problem.
I thought it was OK but I have since installed Gnome and XFCE with a view to having them co-exist to make up my mind which one to use.
I can now no longer save or delete fiels to my Data folder on FAT 32 which is accessible, readable, writeable by Windows.

I can read the files but not save them in Open Office.org.


I THINK I have:
FAT 32 partition
Mounts correctly via media/Data (case is correct)
Symlink in home folder (shearer)
I am not the owner of any files and therefore don't have the permissions.
my fstab line is currently:

/dev/hda4 /media/Data vfat user,fmask=0111,dmask=0000 0 0


but I have seen MANY combinations, most of which I just don't understand.

Should I just try to re-install Dapper and start again (tried the good looking Edgy on another HDD but it has the slow scrolling problem)or is there any mileage left in trying a detailed review (which I think I've come to the end of my tether on.
I really want this to work.
Any advice appreciated

---

### Post by kidders on 2007-02-06
> **DougS said:**
> I am not the owner of any files and therefore don't have the permissions.That's probably why you can't write to your FAT filesystem.

> **DougS said:**
> I have seen MANY combinations, most of which I just don't understand.The best thing to do is learn about mount options. In particular, take a look at "uid" and "gid".

> **DougS said:**
> Should I just try to re-install DapperDefinitely not! Your problem is extremely minor and probably wouldn't be reversed by a reinstallation anyway.

You might like to post the output of **mount** and some directory listings, so we can see what's what, and give you some pointers. The best advice is to learn a little about how filesystem mounts work though.

---

### Post by DougS on 2007-02-07
Output of mount, which I barely understand:

shearer@shearer-desktop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/hda4 on /media/Data type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000                                                    )
shearer@shearer-desktop:~$

Does this give any clues?

I do want to learn/understand thi, but if I can just get it to work I could then use either system and tranfer at will.

Thanks again in anticipation...

Doug

---

### Post by DougS on 2007-02-07
OOOps...

Which directory listings would help and how to get?

---

### Post by kidders on 2007-02-07
> **DougS said:**
> /dev/hda4 on /media/Data type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000)> **DougS said:**
> Does this give any clues?

It eliminates a number of potential issues. :-) Basically, it shows that files in your FAT filesystem have r/w permissions forced on them, directories have r/w/x permissions, and everything is owned by root. Given the /etc/fstab extract you posted, that's exactly what I expected to see, and should tally with the permissions shown in directory listings, etc. This configuration is exceptionally insecure, but _*should*_ still work perfectly for you.

One final check you could perform is **touch /media/Data/something**, just to try creating a file. The command should produce no output, and you can delete the file it creates immediately.

The thing that confuses me is that, assuming the "touch" test is successful, you can in fact write to your FAT filesystem without restriction. To check further, you could try something like this...

Depending on your system configuration, run (often ALT+F2) a text editor (eg something like **gedit /media/Data/testfile**). Type a few characters and save. With any luck, you won't see any errors.

---

### Post by DougS on 2007-02-08
Further diagnostic information.

Seems to have come from nowhere but:

Under Ubuntu I can now APPARENTLY delete files in the Data folder.
The files still say "Not the owner, can't change permissions, Owner is root.
Permissions are _rw_rw_rw Or 600666 

I can also APPARENTLY create new folders and also create, save and reload Open Office files (NO, I don't know what has happened since my original post)

HOWEVER... when I go back to Windows, those deletions and creations do not exist and when I return to Ubuntu they also don't exist.

I'm sure this means something but of course, I don't know what!

---

### Post by kidders on 2007-02-08
Is the filesystem alright?

As well as checking the filesystem, it might be worth looking in your dmesg or system logs for any strange messages.

:confused:

---

### Post by DougS on 2007-02-15
Fixed (for good I hope)

Compared to first time (on low part of learning curve) simply:
Fdisk /MBR
Delete all linux partitions from Gparted and live CD
Reinstall Unbuntu
Adjust Grub to boot Windows first (for the moment!)
Adjust
Fstab with the same line as before
All of this speeded up by creating launcher with gksudo nautilus (Psychocats pages really helpful)

It all seems to work fine.

Thanks for the support.

---

