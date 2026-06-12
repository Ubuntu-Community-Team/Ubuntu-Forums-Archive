---
title: "Second disk question"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by ah pook on 2008-02-22
ok- I have Ubuntu Hardy Heron running nicely on my 120 gig hdb. I have a second disk, sda, which is an 80 gig SATA drive. I'd like to use the sda drive transparently like i can in Windows, ugh, meaing when I boot up, the drive is just another place to store files. Right now, it's used for whatever OS I feel like playing with, but I'm gonna stick with Ubunutu, so I'd like to use this to store movies, music, whatever. But it's not part of the current system. I can see it, but everything requires root privledges
to access. How do I wipe the disk and make it just and extension of the filesystem?

sorry if this is a dumb question..

---

### Post by kaginken on 2008-02-22
You can fdisk it.  Format it to ext3 and put all your data on there.

If there is data there you want to keep, just put it somewhere else until you've reformatted, then copy it back.

Hope that helps!

---

### Post by Presto123 on 2008-02-22
Well...If you have any files that you really want to keep, be sure to back it up. And with the following program, you will need to make sure that you are formatting the CORRECT drive.

```
sudo apt-get install gparted
```

Format that HD into FAT32 or "Vfat", whichever it shows and that will be available to both NTFS systems as well as Linux systems. Just know that this will actually create a second disk that will show up on your desktop.

---

### Post by ah pook on 2008-02-22
no, there's nothing there I want to keep. Right now, it's got some gentoo distro on it, so i don't mind wiping it out. So I should format it to ext3, right?

---

### Post by kaginken on 2008-02-22
Yea, I'd recommend ext3 as you sounded like you want to be primarily ubuntu now...

You could also format it using FAT so windows could read/write it also - but that's not the best filesystem for linux.  Also, there's a windows utility you can install now that gives it full read/write to ext3 anyway  ( [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) )

God speed!

---

