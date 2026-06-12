---
title: "Dual Boot Guide for Powerbook G4"
date: 2007-06-12
forum: Apple PPC Users
---

### Post by czechman86 on 2007-06-12
Are there any guides on how to properly partition a Powerbook or any Apple computer for that matter, so that it is possible to run both OSX and Ubuntu. I have tried several times, but always run into the problem of "Not Enough Room For OSX New World Boot Partition."

If anyone has a guide or suggestions, here are my system specs:
G4 1.5 ghz
80 gig HD
768 memory
SuperDrive

Please note, I am living away from home, and have no externals or no other systems that I can run Ubuntu on. This is the only one. thanks for you help!

---

### Post by stmiller on 2007-06-12
Here's a quicky, but requires you freshly install everything. So backup all data first.

1. Put in OS X install disc, and at the beginning of the installer, click for the Disk Utility at the top menu bar. Navigate in the disk utility and create two partitions. Make the first HFS+ for OS X, and leave the second as raw, unformatted space. Make the sizes of each how you want them to be.

2. Install OS X as normal.

3. Put in the Ubuntu install disc, and run the Ubuntu installer. It will automagically (as of Feisty) install into the raw, free space. It does not want to wipe anything out. But if you want to double check, do a 'manual partition' option, and make sure it is set up in the latter partition on the drive.

4. Once Ubuntu is installed, you might have to edit the file /etc/yaboot.conf (as in the PPCFAQ wiki below) to put a line for booting to OS X, or other booting options.

That's it!

---

### Post by czechman86 on 2007-06-12
Thanks! I will give that a try after I move my docs over to DVD (oh how i miss my externals :( ). Ill post my results as soon as my experiment is done!

---

### Post by czechman86 on 2007-06-13
I have run into some problems, as the Live cd will not recognize my partitions. it says that all I have is raw unformatted space (74 gigs worth). OSX on the other hand, does recognize my partitions, one of 64 gigs (HFS+) and one unformatted free space of 10 gigs. How do I fix the problem with the live install to see the partitions? I have also checked in gnome partition manager, and it shows me the same thing of 74 unformatted gigs.

Thanks for the help!

Here is what my terminal says for the command df -h in linux:

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 378M  268K  378M   1% /lib/modules/2.6.20-15-powerpc/volatile
tmpfs                 378M  268K  378M   1% /lib/modules/2.6.20-15-powerpc/volatile
varrun                378M  104K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  112K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
tmpfs                 378M   12K  378M   1% /tmp
```

Here is what the same command in the OSX Terminal Shows:

```
Filesystem                Size   Used  Avail Capacity  Mounted on
/dev/disk0s3               64G   2.8G    61G     4%    /
devfs                      97K    97K     0B   100%    /dev
fdesc                     1.0K   1.0K     0B   100%    /dev
<volfs>                   512K   512K     0B   100%    /.vol
automount -nsl [123]        0B     0B     0B   100%    /Network
automount -fstab [128]      0B     0B     0B   100%    /automount/Servers
automount -static [128]     0B     0B     0B   100%    /automount/static
```

---

### Post by SycloneMedia on 2007-06-13
I have a guide I put out a few months back... I have a 1.25 15" AlBook. I had some of the same probs you did.

Read this thread, the guide's in it:
[http://ubuntuforums.org/showthread.php?t=406548](http://ubuntuforums.org/showthread.php?t=406548)

In case you run into some other trouble or questions about it, it's discussed more in this thread too:
[http://ubuntuforums.org/showthread.php?t=430679](http://ubuntuforums.org/showthread.php?t=430679)

Read through them both just so you're ready in case something comes up.

---

### Post by czechman86 on 2007-06-14
Thanks to both of you guys for your help! I am now pleased to say that I have a successful dual boot machine. It is like heaven, I can use osx for my Skype and Slingbox, and Linux for everything else!

---

