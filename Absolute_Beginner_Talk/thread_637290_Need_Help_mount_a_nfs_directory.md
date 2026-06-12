---
title: "Need Help mount a nfs directory"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-10
i am having problems mounting a nfs directory i have it setup for /media/network and then on the laptop which i am trying to mount to ```
sudo mount 192.168.1.66:/media/network 
```

but when i type that nothing happens it says it does not exist. This is my export file /etc/exports
```
/media/network *(ro,sync,no_root_squash)


```

---

### Post by bodhi.zazen on 2007-12-10
You need a mount point :

sudo mount 192.168.1.66:/media/network /media/nfs

Call it what you want, and make it first :

```
sudo mkdir /media/nfs
sudo mount 192.168.1.66:/media/network /media/nfs
```

Add it to fstab if you want it to mount @ boot

---

### Post by Rocket2DMn on 2007-12-10
Did you make sure to create the folder at /media/network ?  The directory may need to be owned by root.
```
sudo(?) mkdir /media/network
sudo mount 192.168.1.66:/remote/path /media/network
```

Also check out [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Manually](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Manually)

---

### Post by fedex1993 on 2007-12-10
but network is a hardrive partition under /media/network/ do i need to make another file in /network

---

### Post by Rocket2DMn on 2007-12-10
I'm not entirely sure what you're asking there.  The remote directory needs to be mounted at a directory on your machine.  So for example, you want to mount 192.168.1.66/some/remote/directory
you create a folder locally to access that remote folder, let's say you want to use /media/nfs like b.z suggested.  You would run
```

sudo mkdir /media/nfs
sudo mount 192.168.1.66:/some/remote/directory /media/nfs
```

---

### Post by fedex1993 on 2007-12-10
this is what i get when i start the nfs kernal ```
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/media/network".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

```

---

### Post by bodhi.zazen on 2007-12-10
You need to make a mount point on the local file system.

So, sudo mount 192.168.1.66:/media/network is on the server.

You can call the mount point /media/network or you can call it something else

mount <dev> < mount_point>

---

### Post by fedex1993 on 2007-12-10
okay what yall are not udnerstanding is that /media/network is a directory where i plan to store the files at *network* in media is a hardrive partition just for wha ti want it to do. i am just trying to mount to /media/network/ then upload files there in /media/network with no other diffrent directories inside of it

---

### Post by fedex1993 on 2007-12-10
> **bodhi.zazen said:**
> You need to make a mount point on the local file system.

So, sudo mount 192.168.1.66:/media/network is on the server.

You can call the mount point /media/network or you can call it something else

mount <dev> < mount_point>

so what you saying is that i need to mount a directory for it on my laptop not the server i guess that is what you are trying to explain

---

### Post by Rocket2DMn on 2007-12-10
So are you trying to just copy everything over to your local machine?  Or do you want to access the files FROM the remote directory only (like if keep all the music for your household there?)
If you literally want to just copy everything over, then mount the remote folder at a different directory like /media/remote - then you can drag and drop (or command like cp) to your local hard drive partition at /media/network.  Depending on the size, it could take awhile to do the network transfer.

---

### Post by fedex1993 on 2007-12-10
know my question is how can i give permission for my laptop user of seand to write to that nfs directory

---

### Post by Rocket2DMn on 2007-12-10
I have to run out the door right now, but it sounds like you just want to access the remote directory with R/W permissions.  Do what we originally suggested.  If you still have problems, PM bodhi.zazen since he might have stopped watching this thread.
Good luck, sorry I can't stay.

---

### Post by fedex1993 on 2007-12-10
how can i give permissions to read and write to my nfs so that my laptop and my main desktop can read and write and upload or download to it

---

### Post by fedex1993 on 2007-12-10
can any one help me or i guess i will need to wait a while for a post ugg

---

### Post by Rocket2DMn on 2007-12-10
OK, I'm back.
If it is not letting you access the remote folder, you can try adding the mount to your fstab file.
Start by unmounting the remote folder
```
sudo umount /media/nfs
```
Then you need to open your fstab file:
```
gksudo gedit /etc/fstab
```
Add the correct line with read/write permissions:
```
192.168.1.66:/some/remote/directory /media/nfs nfs defaults 0 0
```
Save and close.  Then mount by running (this mounts everything in your fstab file.
```
sudo mount -a
```
If that doesn't work, try changing the "defaults" to "rw,hard,intr"
Post back with your results.  If you have problems, please post back the contents of your fstab file as well as what happens when you run the mount command as we tried earlier.

---

### Post by fedex1993 on 2007-12-10
> **Rocket2DMn said:**
> OK, I'm back.
If it is not letting you access the remote folder, you can try adding the mount to your fstab file.
Start by unmounting the remote folder
```
sudo umount /media/nfs
```
Then you need to open your fstab file:
```
gksudo gedit /etc/fstab
```
Add the correct line with read/write permissions:
```
192.168.1.66:/some/remote/directory /media/nfs nfs defaults 0 0
```
Save and close.  Then mount by running (this mounts everything in your fstab file.
```
sudo mount -a
```
If that doesn't work, try changing the "defaults" to "rw,hard,intr"
Post back with your results.  If you have problems, please post back the contents of your fstab file as well as what happens when you run the mount command as we tried earlier.

okay it works perfect thank you very much and i am sorry for my ipaitenchish

---

### Post by bodhi.zazen on 2007-12-11
Thanks Rocket2DMn, well done

---

### Post by fedex1993 on 2007-12-11
i give you props to bodhia.zazen

---

