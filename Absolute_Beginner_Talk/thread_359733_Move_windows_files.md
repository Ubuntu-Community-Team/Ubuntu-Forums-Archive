---
title: "Move windows files"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by EmergencyMan on 2007-02-12
I'm trying to use ubuntu to move some files to my external HD, but run into difficulty.  I managed to screw up my windows system and don't seem to be able to repair it or boot it.  There are still important files on the hard drive that I would like to move.  However, they seem to be invisible to ubuntu.  I did get to them the other night and actually thought I could move them.  However, I got an error message saying that the files on my 120 mB hard drive (probably about 60 mB) was too large for the destination drive (apx 200 mB free) and gave a figure for the files I was transfering at 400+ mB.  As the night wore on, it increased the size to 100,000 mB!  

What I want to find out is:
1.   How can I access these files easily?
2.   How can I move them to the external drive?

TIA for any help.  As you can see, I'm a real Linux novice, only having played with ubuntu on and off for a couple of months.

---

### Post by taurus on 2007-02-12
You first need to mount it before you can access it.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Try running "gksudo nautilus" from a terminal.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by Darkspace on 2007-02-12
Someone else will have to supply the commands (edit: see above) but I'd:

1. Mount the Windows partition (maybe you already did this).
2. Copy the files to an external drive/memory key/sd card or burn a CD.

What happens when you try booting Windows? Just in case we can fix that.

---

### Post by EmergencyMan on 2007-02-12
Thanks, I'll get on it.  I've got a lot to learn!

---

### Post by EmergencyMan on 2007-02-12
the search shows:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4865    39078081    c  W95 FAT32 (LBA)
/dev/hda2           13318       14592    10241437+   c  W95 FAT32 (LBA)
/dev/hda3           14593       14593        8032+  1e  Hidden W95 FAT16 (LBA)
/dev/hda4            4866       13317    67890690    5  Extended
/dev/hda5   *        4866       12970    65103381   83  Linux
/dev/hda6           12971       13317     2787246   82  Linux swap / Solaris

The info I'm looking for is on that firs partition, I believe, but I have enough space on the external to copy them all.  Now what?  How do I actually get to those files to copy them?

---

### Post by taurus on 2007-02-12
Have you mounted both /dev/hda1 and your external drives?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by EmergencyMan on 2007-02-12
Windows says that it can't boot.  My plan is to wipe the drive and start over, but I want my PasswordSafe and PowerPoint presintations, which I hadn't backed up  I don't have any other way to repair windows.  Nice to be learning a way around Microsoft, though.:confused:

---

### Post by EmergencyMan on 2007-02-12
I feel like I'm getting more dense all the time.  Below is the results of that one.  Now I have to take my wife to work, be back in ten.

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.3G  668M  66% /
tmpfs                 506M  4.0K  506M   1% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
tmpfs                 506M   72K  506M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev
/dev/sdc1             234G   40G  195G  17% /media/FAT32

---

### Post by taurus on 2007-02-12
Looks like the external drive is mounted, /media/FAT32.  Now, you just need to mount /dev/hda1 so you can transfer stuff from /dev/hda1 to /dev/sdc1.

```
sudo mkdir /media/hda1
sudo mount -t vfat /dev/hda1 /media/hda1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by EmergencyMan on 2007-02-12
And it suddly appears!  Many thanks.  Now I'll try to move it.

---

### Post by EmergencyMan on 2007-02-12
Well, now it's saying that the folder I am moving (Documunts & Settings) is too big,  Since it's a 250 gig, mostly free, I don't really understand the error message.  Is there something else I am missing?

---

### Post by taurus on 2007-02-12
Is there any file in that folder larger than 4GB?  Fat32 can't handle anything larger than 4GB in size.

---

### Post by EmergencyMan on 2007-02-12
Checking

---

### Post by EmergencyMan on 2007-02-12
Yes, there are, and all are renamed in some format I don't understand, and even when I drag the small ones as individual files, either the tree disappears or I get an error message about parameters not being recognized.

---

