---
title: "loging in as root ?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-03
I have mounted several hard disks. I don't have premmision to write to them, when i try to change the premmision i get a message that only "root" can do this.

I have only one account, and that's mine.
I try to login as :
user name  : root
password : my account password
it doesn't work

what should i do ?

---

### Post by Titus A Duxass on 2007-01-03
Root is disabled by default, log in as normal user and 
use sudo, it works the same as root.

Do as normal user (for example):

sudo apt-get install XX 
Enter your user passwd

Root can be enable as part of the install process if you press F6 and select expert mode at the first screen you see when booting from the CD.

---

### Post by Sasa_Ivanovic on 2007-01-03
> **Titus A Duxass said:**
> use sudo, it works the same as root.

Do 

sudo apt-get install XX 
Enter your user passwd
i know about sudo, but i want to learn how to login as root.
and i can't add premmisions with sudo, or i can but it's complicated.

---

### Post by Malac on 2007-01-03
Ubuntu uses sudo to change temporarily to root access so for example.
```
sudo chmod +x test.bin
```
would change test.bin to be executable.

If you are more comfortable with doing it in nautilus then :
```
sudo nautilus
```
will bring up a root privilege nautilus so you can right-click the file and change the permissions from the properties option.
I have a shortcut setup for quick access to this, that way when in mid-compile and I find I haven't set one of the file permissions correctly, it's quicker than cd'ing to the folder and typing in the commands. :)

Hope this helps.

---

### Post by Titus A Duxass on 2007-01-03
[https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d) - this will explain all.

do:
 
sudo passwd root

and then give it your new root passwd.

---

### Post by Malac on 2007-01-03
Okay just read last reply:
Go to [System->Administration->Login Window] then "Security" Tab and tick "Allow local system administrator login"
Then go to [System->Administration->Users and Groups] choose root then "Properties" under "Password" set as complex a password as you can remember (as you hopefully won't be using this often).

---

### Post by rejser on 2007-01-03
Or else you could
sudo -s
enter your password and you are in root mode.

---

### Post by Sasa_Ivanovic on 2007-01-03
OK i loged in as root. But i still can't change premmisions. It says that the disk is read only...
heres the screenshot : [http://img518.imageshack.us/img518/6793/screenshotoz2.png]("http://img518.imageshack.us/img518/6793/screenshotoz2.png")

---

### Post by Malac on 2007-01-03
How are you mounting the disks?
If you are using /etc/fstab then you need to set the umask to 111 to allow read/write access to everyone.
e.g.:
```
/dev/hda1 /mnt/C_Win98 vfat defaults,utf8,**umask=111**,gid=46 0 1
```
This is for a fat32 windows drive.

---

### Post by nsleiman on 2007-01-03
sudo su

---

### Post by Sasa_Ivanovic on 2007-01-03
> **Malac said:**
> How are you mounting the disks?
If you are using /etc/fstab then you need to set the umask to 111 to allow read/write access to everyone.
e.g.:
```
/dev/hda1 /mnt/C_Win98 vfat defaults,utf8,**umask=111**,gid=46 0 1
```
This is for a fat32 windows drive.
still got problems.
here's the output of the terminal :

```

root@sasa-desktop:~# sudo cp /home/sasa/desktop/VCP.rar /media/usbdisk/VCP.rar
cp: cannot stat `/home/sasa/desktop/VCP.rar': No such file or directory
root@sasa-desktop:~# sudo cp /home/sasa/Desktop/VCP.rar /media/usbdisk/VCP.rar
cp: cannot create regular file `/media/usbdisk/VCP.rar': Read-only file system
root@sasa-desktop:~# sudo su
root@sasa-desktop:~# sudo cp /home/sasa/Desktop/VCP.rar /media/usbdisk/VCP.rar
cp: cannot create regular file `/media/usbdisk/VCP.rar': Read-only file system
root@sasa-desktop:~# /media/usbdisk /mnt/C_Win98 vfat defaults,utf8,umask=111,gid=46 0 1
bash: /media/usbdisk: is a directory
root@sasa-desktop:~# /media/usbdisk /mnt/C_Win98 vfat defaults,utf8,umask=111,gid=46 0 1

```

---

### Post by Sasa_Ivanovic on 2007-01-03
ok i looked up mount command and here's what i do :
```

 mount /dev/hda /mnt/nesto ntfs  defaults,utf8,umask=111,gid=46 0 1

```
still doesn't work.

---

