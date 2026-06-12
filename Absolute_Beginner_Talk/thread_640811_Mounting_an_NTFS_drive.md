---
title: "Mounting an NTFS drive"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-14
I'd like to Mount my NTFS slave drive that I had on my Windows Installation.
Currently I'm not duel booting or anything, I just need to mount my slave
drive that has all my Photos on it. Also, Will I be able to write to it?
I heard that Gusty supports writing to NTFS by default, is this true
and is that dangerous?

I remember Years ago when I tried linux for the 1st time ( RedHat 8 ) I had to 
type out this long command string into the terminal or type the long command 
string into the fstab file to hold the setting and it would be ready and mounted
for me at boot. 

Does Ubuntu work the same way, or do I just plug it in and then boot up?
If I do have to type a command will I need to add some sort of permission?
Linux has gotten much easier since then so I am not familiar with the new
mounting features. I remember I had to type something like this back in
the day

mount -t fstype [-o optiond ] datasource mountpoint

```
mount NTFS /dev/hdb1  /MyDrive
```

If I recall correctly I put this in my fstab
I can't remember what permission those are its been so long
```
mount /dev/hdb1 /MyDrive ntfs  ro,umask=0222 0 0
```

---

### Post by LaRoza on 2007-12-14
Ubuntu 7.10 Gutsy Gibbon will read and write to it with no problem.

You will have to mount it, double click it in Places->Computer.

You won't have to use the terminal.

To make things easier, you can add it to fstab, but you don't have to.

How to fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by forestpixie on 2007-12-14
does this help - apart from the ntfs3g bit at the start, believe also gutsy has the support built in - didn't seem dangerous when I used ntfs3g with feisty - can't verify gutsy as ntfs all gone

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-3c27b1fe906b037b438cebcdcdb702d0afa5bd3d](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-3c27b1fe906b037b438cebcdcdb702d0afa5bd3d)

---

### Post by Orbital75 on 2007-12-14
Thanks guys......  Is that Mounting string correct or is there an easier string to mount
a drive.....  I honestly can't remember all this stuff so more than likely you guys will
have to tell me what to type in the command prompt..... thanks

---

### Post by cszikszoy on 2007-12-14
go to synaptic and search "pysdm"

Once installed it'll show up under system > administration > Storage Device Manager.

Use this for any of your mounting needs.  If you tell it to mount a drive (say your windows drive) it'll automatically reconnect at the next startup too.

---

