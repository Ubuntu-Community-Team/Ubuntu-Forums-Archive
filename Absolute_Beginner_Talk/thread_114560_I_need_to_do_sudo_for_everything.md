---
title: "I need to do sudo for everything?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by 0x001A4 on 2006-01-08
I just installed Ubuntu today and its great so far.

The only problem I have is that I can't do anything without being root. I wanted to delete a folder of music today through Nautilus but couldnt, so I had to go through the terminal and basicly do "sudo rm /dir" which isnt a huge deal, but will get annoying if I have a bunch of things to erase at once.

Does anyone know how I can change this? Like is there a way to go into superuser mode in Nautilus?

---

### Post by 23meg on 2006-01-08
```
gksudo nautilus
```will give you a superuser nautilus. Enter it in the "run application" dialog you get with alt+f2.

---

### Post by kingsidy on 2006-01-08
you do not have to sudo for everything. make sure that you use the regular user account so that most of the music folders for example will be owned by the user not root. that would allow u to delete it without sudoing.

---

### Post by d1337 on 2006-01-08
How many users did you set up after install?  Are you running (logged in) as the user that you created during install?  If the folder belongs to who you are logged in as, you shouldn't have to use sudo to alter that folder unless the permissions were set up that way.  Are the folders shared/mounted from another OS?

d1337

---

### Post by 0x001A4 on 2006-01-08
Well yes, it's a drive that I formatted in FAT32 and is associated with WindowsXP. 
I had SuSe on here and it showed that drive as /windows/D
I checked the permissions and for some reason the owner for every folder on that drive is root and the permissions are set at 755.

But the first answer will help alot! Thanks!

---

### Post by 23meg on 2006-01-08
Modify your fstab file to give yourself the proper permissions on the drive.

[http://ubuntuguide.squarecows.com/doku.php#windows](http://ubuntuguide.squarecows.com/doku.php#windows)

---

### Post by 0x001A4 on 2006-01-08
Thats odd. I put exactly what it told me to put in fstab and it still doesnt give me access.

This is the line I put at the end of the file:

/dev/sdb1       /media/data     vfat    iocharset=utf8,umask=000   0       0

Do I need to get rid of the other mount point for the same drive? And how would I get one of those funky drive icons on my desktop that got put there automatically?

---

### Post by 23meg on 2006-01-08
Did you remount everything after making changes with ```
sudo mount -a
``` or a reboot? And yes, remove your old line, have one line in fstab for each drive.

---

### Post by 23meg on 2006-01-08
[QUOTE=0x001A4] And how would I get one of those funky drive icons on my desktop that got put there automatically?[/QUOTE]
Disable this key in Applications / System Tools / Configuration Editor : /apps/nautilus/desktop/volumes_visible .

---

### Post by 0x001A4 on 2006-01-08
Thats beautiful. Thanks alot for your help.

And when I took out the first line and rebooted, it put a drive icon on my desktop for me :)

---

### Post by 23meg on 2006-01-08
Glad it helped you; now if you don't want that icon, take a look at my last post..

---

### Post by Zillion on 2006-01-09
Why is there no root terminal anymore in 5.10? Or how do I get a root terminal?

And after i installed konsole, i click on session, new root session, if i type there my password it just throws me back in normale konsole???  :confused: 

tx

---

### Post by Mustard on 2006-01-09
[QUOTE=Zillion]Why is there no root terminal anymore in 5.10? Or how do I get a root terminal?

And after i installed konsole, i click on session, new root session, if i type there my password it just throws me back in normale konsole???  :confused: 

tx[/QUOTE]

This wiki page tells you how to get to a root terminal using sudo (as well as other things about root and sudo)...

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The short answer is..

```
sudo -i
```

---

### Post by Zillion on 2006-01-09
thank you!

---

### Post by Perfect Storm on 2006-01-09
Actually if you go into application menu editor (or smeg) you can find it under System tools. Just activate it and it shows up in your application tab. (look for root terminal)

---

