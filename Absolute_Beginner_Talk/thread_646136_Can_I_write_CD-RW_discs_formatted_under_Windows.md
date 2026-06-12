---
title: "Can I write CD-RW discs formatted under Windows?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by bw44 on 2007-12-20
I created some re-writable CDs under Windows XP using a utility called Roxio (before moving to Ubuntu).  When I insert them in the CD reader now they appear on my desktop, but in read-only mode.  Under XP I could re-use the whole CD by deleting files and writing new ones to it.  Can I somehow mount these CDs in read/write mode under Ubuntu?

Under Properties>Volume it says:```
Media: CD-RW Disc
File System: udf
Mount Point: /media/cdrom0
Mount Options:  ro nosuid nodev noexec
```

Can I use the the "Settings" on this tab to change it to read/write, and what options should I use? Or is there some other way?

Thanks.

---

### Post by nowshining on 2007-12-20
u can see what u can do under places -- > cd/dvd creator

i don't have any  cd-rw's to test, only cd-r's :P but that is the cd/dvd creator that came with nautilus (file browser)

add/remove or synaptic

i heard if i get the name right k3b is a good one that u might like and i think it is suppose to be like nero or something..

---

### Post by bw44 on 2007-12-21
> **nowshining said:**
> u can see what u can do under places -- > cd/dvd creator

i don't have any  cd-rw's to test, only cd-r's :P but that is the cd/dvd creator that came with nautilus (file browser)

add/remove or synaptic

i heard if i get the name right k3b is a good one that u might like and i think it is suppose to be like nero or something..Thanks a lot for your input. I may look at k3b, but I don't think it will solve my present problem.

cd/dvd creator is good for formatting and writing to blank discs, but what I want to do is access a CD-RW that was already created under Windows, and has files on it I would like to delete. Under XP I could access the CD like it was another hard disk, drag and drop, delete, rename files and so on.  But when the CD is mounted on Ubuntu, it's read-only, and I'm not allowed to change the permissions (or I should say I don't know how!)

Cheers.

---

### Post by insane_alien on 2007-12-21
try brasero. it is pretty much k3b for gnome

---

### Post by bw44 on 2007-12-21
> **insane_alien said:**
> try brasero. it is pretty much k3b for gnome
II installed brasero and it looks like a great program.  I don't do a lot of audio/video CD burning, but I might make it my default.

Unfortunately, brasero doesn't recognize the files on my Windows-created CD-RW disc (It says the CD is empty!)

Nautilus has no problem displaying the files and folders and allows me to read everything.  What I want to be able to do is manage things on the CD with Nautilus (or the command line) just like I would on my hard disk, floppy or SDram stick.

Glad to know about brasero, though.  Many thanks for that!

---

### Post by nowshining on 2007-12-21
u can search in synaptic with keywords like cdrw or something,

system - administration - synaptic package manager

again try there and see what u can find.

---

### Post by zvacet on 2007-12-21
Look better in k3b because it have** erase **and** format **options and that is what you are looking for.

---

### Post by CCNA_student on 2007-12-21
Try this command: *sudo mount -t iso9660 /dev/cdrom /media/cdrom* or
*sudo mount -t udf /dev/cdrom /media/cdrom*

Even if the terminal says that does not work it actually does. Just go into your file manager after running one or both of these commands to see if either worked. I have to use that command to get my Memorex 16x DVD-ROM drive to look at a disc other than a video DVD. To unmount the drive use the command: *sudo umount /media/cdrom*

I hope that this works for you.

    Sin Cere,

    CCNA

---

### Post by Irony on 2007-12-21
You can read off the disc and you can format it and write to it and format it and write to it - thus you can use it like a cd-r but many times.

However there is no program in linux that can read and write to a cd-rw like in windows.

---

### Post by bw44 on 2007-12-22
> **Irony said:**
> You can read off the disc and you can format it and write to it and format it and write to it - thus you can use it like a cd-r but many times.

However there is no program in linux that can read and write to a cd-rw like in windows.

Thanks for that information, Irony. It's not the answer I was hoping for, but so it goes.

Best.

---

