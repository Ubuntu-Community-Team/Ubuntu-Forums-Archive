---
title: "External hard drive"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Niranjan81 on 2006-05-30
Hi,
    am trying to put data inside a new external USB hard drive . though the HD is being recognised I cannot put files into it as it says that the user does not have permissions. how do I get the permissions to write into the HD? Its a new HD so I don't know whether Ican read from it though the permissions indicate that i can read n execute but can't write.Thanks

---

### Post by aysiu on 2006-05-30
Is it an NTFS hard drive? If so, forget about putting stuff on it from Ubuntu.

Otherwise, this might help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by catlett on 2006-05-30
How are you trying to put data in? Are you dragging and dropping folders into the new hd? Are you giving a command in the terminal to copy data from somewhere to the new hd? Are you downloading off the internet and trying to download directly to the new hd?

---

### Post by Niranjan81 on 2006-05-30
yeah its NTFS.... can i not change it to FAT?

---

### Post by Niranjan81 on 2006-05-30
yeah trying to drag n drop....

---

### Post by aysiu on 2006-05-30
[QUOTE=Niranjan81]yeah its NTFS.... can i not change it to FAT?[/QUOTE] If there's nothing on it, you can (in other words, all the data on it will be erased). Plug the drive in. Then, paste these commands into a terminal: ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` Then, click on the top-right button and find your external hard drive. Right-click on the partition on that drive and unmount it. Then, delete the partition. Then create a new one of type FAT32.

---

### Post by Niranjan81 on 2006-05-31
k...i deleted the NTFS partition ( i think).... the GParted window shows me 2 "pending " messages:

first is to delete the NTFS one and second is to create the fat one.... but nothing seems to be happening..... its kind of stuck there... is the conversion to Fat done ? i know i am very confusing but i really haven't worked with Linux at all n so have no idea as to whats happening!!

---

### Post by aysiu on 2006-05-31
This is me deleting my USB key and then creating a new FAT32 partition on it.

Did you not have these things happen?

---

### Post by Niranjan81 on 2006-05-31
hehe... i wasn't pressing the 'Apply' button ( i am retarded)...did it n things working just fine...can write into it perfectly!! :) Thanks !!

---

### Post by jorn on 2006-05-31
Did you press the "Apply" button?
Edit: You made it!

---

### Post by aysiu on 2006-05-31
I like easy solutions. Glad it worked out for you.

---

### Post by catlett on 2006-05-31
[QUOTE=aysiu]I like easy solutions. Glad it worked out for you.[/QUOTE]
They're easy when you're invoved.:-D

---

