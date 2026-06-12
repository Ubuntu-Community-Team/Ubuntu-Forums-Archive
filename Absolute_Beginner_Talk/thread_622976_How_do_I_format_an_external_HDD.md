---
title: "How do I format an external HDD"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-11-25
Hi,
    I have a laptop drive in an usb external case currently formatted in NTFS.  How do I format it with ext3 format?  Fat32 format?  Can this be done from within Ubuntu, or do I have to do if from a liveCD or gparted CD?  

I am comfortable with command line instructions and using the terminal.  Thank you for any advice.

---

### Post by Taboo Mirage on 2007-11-25
First off, plug it in and execute this:

```
mount
```

That will give you the device names of mounted drives, as well as locations.  You'll see the drive mounted somewhere like /media/usb.  Next to that you'll see its device name.  Assuming it was /dev/sdb we'd then do this:

```

su
umount /dev/sdb
mkfs -t ext3 /dev/sdb
eject /dev/sdb
```

Remove the drive, then plug it in again for it to be re-mounted.  There you go, a new EXT3 filesystem.

The -t switch of the mkfs utility specifies the type of filesystem you wish for it to be formatted in.

---

### Post by ijason on 2007-11-25
should be easy to do from within ubuntu. if you've installed gparted (available in the Synaptic) you just choose the drive from the pull-down menu on the right side of the partition manager screen. select the drive and it will show a list of the partitions on it.

i like to delete the old partition, then close the partition editor and then reopen it to put on the ext3 partition. i'm sure it's not needed, but i feel like it works better. you'll want to have the external drive unmounted at the time.

:)

---

### Post by neotasic1 on 2007-11-25
Thanks guys, I will try it both ways for the practise.  I take it I should use sudo rather than su?  And if I want FAT32 I use fat32 as the switch rather than  ext3? Thanks again for your time.

---

### Post by Taboo Mirage on 2007-11-25
"su" is just a method of obtaining root rights for the commands you're about to execute until you issue the "exit" command to drop back to a normal user shell.  I used it there as it is more efficient than typing "sudo" before each command in this case.  You just have to remember to type "exit" or close the terminal after you're finished issuing root commands, otherwise you may be executing commands with privileges that they needn't have and thus going against the principle of LUA.  

Another thing, you may wish to check out the command line utility called "cfdisk" if you're interested in learning about partitioning devices using command line tools also.  This, again, will require root permissions so use this to invoke it:

```
sudo cfdisk
```

Take care and good luck.  Oh, and yes "fat32" would be the switch you're looking for if you want a fat32 filesystem.

---

### Post by neotasic1 on 2007-11-25
> **Taboo Mirage said:**
> "su" is just a method of obtaining root rights for the commands you're about to execute until you issue the "exit" command to drop back to a normal user shell.  I used it there as it is more efficient than typing "sudo" before each command in this case.  You just have to remember to type "exit" or close the terminal after you're finished issuing root commands, otherwise you may be executing commands with privileges that they needn't have and thus going against the principle of LUA.  

Another thing, you may wish to check out the command line utility called "cfdisk" if you're interested in learning about partitioning devices using command line tools also.  This, again, will require root permissions so use this to invoke it:

```
sudo cfdisk
```

Take care and good luck.

Cool - thanks - trying it your way first as I type this. 

BTW my understanding in the Ubuntu world was that sudo invoked superuser privileges for about 15 minutes after password entry so I only would need to invoke it once anyway - is this understanding incorrect?

---

### Post by Taboo Mirage on 2007-11-25
Slightly incorrect.  Take this example:

```
sudo vi /etc/apt/sources.list
```

This would open that document in the vi text editor with superuser permissions.  It would prompt you for a password before allowing you root access to that file.  Now, if you exited that and then issued this on the next line:

```
sudo vi /etc/fstab
```

That would open that file up as root user without asking you for a password beforehand as it would already recognize the first time that you entered it.  

Now, if you then did this again straight after:

```
vi /etc/apt/sources.list
```

Despite being within the grace period, it would **not** open that file as a root user.  Why?  Because it lacks the "sudo" in front of it.  That must be explicitly included within the command for you to gain root permissions; it grants root access on a per-command basis.  What you are describing relates only as to whether it prompts you for a password or not.

---

### Post by neotasic1 on 2007-11-25
> **Taboo Mirage said:**
> Slightly incorrect.  Take this example:

```
sudo vi /etc/apt/sources.list
```

This would open that document in the vi text editor with superuser permissions.  It would prompt you for a password before allowing you root access to that file.  Now, if you exited that and then issued this on the next line:

```
sudo vi /etc/fstab
```

That would open that file up as root user without asking you for a password beforehand as it would already recognize the first time that you entered it.  

Now, if you then did this again straight after:

```
vi /etc/apt/sources.list
```

Despite being within the grace period, it would **not** open that file was a root user.  Why?  Because it lacks the "sudo" in front of it.  That must be explicitly included within the command for you to gain root permissions.  What you are describing relates only as to whether it prompts you for a password or not.

Great - thanks for the excellent explanation.

---

