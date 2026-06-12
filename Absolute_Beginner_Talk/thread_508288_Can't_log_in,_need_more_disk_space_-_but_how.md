---
title: "Can't log in, need more disk space - but how?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Cereus on 2007-07-24
Hello,

I am running version 7.04, I booted up my computer this evening but I couldn't log in. I can't quite read the error message because it is too small but I could make out something about Ubuntu can't boot because it is out of disk space and to contact my administrator. That would be me and frankly I'm stuck.

I tried to log in with different options - I selected logging in with just terminal or something (I think they were safe modes of some sort which I could change at the login screen). I tried every option and every time it was the same error.

I believe I can solve my problem if I just log in and delete some files but I can't figure out how to do that.

I have a live CD of an older Ubuntu version that I can load and it is what I am using now. I can get to the terminal but I am ubuntu@ubuntu:~$
How can I look at what files are available on my hard drive so I can go in as root and delete something from my home directory?
I can't see my hard disk with the live CD that I have (version 6.10). The filesystem just shows whats on the CD and my hard drive just doesn't show up. How can I mount my hard drive and where can I find info about how to mount it?

Any information would be greatly appreciated because I would love to get back on to my computer.

Thanks,
Cereus

---

### Post by rajeev1204 on 2007-07-24
From your grub menu just select the recovery mode option which will log u in as root

Then delete a few unnecessary files and u should be able to reboot into regular mode

---

### Post by AceofSpades19 on 2007-07-24
you could also boot into a KNOPPIX livecd and delete some unecessary files as well

---

### Post by lert on 2007-07-24
If you have a livecd and your cdreader works well, then booting your computer with the livecd can help you manipulate your original hard disk. Remember the livecd system is also a linux system. Dir your /dev/ and find your harddisk devices, mounting them. Then you can delete some unnecessary files on your disk and login your harddisk system.
PS: login as a root is not good for ubuntu or other linux personal OS.

---

### Post by asmoore82 on 2007-07-24
Boot your actual system with no LiveCDs ...

when it asks for you to log in graphically press [Ctrl]+[Alt]+[F1]

now log in non-graphically and ...

**ls** is the command to **list** filenames
**cd** is the command to **change directories**
     cd with no directory name will take you back home.
and finally ...
**rm** is the command you need to _very_ carefully **remove** files from your system ...

Be forewarned: from the command line there is no "Trash" - which is also what makes the command line
the perfect solution to this situation! right? you need some files gone!

so at first just play around until you feel more comfortable ... 
```

~ $ ls
~ $ cd Desktop
Desktop $ ls
Desktop $ cd
~ $ ls
```
list files, change into 'Desktop' folder, list files, change back home, list the same files you started with.

... and then _very_ carefully ...
```
~ $ rm <some_old_file_you_really_dont_want>
```

When you are done type **exit** to logout of the console and press [Alt]+[F7] to return to your graphical system.

---

### Post by hyper_ch on 2007-07-24
if you have installed a few things, the .deb files will still be resident on your computer... you could also delete those:

```

sudo rm -Rf /var/cache/apt/archives/*

```

---

### Post by Cereus on 2007-07-24
Hello and thanks everyone for the suggestions.

It turns out that when I was selecting a new session (i.e. to use only terminal) you had to type your name and password in first (but not hit enter after the new password) and then select the session and then hit enter to your password. That logged me into terminal, I was able to remove some files and then I came to this page to check out the information. 

What I don't understand is that I still had some 20 gigs free space on the hard drive. Was it instead that I filled up my home folder to some set limit?

I really like Ubuntu but I think there is something here to be improved. I appreciate that ubuntu isn't windows but it is trying to be friendly and easy to use. It doesn't seem unusual to me that someone would fill up their disk, mine wasn't even full! 

1) can the system check that it has enough disk space when it turns off to confirm that it can turn on? If someone (say a windows user switcher like my mother) has no clue about terminal and wouldn't think about a live cd solving this the next time she boots up could be really difficult. A warning before logging off means you could fix the problem before it becomes one. I still had gigs of free space on my hard drive.

2) why could I not select what type of session I wanted and then log in? Why did I have to almost log in, then select session, then hit enter. That sequence of events doesn't seem obvious. If that is how it has to be, perhaps it should be posted as directions at the Select Session option. I thought it was obvious that I should select my session and then log in.

Thanks again for everyone's suggestions,
Cereus.

---

### Post by Mornedhel on 2007-07-24
This happens if your root partition is filled, not if your entire disk is filled. So you may very well have space remaining on, say, your MP3/video partition, but not your system partition.

Just for the record, I can select a different session at any point of the login procedure, not sure why you cannot.

---

### Post by rajeev1204 on 2007-07-25
> **Cereus said:**
> Hello and thanks everyone for the suggestions.

It turns out that when I was selecting a new session (i.e. to use only terminal) you had to type your name and password in first (but not hit enter after the new password) and then select the session and then hit enter to your password. That logged me into terminal, I was able to remove some files and then I came to this page to check out the information. 

What I don't understand is that I still had some 20 gigs free space on the hard drive. Was it instead that I filled up my home folder to some set limit?

I really like Ubuntu but I think there is something here to be improved. I appreciate that ubuntu isn't windows but it is trying to be friendly and easy to use. It doesn't seem unusual to me that someone would fill up their disk, mine wasn't even full! 

1) can the system check that it has enough disk space when it turns off to confirm that it can turn on? If someone (say a windows user switcher like my mother) has no clue about terminal and wouldn't think about a live cd solving this the next time she boots up could be really difficult. A warning before logging off means you could fix the problem before it becomes one. I still had gigs of free space on my hard drive.

2) why could I not select what type of session I wanted and then log in? Why did I have to almost log in, then select session, then hit enter. That sequence of events doesn't seem obvious. If that is how it has to be, perhaps it should be posted as directions at the Select Session option. I thought it was obvious that I should select my session and then log in.

Thanks again for everyone's suggestions,
Cereus.



The next version of ubuntu called gutsy is implementing this feature which will let u log in inspite of disk being full .


[https://wiki.ubuntu.com/BootLoginWithFullFilesystem](https://wiki.ubuntu.com/BootLoginWithFullFilesystem)

---

### Post by AceofSpades19 on 2007-07-25
I can change the session on my ubuntu box before I type my username

---

