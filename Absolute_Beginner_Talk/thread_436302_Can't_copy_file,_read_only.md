---
title: "Can't copy file, read only"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dibbz on 2007-05-07
I'm trying to move over a file to my memory stick in my psp. 

I've tried manually dragging the file to the folder but get the error that the folder I'm trying to move it to is read only. 

I tried to do it via terminal with the follwing command line 

```
sudo mv -v a-mgsops.cso /media/psp/iso
```

I get the error mv: cannot create regular file `/media/psp/iso': Read-only file system when doing that command. 

Any help?

---

### Post by fakie_flip on 2007-05-07
What do you get from this?

mount | grep iso

---

### Post by dibbz on 2007-05-07
> **fakie_flip said:**
> What do you get from this?

mount | grep iso

What is it meant to do? 

I'm not familiar with it, so I don't want to try it out

Care to explain? 

><
 :)

---

### Post by obrient on 2007-05-07
Do you have rights to work with the file? If you do an ls -alh in the directory that the file is stored in it will show you what the premissions are. ie -rwxrwxr-x  this is done in groups of three. The first rwx is for the owner of the file. the next is for the group and the last is for anyone else. The - means that the  person doesn't have the rights. What you want the file to look like is something like this.
```
-rwxrwxr-x  3 username username 4.0K 2006-10-31 18:53 file.iso
```

Username should be your user. If it isn't your user or a different user then you don't have the rights to the file. To change these permissions you will need to change the ownership.To do this you will want to do:

```
sudo chown username:username
``` 

 sudo will make you root  chown means change ownership and then use the username of your regular user. This will allow you to manipulate the file.

---

### Post by dibbz on 2007-05-07
This is what I get 

-rwxr-x---  1 dibbz dibbz 843M 2007-05-07 22:11 a-mgsops.cso

Seems like a few letters are missing there. 

How can I copy the orginal file over with full permissions? I copied the orginal file from a different partition on my HDD to my home folder in Ubuntu, with a simple cp <name>.

EDIT:- OK solved it. I just right clicked my file, and changed the access to read and write. It was read only first. 

Thanks for the help guys.

---

### Post by obrient on 2007-05-07
Hum looks like the permissions should work.What that is telling you is your user dibbz has read write and execute rights for the file, the group dibbz has only read and execute rights, and no one else can mess with the file. 

Can you move something else to that location? Create a simple text file and see if you can move it there. Looking at the other post in relation to:

```
mount | grep iso
```

should tell you if the iso /media/psp/iso is mounted as a drive. Fakie_flip is seeing if the PSP drive is mounted so that you can write to it.

You can also type 

```
mount -v
```

which will show what you have mounted. You should see a line something like 

```
/media/psp/iso type usbfs (rw)
```

Which means that the PSP is mounted. 

In relation to changing the file permissions you would do

```
sudo chmod 0777 file.iso
```

This would give everyone read, write, and execute permissions.

---

### Post by ilikeytacos12345 on 2007-05-08
hi, this is fakie_flip, but im using my brothers computer, so im on his name.

push alt f2 and type xterm. push enter. type this in.
```

mount | grep iso
```

push enter. what do you get?

i suggest you start reading man (short for manual) pages for more information.

```
man mount
```

i suspect you have mounted it with read-only permissions without looking at the mount man pages. first unmount it.

```
sudo umount /media/psp/iso
```

then you need to mount it like this.

```
mount -o loop,rw file.iso /media/psp/iso
```

update: you dont have to unmount it first. by reading the man pages like you should do, i found the remount option. this command will do it all.


```
mount -o loop,rw,remount /media/psp/iso
```

btw, no i dont care to explain. RTFM and find out what it does.

---

### Post by TC-cheesy on 2007-06-11
Hello
I, too am having trouble mounting my psp too copy files over, or to delete files and make more room. I have tried the steps above, but to no avail. please help me!

---

### Post by nmtsunami on 2007-09-13
If you want to have write permissions in every folder in your PSP you just need to enter in the terminal window the following command:

$sudo mount -o loop,rw /media/disk/

The /media/disk option must be equal to your PSP read only drive that as been mounted automatically by Ubuntu.

In my case this solution works quite well.

If you want to delete files do a Shift+Delete

nmtsunami

---

### Post by thomsany on 2008-05-29
Well, I tried doing those instructions and the PSP connects automatically. However, I can move, copy, whatever I want but as soon as I disconnect the device, the files are gone.
No way of copying them and having them stay there... any suggestions?
I tried even opening a SUDO NAUTILUS and nothing stays on the PSP...
Regards,
Teo

---

