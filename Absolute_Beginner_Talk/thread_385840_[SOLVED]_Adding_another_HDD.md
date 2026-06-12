---
title: "[SOLVED] Adding another HDD?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-16
Ok im still a lil new to Ubuntu.. i have 2 internal HDDS, one has everything on it swap ect, how do i add the other one to the system? any help would be much appreciated

Thanks, Davey

---

### Post by ouilsen on 2007-03-16
Sadly your second hd will have to become a folder on your root filesystem where you can mount it. It's not possible to just extend a partition with a second hd and have more free space on your root filesystem.

So there are 2 steps:

1) start gparted and create a partition. Format it and choose your filesystem (f.ex. ext3).
2) now create a folder where you want to mount your newly created partition. This can be in /media or /home/yourname/.

f.ex.:
```
sudo mkdir /media/2ndhd
```
in /home/yourname you don't have to use sudo.

3) Let's mount the partition. 
```

sudo mount /dev/hdb1 /media/2ndhd
```

/dev/hdb1 should be correct.

4) If this works and you can access your hd we have to be able to automount it. Therefore we edit /etc/fstab and append a line like this:
```

/dev/hdb1  	/media/2ndhd   ext3  	rw, auto, user  	1 1
```

Voilà... this should work.

---

### Post by DaveyG on 2007-03-16
Thanks, that seems to have added the other as a folder :)

---

### Post by mahy on 2007-03-16
> **Davey Goudou said:**
> Thanks, that seems to have added the other as a folder :)

This is Unix world, everything's a file. And please refrain from using the world 'folder'. It's a directory, which is also a file ;)

---

### Post by rpommier on 2007-03-17
I followed those instructions, how do I verify that the HDD is indeed added?  I did the disk usage analyzer and my filesystem size grew to 110gb (80gb hda1 + 40gb hdc1)

Does Ubuntu just add it to the filesystem automatically?  Is it part of my /home directory now?  Basically how do I know that I am using this space to store data now?

vr,
Roderick

---

### Post by DaveyG on 2007-03-17
> **mahy said:**
> This is Unix world, everything's a file. And please refrain from using the world 'folder'. It's a directory, which is also a file ;)

Ok, let me say it again.... "Thanks, that seems to have added the other as a directory :) "

lmao

---

### Post by captin_moor on 2007-03-29
Hi ther Guys and girsl. I have the same problem. However I am running and server edition of ubuntu 6.06 and do not believe that gparted will work on it. I have attempted to create an ext3 partionon my new drive and have created several logical and primary partions on it as well. I have then rebooted the server and have attempted to mount the drive to /home/<user>/link with the following command. sudo mount /dev/hdb1 /home/<user>/link but I am getting an error message. 

Its saying that either the drive is already mounted or that the destinaion is busy. I have been trying to get this sorted for days and am feel lost. Can somone please help. Thanks

---

### Post by captin_moor on 2007-03-29
> **captin_moor said:**
> Hi ther Guys and girsl. I have the same problem. However I am running and server edition of ubuntu 6.06 and do not believe that gparted will work on it. I have attempted to create an ext3 partionon my new drive and have created several logical and primary partions on it as well. I have then rebooted the server and have attempted to mount the drive to /home/<user>/link with the following command. sudo mount /dev/hdb1 /home/<user>/link but I am getting an error message. 

Its saying that either the drive is already mounted or that the destinaion is busy. I have been trying to get this sorted for days and am feel lost. Can somone please help. Thanks

Please disregard this last comment as if have resolved the problem. I was using sudo to do all this work and for some reason it did not work. Yet when I went through su it worked fine. all good, cheers

---

