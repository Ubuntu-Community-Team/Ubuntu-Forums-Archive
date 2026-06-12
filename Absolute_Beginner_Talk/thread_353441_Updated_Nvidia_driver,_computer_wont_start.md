---
title: "Updated Nvidia driver, computer wont start"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by verymagicalguy on 2007-02-04
So I tried to update my Nvidia drivers with automatix. I let it run and it gave me this command to restore it in case something went wrong. The code was: 
```

sudo cp /etc/X11/xorg.conf_backup_200702040026/etc/etc/X11/xorg.conf 
```
Well now my computer wont start it says: "Failed to start the X server."

So I go into recovery mode and attempt to type in the command that automatix gives me and it tells me:
```

cp: missing destination file operand after /etc/X11/xorg.conf_backup_200702040026/etc/etc/X11/xorg.conf

```

What should I do? Am I typing the command wrong? Thanks for your help!

---

### Post by taurus on 2007-02-04
You forget a space in there.

```

cp  /etc/X11/xorg.conf_backup_200702040026   /etc/X11/xorg.conf

```

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by crumbum on 2007-02-04
I guess I didnt back up my xfile can I fix it of a live cd

---

### Post by taurus on 2007-02-04
Yes.  Boot with the LiveCD and open a terminal and do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming your Ubuntu is on /dev/hda1...)
sudo cp /etc/X11/xorg.conf   /mnt/ubuntu/etc/X11/xorg.conf
sudo umount  /mnt/ubuntu
```
Reboot and see if X is working again.

---

### Post by DarinB on 2007-09-09
Mr taurus you saved my system you guys are great i used the live cd used the formula you showed above just changed the hda to sda1 then i 
looked at what nvidia drivers live cd  chose in synaptic package manager rebooted then deleted and made everything look like the synaptic package manager of live cd now everything is back to normal.

thanks even my screen re fresh rate is back to 85 and i can see my screen with out a headache 

i love ubuntu and the forum members aren't bad either

---

