---
title: "[SOLVED] Insufficient space to make ISO...."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Langson on 2007-08-26
Hi.
I'm new here and new with Linux Ubuntu, so please try to bear with me....
I'm trying to transfer some .AVI files to DVD. I've got DeVeDe which I am trying to use to create the .ISO file. The first attempt went well, but since then I keep getting an insufficient space warning (i.e. only 1737mb available).
I know that I have plenty of space on the primary HDD.
I have no idea about what's happening here, or how to correct it.
Sorry if this has already been dealt with in depth in another thread, but as I don't really know what's happening, I'm not sure what to search for.
Thanks in advance,
Your Friend,
Langston.

---

### Post by Mud.Knee.Havoc on 2007-08-26
> **Langson said:**
> Hi.
I'm new here and new with Linux Ubuntu, so please try to bear with me....
I'm trying to transfer some .AVI files to DVD. I've got DeVeDe which I am trying to use to create the .ISO file. The first attempt went well, but since then I keep getting an insufficient space warning (i.e. only 1737mb available).
I know that I have plenty of space on the primary HDD.
I have no idea about what's happening here, or how to correct it.
Sorry if this has already been dealt with in depth in another thread, but as I don't really know what's happening, I'm not sure what to search for.
Thanks in advance,
Your Friend,
Langston.

How much space do you have on your HDD?  Do you have one single large partition for Ubuntu, or do you have separate partitions?

If you have multiple partitions, eg. one for Ubuntu's system files and another larger one for /home, you must tell it to create the .ISO (and put any temporary files) on the partition with tons of space.

1737MB is not a heck of a lot of empty space...

How about entering "df -h" (without the quotes) into a terminal and pasting the results here?

---

### Post by Dr Small on 2007-08-26
A faster, and simpler way to make an ISO of the livecd would be to run this command:
```

dd if=/dev/cdrom of=ubuntu-7.04-desktop-i386.iso
```

Dr Small

---

### Post by por100pre1 on 2007-08-26
Are you sure you have enough free space? A way to free up some space is to remove downloaded .deb files:

```
sudo aptitude clean
```

---

### Post by Langson on 2007-08-26
Thanks, peeps.

Here the results of the df -h command...

Filesystem            Size Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                       11G  2.5G  8.1G  24% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      1.9G  136M  1.7G   8% /home
/dev/sdb1             299G  113G  187G  38% /media/Secondar

---

### Post by Langson on 2007-08-26
> **Dr Small said:**
> A faster, and simpler way to make an ISO of the livecd would be to run this command:
```

dd if=/dev/cdrom of=ubuntu-7.04-desktop-i386.iso
```

Dr Small
OK. Maybe I'm thick, but you lost me there....

The files are '.avi'. Is this the same as 'livecd'?

---

### Post by vanadium on 2007-08-26
I won be able to help you directly as I am not familiar with DeVeDe, but I can give some insight into why you get this error. Insight is a good start to find a solution. You have 8.1 G on your / partition. That might be limited for DVD creation. A filled single layer DVD is 4.6 GBytes. The way DeVeDe works is: it transcodes your AVI to DVD compliant mpeg streams. Supposing the full DVD capacity is used, the mpeg file will take more than 4 GBytes. Then, the mpeg is authored to a video DVD stucture. The mpeg is muxed into DVD VOB files that live under a VIDEO_TS directory. Another 4 gigabytes. Finally, a video-DVD  image is created from the VIDEO_TS directory. Another 4 gigabytes. You have plenty of space on your partition hosting /home. However, DeVeDe probably uses the /tmp or the /usr/tmp directory for the temporary files (2 times 4 Gigabyte), and these will reside in your / partition. I am not familiar with DeVeDe, unfortunately, and loading it, I see that the only "option" is to delete temporary files . Hopefully someone familiar with DeVeDe can step in here..Alternatively, you could replace your /tmp and /var/tmp by symbolic links to directories on your largest partition, but that is for the system admin and beyond the scope of the absolute beginner.

---

### Post by Langson on 2007-08-26
Thanks, Vanadium.

Is there another DVD writer program that you could recommend? One that can handle .AVI files and, if possible, make 'photoDVDs' out of JPEGs?

---

### Post by Langson on 2007-08-27
Still not getting anywhere...

A bit more info about my set up...

I have a dual boot system. The 'original' Windows XP partition and a dual boot partition of Ubuntu set up via the Wubi installer thingy...

Having carried out the suggested 'sudo aptitude clean' command my df -h output now reads...

Filesystem            Size Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                       11G  2.4G  8.1G  23% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      1.9G  139M  1.7G   8% /home

Windows informs me that the 'C' drive has over 100GB free on it...

---

### Post by yogo on 2007-08-27
Do you have any memory cards?Try to create the iso on a memory card that has room and if you still get that error then the problem does not have to do with available space but I think it does.

---

### Post by Hospadar on 2007-08-27
well, you could look into mounting your larger drive to /usr/temp to give more space there, or cd to that drive and run devede from a command line there.  The mounting is a little difficult and probably not recommended.  Try just transcoding the videos with devede (don't write the iso, then move all the video files to to the larger drive, then use devede to make a dvd out of the transcoded files.

---

### Post by Langson on 2007-08-27
Thanks, Hospadar.
That works for the smaller AVIs, but the problem remains for the others...

---

### Post by Langson on 2007-08-27
> **yogo said:**
> Do you have any memory cards?Try to create the iso on a memory card that has room and if you still get that error then the problem does not have to do with available space but I think it does.
Thanks, Yogo.

I do have memory cards. The largest I have is a 2gb XD.

I don't know how to select the location for the ISO in DeVeDe.... (we talking absolute beginner here...)

---

### Post by yogo on 2007-08-27
I am not familiar with that program but it should be rather straight forward to save it to your sd. I have seen a few mention devede, I may jsut get it to see whats up.

---

### Post by yogo on 2007-08-27
Just from a quick glance at the program, my guess is that after you choose your files, the program asks you to choose a folder, if you have your sd card connected with a card reader etc at that time, choose an output folder there, that should do it for you, although I have never used devede.

---

### Post by Langson on 2007-08-28
Sorted.
Thanks Yogo and the others who've helped me in this matter...

Ah, yes. I had a feeling that I was overlooking something obvious, and I was. The annoying thing is, I must have used that option when I did my first project, but then forgot about it.

Well, I did say I was an absolute beginner, but I forgot to mention that I'm perfectly capable of missing answers that are right under my nose.

Your Friend,
Langston.

---

### Post by pizpot on 2008-01-29
You have to read what devede tells you when you pick the output folder: "do not choose a folder on a fat32 partition." That is the problem, fat32 can only hold files as big as 4GB whereas a dvd is over that.

---

