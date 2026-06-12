---
title: "Mount iPod Touch at /"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by parm289 on 2008-01-29
Hello,

I recently learned how to wirelessly mount my ipt thru ssh, and I must say it's pretty impressive.  I use a program on my touch that lets me download music straight to it, without a computer, but the thing is, it will only play in a certain 3rd party app, not in the mobilemusic app (the apple one).  I want to wirelessly sync to take the downloaded music off my touch and put it into my itunes library (maybe even without copying the files to the computer?  now that would be cool).  However, the problem is that when the ipod mounts, it isn't mounted at /, but rather at a lower directory that belongs to root (i believe /var/root/), where I don't have access to the folder containing the music.

So my question is, is there any way to access files from the / directory, or is that impossible because the files don't belong to root?

Thanks in advance for your help.

EDIT:  I looked into the directory where the files are downloaded, and its in the folder /var/root, while the touch is mounted at /var/root/media.  Is it possible to mount the touch at /var/root rather than /var/root/media?

---

### Post by skymera on 2008-01-29
ermm do you mean mount it to / ?

example below

```
 sudo mkdir /media/touch
sudo mount /dev/*** /media/touch 
```

to get the drive ID try

```
 sudo fdisk -l 
```

not thats a lower case L not a 1 :wink:

im not sure if that will do it but thats how i mounted my usb where i wanted it

---

### Post by parm289 on 2008-01-30
Im not sure if i made myself clear.  I already have a mount point for my ipod on my pc - i want to be able to view all files on the ipod instead of only /var/root.  Is this possible?  Btw, i mount my touch via ssh, not usb.

Edit: also, another question about syncing my touch with amarok - how do i sync the album art? Its already downloaded, but aince i synced with amarok no album art shows up on my touch.  Is the database file corrupted?

---

### Post by ntetreau on 2008-01-31
For the album art, take a look and follow this guide: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) It will show you how to use the package ipod-convenience, the newest amarok and ligpod to sync album art.  

As for your second request, let me just say that the program you use to download the music to your root folder isn't very good!  Why would it download it there of all places?  Anyway, after you have install ipod-convenience, you can change the mount point:

```
sudo gedit /usr/bin/ipod-touch-mount
```

and change it here:

    #Mount our Music Directory
    sshfs root@$IPADDRESS:/var/root/Media $MOUNTPOINT/ -o workaround=rename

You will also need to update the mount point in amarok and gtkpod so that instead of looking for your music in /media/ipod it will be in /media/ipod/Media/Music or something, double check

---

### Post by parm289 on 2008-01-31
thank you, this should work, ill try it when i have a chance.

---

