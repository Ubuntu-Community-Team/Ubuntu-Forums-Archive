---
title: "Where is &quot;/&quot;?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by paker on 2007-02-19
I downloaded a bunch of .zip files to desktop. When I clicked on the file, it got unzipped and individual files were created at "/" Since I need a Windows program to view and print the files, I need to save them on a CD. But where can I find the unzipped files? Thanks.

---

### Post by 23meg on 2007-02-20
It's the topmost directory in your filesystem, which contains all the other directories.

---

### Post by paker on 2007-02-20
Thank you. Please help me locate the files. I checked File System. It had a whole bunch of folders, including bin, home, boot, lib, etc,.... But I cannot locate the unzipped files. When I click on a zip file, it takes me to "/" and I see several folders. Should I archive these first?

I downloaded 25 zip files. I selected all 25  and clicked on them. Each zip file created about 10 folders and each folder several files. I want to be able to save them all on a cd or dvd. I just cannot find them.

---

### Post by Maestro23 on 2007-02-20
Are you sure they went to "/"?

Open a terminal:

cd /

ls

Do you see the folders?  IF not...

cd /home/username/Desktop

ls

What do you see?

---

### Post by jellystones on 2007-02-20
Your question makes no sense.

First of all, how do you know how many files and folders each zip file created if you don't know where the folders and files are.

Also, why not just unzip the zip files again, and this time make sure you know where you are unzipping them to.

---

### Post by aysiu on 2007-02-20
In your file browser, press Control-L and type ```
/
``` and press Enter. That's what / is.

---

### Post by tonyr1988 on 2007-02-20
If you're coming from Windows, you can also view / as the Ubuntu equivalent to C:/ (sort of, it's not exact - but close enough :))

---

### Post by aysiu on 2007-02-20
> **tonyr1988 said:**
> If you're coming from Windows, you can also view / as the Ubuntu equivalent to C:/ (sort of, it's not exact - but close enough :))
It's pretty close.

C:\
/

C:\Documents and Settings
/home

C:\Documents and Settings\*username*
/home/*username*

C:\Documents and Settings\*username*\Application Data\Mozilla\Firefox
/home/*username*/.mozilla/firefox

---

### Post by tonyr1988 on 2007-02-20
> **aysiu said:**
> It's pretty close.

C:\
/

C:\Documents and Settings
/home

C:\Documents and Settings\*username*
/home/*username*

C:\Documents and Settings\*username*\Application Data\Mozilla\Firefox
/home/*username*/.mozilla/firefox
Very informative and extensive (like always, aysiu! :D).

Just to throw one more thing out there:

The biggest difference (that I know of) between / and C:/ is that C:/ just represents one partition of one hard drive. There is a separate "upper level directory" for each separate partition of each storage device. In Linux, everything that is mounted (all partitions, all hard drives, all thumb drives, all iPods, all CDs and DVDs, all floppy disks, etc.) is located somewhere in /

It's slightly overwhelming, but *amazingly* convenient.

---

### Post by aysiu on 2007-02-20
Just to illustrate a bit what you're talking about:

C:\
/

D:\
/media/hda2

E:\
/media/hdb1

F:\
/media/hdb2

---

### Post by paker on 2007-02-20
Thanks for the explanation. I think this is what's happening, but if I am wrong, please correct me.

I downloaded a zip file and clicked on it. It got unzipped and several folders were created in "/" Here is the screen shot:



I had to EXTRACT in order to save the unzipped folders. After I did on all the zip files, I put all   EXTRACTed folders/files on a blank CD and burned them. I found it to be more intuitive than installing WinZip, and working with WinZip interface.

---

### Post by Tomosaur on 2007-02-20
There's no way they got extracted to / unless you were running as root - which you shouldn't be!

Go to a command line and type:
```

ls /

```
Then paste the output here please.

---

### Post by paker on 2007-02-20
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old


Above is what I got from $ ls /.
Please interpret what I did for me.:)

When I click on the zip file, a new window pops up with the zip file name in the colored bar: "tch-nwca.zip" And another bar with a house icon: "Location /" I wish I knew how to post screen shot.

---

### Post by Tomosaur on 2007-02-20
Alright, it looks fine - you didn't extract anything into the / directory.

The files have probably been extracted into your home directory. To check, just click Places (on the top panel), then click Home Folder. The files should (hopefully!) be there.

---

