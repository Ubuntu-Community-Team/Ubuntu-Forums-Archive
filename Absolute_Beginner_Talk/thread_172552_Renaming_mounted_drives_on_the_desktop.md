---
title: "Renaming mounted drives on the desktop"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-05-08
Good day to all...

I come before you with another question. 

Before I dist-upgraded to Dapper, my mounted drives were named hda, hdb, etc. Now they read drive, drive (2), etc....when I try to right click and rename them, the option is greyed out...

Is there any way to remane them? Thanks for your advice and any input on this...

---

### Post by djsroknrol on 2006-05-09
Sorry...I realized that my fstab might be of some insight to my problem:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdb1       /media/hdb1     vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdc1       /media/hdc1     vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

as you can see, it's still hda1, hda2, etc, but it shows up as drive, drive (2), and drive(3)...any ideas??

---

### Post by djsroknrol on 2006-05-09
Sorry for the bump, but I'm sure someone has an answer for this...



file:///home/bob/Desktop/Screenshot.png

I hope this .png comes thru...I've never tried to attached a screenshot in the forums before...

---

### Post by ComplexNumber on 2006-05-09
>  I hope this .png comes thru...I've never tried to attached a screenshot in the forums before... it didn't. just above the textbox when you enter what you have to say, you will see bold, italic, underline, etc. follow them along until you come to "Insert Image". press that, then copy the image URL into the popup dialogue box.

> 

as you can see, it's still hda1, hda2, etc, but it shows up as drive, drive (2), and drive(3)...any ideas?? where exactly do they show as drive, drive 2 etc?

---

### Post by djsroknrol on 2006-05-10
sorry...tried to do it...on the desktop...like so (Hopefully)...
[IMG]/home/bob/Screenshot-1.png[/IMG]
as you can see, Natutilus shows drive, etc, but opened volumes show hda, hdb, and so on...

---

### Post by djsroknrol on 2006-05-10
sure wish I gould get this screenshot up..it's in my home folder..doesn't work??...anyway, the fstab shows hda, and so on, but the desktop has the mounted drives shown as drive, drive (2), and drive(3)...can't figure it out...any other ideas?

---

### Post by djsroknrol on 2006-05-10
so sorry...lets try this one more time...
[IMG]http://file:///home/bob/Screenshot-1.png[/IMG]

---

### Post by joshrobinson on 2006-05-10
[QUOTE=djsroknrol]so sorry...lets try this one more time...
[IMG]http://file:///home/bob/Screenshot-1.png[/IMG][/QUOTE]


you cant do it that way, it wont run from your hard-drive.. click reply or new post and then scroll down past where you type and you see additional options

click manage attachments, then browse for the image in the top where it says upload file from your computer, then click the upload button.. type your reply then submit the reply

im also looking for an answer to this, my one drive on my desktop is called 20 gig volume or something along those lines on my other computer.. then some are named by the folder they are mounted at in /media.. such as music movies etc etc

---

### Post by joshrobinson on 2006-05-10
hmm i found this link how to do it to fat32 drives, wont work for ntfs.. but you can rename fat32 and ntfs in windows and i think that name should show up.. at least thats how my desktop is, since i named them in windows on another computer in the house so i didnt have to use my computers cpu and hdd time and could leave it copying files overnight (300 gig of data takes a bit)


[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/]("http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/")

---

### Post by ComplexNumber on 2006-05-10
i forgot to say that the URL in Insert Image only works if its on the net (eg your own server or somewhere else on the net). you have to use the 'Manage Attachments'. go to advanced -> Manager Attachments -> upload image.

---

### Post by djsroknrol on 2006-05-10
ok..that finally works. thanks for the help(never noticed that attachment button up till now)...as you can now  :)....the fstab has always worked up till the point that I upgraded to dapper...any takers?

---

### Post by djsroknrol on 2006-05-11
For the record, I solved this one. It had everything to do with my dual boot...Because I label all my drives the same in M$. (Windows Explorer letters them automatically).....joshrobinson got me snooping in windows, and decided to change a drive lable in the drives properties, and when I came back to Gnome there it was !! Who would have thought that there was that much intergration going on between the two OS's ??

Thanks for looking anyway...

](*,)

---

### Post by danjordy on 2006-06-08
Besides changing the name in XP, is there a way to change it in Ubuntu itself?

---

