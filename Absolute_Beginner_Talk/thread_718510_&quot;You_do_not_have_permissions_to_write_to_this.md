---
title: "&quot;You do not have permissions to write to this folder&quot;"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by andy_blah on 2008-03-08
Greetings again,
I have made a partition and I have mounted as hdb4 under /media/. I tried to copy from another partition some files but it gives me this message: 
> Error while copying to "/media/hdb4".
You do not have permissions to write to this folder.
I have searched a bit over the forums but I did not found anything relevant.

What shall I do to grant the permission to write under that folder?


Thank-you in advance,
>-Andy-<

---

### Post by Aeph on 2008-03-08
I have gotten this message also, usually when trying to access "locked" directories that were created in Windows.

---

### Post by legend2440 on 2008-03-08
In the teminal type
gksudo nautilus and enter your user password

Browse to the /media folder and right click on the directory you are mounting to and open properties then click on permissions tab on top of window

Make sure your user name is in the owner and group fields and also that read write execute boxes are checked

Another thing to consider is if we are talking about copying files from a windows partition that is ntfs to a linux partition such as ext3 then you will need to install ntfs-config

sudo apt-get install ntfs-config will do that or you can open synaptic and install it that way

Hope that helps

---

### Post by justsomedude on 2008-03-08
```
sudo chown -R yourusername:users /media/hdb4
```

---

### Post by andy_blah on 2008-03-08
It had worked, Thank-you both!

---

