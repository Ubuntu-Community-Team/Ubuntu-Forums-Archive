---
title: "can't get in to my second hdd"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by mastif on 2007-01-17
hello, Im new at linux, I have tried to mount my other hdd but I dont get it, so can someone tell me what I have to do to get in to my other hdd. I have ubuntu 6,06

this is what comes up when i click on it:
[http://img242.imageshack.us/img242/6751/screenshot2kn7.png](http://img242.imageshack.us/img242/6751/screenshot2kn7.png) <- edit to english!

sry if my spelling isnt so good ;>

---

### Post by taurus on 2007-01-17
I assume it's a Windows drive...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, paste the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mastif on 2007-01-17
"sudo fdisk -l"  [http://img62.imageshack.us/img62/8896/screenshotqy2.png](http://img62.imageshack.us/img62/8896/screenshotqy2.png)

"sudo nano /etc/fstab" [http://img62.imageshack.us/img62/3152/screenshot1uo9.png](http://img62.imageshack.us/img62/3152/screenshot1uo9.png)

it didnt work with the guide, or I did something wrong :s

its a SATA-II hdd. with music and stuff on it :p

---

### Post by taurus on 2007-01-17
Isn't sfs filesystem which is that crappy SCO's filesystem?

---

### Post by haxer on 2007-01-17
Hmm.. this is my friend i said it should be ntsf? [http://img62.imageshack.us/img62/8896/screenshotqy2.png](http://img62.imageshack.us/img62/8896/screenshotqy2.png) <---this one sfs is sataII hdd thats the one he wants to mount

---

### Post by haxer on 2007-01-17
Please help

---

### Post by souki on 2007-01-17
can you try to mount it from the terminal ?

```
sudo mkdir /media/test-sda1
sudo mount -t ntfs -o ro /dev/sda1 /media/test-sda1
```paste the result here if it doesn't work

---

### Post by mastif on 2007-01-17
yes a think it worked!
but I cant view the files anyway, I dont have the premission to do it, it says

[http://img217.imageshack.us/img217/3066/screenshot3hb7.png](http://img217.imageshack.us/img217/3066/screenshot3hb7.png)

---

### Post by taurus on 2007-01-17
```
gksudo nautilus
```

---

### Post by mastif on 2007-01-17
> **taurus said:**
> ```
gksudo nautilus
```

YES! THANKS!

but now, do I have to write that everytime i start my computer?
cause, I cant go in /media/test-sda1 with going the way Places>Computer>Fliesystem>Media>Test-sda1 , its locked with an red [X]

---

### Post by taurus on 2007-01-17
Just put an entry in /etc/fstab so it would be mounted each time you boot.

```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/sda1   /media/test-sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it and then reboot.

---

### Post by konst88 on 2007-01-17
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by souki on 2007-01-17
duplicate post (tooo sloowwww)
well done taurus :)

---

### Post by taurus on 2007-01-17
> **souki said:**
> duplicate post (tooo sloowwww)
well done taurus :)

Thank you.  ;)

---

### Post by mastif on 2007-01-17
thanks everyone :) Ill try reboot now and see if it worked :)

IT WORKED! :D:D thanks<3 :) *happy*

---

