---
title: "xorg.conf problem"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by tumble on 2007-08-04
So I'm a bit of a newbie- this is a stupid mistake. I was editing xorg.conf slightly and made a mistake. When I restart I can't get into the gui so I can use the command line a bit and open the file. Is it possible to load up a safe graphics mode like on the live cd? or can I edit the xorg.conf file, if so how? 

:confused:

---

### Post by w4ett on 2007-08-04
From Grub, boot into recovery mode. This will get you to a command line. From there type:

```


sudo dpkg-reconfigure -phigh xserver-xorg
```

this will get you to an interface to select your video driver and resolutions. scroll through the driver selections and select the 'vesa' driver, then select the resolutions that you want. The cursor keys move the cursor, <spacebar> makes selections and <enter> confirms the selections. Save and quit the interface, then type:


```

startx

```
this should get you into a GUI Desktop

---

### Post by Stemp on 2007-08-04
try this command :
sudo dpkg-reconfigure xserver-xorg

---

### Post by benx009 on 2007-08-04
> **tumble said:**
> So I'm a bit of a newbie- this is a stupid mistake. I was editing xorg.conf slightly and made a mistake. When I restart I can't get into the gui so I can use the command line a bit and open the file. Is it possible to load up a safe graphics mode like on the live cd? or can I edit the xorg.conf file, if so how? 

:confused:


do you remember what you did to your xorg.conf file?  if its nothing too drastic, you can probably get the gui running again w/o having to do *sudo dpkg-reconfigure xserver-xorg*

---

### Post by tumble on 2007-08-04
Thanks all you folk -its been a big help. Im gonna give it a try soon. you learn something new everyday.

---

### Post by forestpixie on 2007-08-04
> **tumble said:**
> So I'm a bit of a newbie- this is a stupid mistake. I was editing xorg.conf slightly and made a mistake. When I restart I can't get into the gui so I can use the command line a bit and open the file. Is it possible to load up a safe graphics mode like on the live cd? or can I edit the xorg.conf file, if so how? 

:confused:

and of course you made SURE that you made a backup - just that you can't remember the name ;) 

how many times did I say that-  once too many :D


tsh tsh of course the command could be 

```
sudo cp xorg.backupname xorg.conf
```


Backups in linux are as important as those in windows - said the man who lost a drive of media files :D

and I do really mean that - without meaning to make you feel worse than you already do- Good  luck to you

---

