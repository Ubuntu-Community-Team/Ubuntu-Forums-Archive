---
title: "I need a little guidance with encrypting"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by stfu on 2006-02-12
I have an old 160Gb SATA drive that is not used at the moment. I'm thinking of using it as a storage for my media files. I would like to encrypt it with truecrypt since I have some experience with it in windows environment and they're promising a GUI for linux somewhere in the future.

Anyways, I'd like the encrypted disk to be easily mountable into somewhere in /home/user/media/ or such. If it prompted for the password on log-on it would be perfect. Can anyone give me some help with the commands and such and how to add the disk to auto-mount.

thanks.

---

### Post by stfu on 2006-02-13
I'm gonna bump this thread once. Someone has to know how to do this :)

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=stfu]I'm gonna bump this thread once. Someone has to know how to do this :)[/QUOTE]
These packages are seem to be related to what you want to do:
```

$ apt-cache search crypt | grep filesystem
encfs - encrypted virtual filesystem
loop-aes-utils - Tools for mounting and manipulating filesystems
lufs-cryptofs - Transparent filesystem encryption plugin

```
Can't say I've ever used any, but maybe someone else can provide more info.

---

### Post by aysiu on 2006-02-13
[QUOTE=stfu]I have an old 160Gb SATA drive that is not used at the moment. I'm thinking of using it as a storage for my media files. I would like to encrypt it with truecrypt since I have some experience with it in windows environment and they're promising a GUI for linux somewhere in the future.[/quote] Go [here](http://www.truecrypt.org/downloads.php) and download the .tar.gz for Ubuntu. You can extract the .tar.gz by double-clicking it and selecting **Extract**. Once the new folder appears, find the .deb file in there and copy it to your desktop.

Go to Applications > Accessories > Terminal and type these commands: ```
cd Desktop
sudo dpkg -i truecrypt_4.1-0_i386.deb
``` This all assumes you're using Gnome. If you're using KDE or something else, let me know.

---

### Post by stfu on 2006-02-14
I've installed truecrypt, but as it is a command line program I've no idea how to do the maneuvers I described. I have 64-bit system ubuntu.

---

