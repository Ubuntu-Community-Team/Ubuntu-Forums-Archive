---
title: "Change Permissions For USB Discs"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-07-12
I Plugged in my usb discs (ipod, external hd etc.). Right Click -> Properties -> Permissions . . . can't change any to Read and Write. How do change these permissions please?

---

### Post by gidra on 2007-07-12
Any ideas?

---

### Post by nitro_n2o on 2007-07-12
You can use "chmod" to change permissions and "chown" to change file ownership
For example, 
In the terminal type: 
```
sudo chown your_usr_name /media/usbdisk 
``` so you'll be the owner 
if you want to make all files writable 
```
sudo chmod +w /media/usbdisk
```
and of course ur ultimate friend man:
```
man chmod
man chown
```

---

### Post by Inxsible on 2007-07-12
nitro is correct except that you might want to use the chown command like so

```
sudo chown -R <your username>:<your group> <path to mount point of the device>
```a user may belong to multiple groups and so it kinda screws it up if you dont specify which group. I could be wrong, but its safe to list it too. Generally your group and username are one and the same. -R = recursive and will do it for all files and folders within that mount point too

---

### Post by gidra on 2007-07-12
I tried those commands but i'm still stuck with read-only permissions. 

chmod: changing permissions of `/media/sdb1': Read-only file system

:(

---

### Post by Inxsible on 2007-07-12
This is mostly because the drive was removed uncleanly from a Windows machine and it has created a lock on it. Plug the disk into a Windows machine and do the 'Safely Remove Hardware' thingy. Wait for a it to be removed cleanly and then try plugging it back into the Linux machine.


Hopefully that should help !!

---

### Post by gidra on 2007-07-12
Booted windows, safely remove hardware thingy, restart in linux, sudo chown -R bla bla bla and i'm  back to square one :confused: ; no write access. For once i adore windows' insecurity. I used to use Mepis, it used to allow me write access permissions easily, is it so difficult in ubuntu ?

---

### Post by Al3xK3aton on 2007-07-12
Try logging in as the root user, it will let you have more control.

---

### Post by gidra on 2007-07-12
As far as i know Ubuntu doesn't allow you to log in as root. Anyways it surely doesn't on mine cause it won't accept the password neither from login window nor by SU from terminal.

---

### Post by Inxsible on 2007-07-12
> **gidra said:**
> As far as i know Ubuntu doesn't allow you to log in as root. Anyways it surely doesn't on mine cause it won't accept the password neither from login window nor by SU from terminal.

If you mean that you cant see the asterisks when you type in the password, then dont worry. It is taking in your password just not showing you anything. Put in your password and hit 'Enter'. It should work.

You can also do a ```
sudo nautilus
``` to log into nautilus as root.

---

### Post by Inxsible on 2007-07-12
> **gidra said:**
> As far as i know Ubuntu doesn't allow you to log in as root. Anyways it surely doesn't on mine cause it won't accept the password neither from login window nor by SU from terminal.

If you mean that you cant see the asterisks when you type in the password, then dont worry. It is taking in your password just not showing you anything. Put in your password and hit 'Enter'. It should work.

You can also do a ```
sudo nautilus
``` to log into nautilus as root. This is highly discouraged however, because you can really mess up your system if you don't know what you are doing.

---

### Post by Inxsible on 2007-07-12
hmm..Sorry for the double post... I dont know what happened :confused:

---

### Post by gidra on 2007-07-12
When entering Su password in Terminal gives me 
su: Authentication failure
(password is correct since it works fine with sudo)

sudo nautilus /media/sdb didn't even allow to view the contents of the device let alone write on the disc.

Anyways i'm not interested in using root to have this damn write access, i'm sure there's a more 'normal' way of doing it. Yet, max respect for trying to help me out

---

