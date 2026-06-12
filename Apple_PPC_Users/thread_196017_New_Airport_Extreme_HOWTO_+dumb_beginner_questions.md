---
title: "New Airport Extreme HOWTO? +dumb beginner questions"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by maxmartin on 2006-06-13
So I'm a total Linux novice, posting this from an iBook G4 on which I installed dual-boot Ubuntu last night. I've currently got it plugged into the ethernet because (obviously) Airport wasn't working. I went to [this thread]("http://www.ubuntuforums.org/showthread.php?t=142727") and tried to follow the steps, but I'm having lots of problems with them. First off, many of the files it's dependent on have been removed from the locations listed in these steps. Also, in step 3 when I type "make", my output is this:

```
cc -std=c99 -O2 -fomit-frame-pointer -Wall -pedantic -D_BSD_SOURCE -DFWCUTTER_VERSION_=005   -c -o fwcutter.o fwcutter.c
make: cc: Command not found
make: *** [fwcutter.o] Error 127
```

So I was wondering if anybody could 1. help me with this problem I'm having with make and 2. make a new/revised list of steps with file locations that are up to date. I'd really appreciate somebody taking the time to help me/others in my position out.

also, some unrelated questions: I have an external hard drive that I use to store files, mostly my music. Will there be any way for me to access it through Ubuntu? Is the only way for me to share files to create a new partition compatible with both systems to swap files around? Again, any help is appreciated. Thanks!

---

### Post by ibookppc on 2006-06-13
Here is the howto I used to get the airport extreme working no my ibook (12" 1.33ghz); [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
And for the external drive I had one aswell in fat32 format. I just edited my /etc/fstab and added it in there. To edit it just do this in terminal
sudo nano -w /etc/fstab
I added these lines to it:
/dev/sda1       /media/hd       vfat    defaults
You would have to replace vfat with whatever yours is, but if its HFS I'm not sure if it will work. You can also put auto there and it will automatically detect it. Also yours might not be /dev/sda1 but I think most likely it should be. Once your done editing just hit ctrl+o and ctrl+x.
Now sudo mkdir /media/hd and sudo mount /media/hd
That should mount it in /media/hd. 
If you have any further questions feel free to ask, we are all here to help each other.

---

### Post by maxmartin on 2006-06-13
First off, thanks very much for the link. I'm now posting on my wireless. Whee!

As for the second bit - my device is listed in Disks Manager as /dev/sda with an Extended 2 filesystem, so I added this line to the file you listed in nano:

```
/dev/sda   /media/hd   ext2   defaults
```

And this is the reaction I get when I type sudo mount /media/hd:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

thanks for the help so far.

---

### Post by ibookppc on 2006-06-13
I don't know why it would say bad file type try using "auto" for fs type.

---

### Post by maxmartin on 2006-06-13
No such luck; if I make the type auto it responds with:

```
mount: you must specify the filesystem type
```

---

### Post by ibookppc on 2006-06-14
Hmm. I don't know what it could be. Try the drive on mac osx and see what happens, check to see if it is not corrupt. If you have enough space just copy over the files onto the hard drive of the computer than reformat it to like fat32 and than copy them back over.

---

### Post by detour on 2006-06-14
I just did this today using the instructions in the wiki: [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

No need for fwcutter just install the experimental firmware package provided.

Good luck.

---

### Post by maxmartin on 2006-06-16
The drive is fine, and I definitely don't have nearly enough room to backup and reformat. I'd really appreciate any help on this - all of my music is on this drive, and if I can't get it working in Ubuntu it's going to be a major pain in the ***.

---

