---
title: "Udf &amp; Dvd Ram"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-03-27
Hi,

I have an LG CD/DVD burner that worked fine with Ubuntu.

Anyway, I installed udftools so that I could make UDF DVD-RAM's through Ubuntu, I could already use those created from XP with InCd.

Since formating the DVD-RAM and formatting with mkudffs, the DVD mounts as Linux_UDF, however, I cannot drag files to it as all of the permissions are root and the device lists as /media/dvdrecorder.

How can I change this, I read about updating the fstab file, but the device is already there under:

/dev/hda /media/cdrom

Like wise when I try to edit fstab I cannot save the file.

---

### Post by jhenager on 2007-03-27
When you are editing fstab, are you starting your editor with 'sudo'?

---

### Post by ushills on 2007-03-27
No, should have remembered that :oops: :oops: 

Does it matter is the drive is already mounted using cdrom0.

The drive mounts but I cannot write to it.

---

### Post by ushills on 2007-03-28
I have formatted a disc with udftools and it mounts to my desktop, I have a "lost+found" folder on the disc but I cannot delete it or copy new files to the DVD.

The permissions show as group user, but still the main permission is route.

Can someone please point me in the direction of a walkthough to format a DVD-Ram as UDF and use it with Ubuntu please.  Discs formatted using XP with InCd work fine so I assume that it is a permission issue when using udftools.

Thanks
Ian

---

### Post by mnomoto on 2007-04-01
Can you write to discs formated on windows?

I tried to write to a DVD-Ram, but all I got were write errors. My disc was formated on windows with a Toshiba app. It mounts, but I cannot write to it. Do someone know what I'm doing wrong? On windows the disc works fine.

---

### Post by junkonina on 2007-05-25
Re: dvd-ram formating and permissions.

sudo -i
mkudffs /dev/scd0

This will create the udf structure. You will then find a new directory /media/LinuxUDF with root as the owner.  You have to change the owner of this folder. You can't change the owner of /dev/scd0.

sudo chown username:username /media/LinuxUDF

If you want to use the gui,

sudo thunar /media/LinuxUDF

This will open a file browser window with the red root caution bar. Go to the /media/LinuxUDF folder, right click, and change the permissions. 

One strange thing I have found is that if you delete a file from a udf dvdram you can't unmount or eject it.  It just says busy.  If you restart it is okay. ?????????

---

### Post by junkonina on 2007-05-25
opps! the above post is on Xubuntu

[U]If you want to use the gui,

sudo thunar /media/LinuxUDF

This will open a file browser window with the red root caution bar. Go to the /media/LinuxUDF folder, right click, and change the permissions.[/U]

For other versions use the name of your file browser instead of thunar.

---

