---
title: "Command Line Question"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by LsrLine on 2006-06-07
I have a 500GB external USB hard drive.  X server won't boot so I want to plug it in and copy all my data onto the ext drive which is FAT32. So:

1) Will Linux recognize the drive even though it won't boot x server,  and

2) What command do i need to use to access and copy to the external drive?  I'm curious to know even the cd rom drives too

Thanks guys!

---

### Post by fluffington on 2006-06-07
[QUOTE=LsrLine]I have a 500GB external USB hard drive.  X server won't boot so I want to plug it in and copy all my data onto the ext drive which is FAT32. So:[/QUOTE]

Not interested in just fixing the X server? 'Cause I might be able to help with that too.

[QUOTE=LsrLine]
1) Will Linux recognize the drive even though it won't boot x server,  and
[/QUOTE]

Try it and find out. If it works, it should mount somewhere in /media. Probably /media/usbdisk.

[QUOTE=LsrLine]
2) What command do i need to use to access and copy to the external drive?  I'm curious to know even the cd rom drives too
[/QUOTE]

```

cp -R <source> <dest>

```

Where <source> is the directory you want to copy from (if you want to backup your home directory, use "~"), and <dest> is the directory you want to copy to (assuming the drive mounts to /media/usbdisk, use "/media/usbdisk/" or whatever subdirectory of that you want to put your stuff in)

[QUOTE=LsrLine]Thanks guys![/QUOTE]

No prob. Hope that works.

---

### Post by nalmeth on 2006-06-07
follow previous poster's advice if you don't want to fix xserver.

have you run 

sudo dpkg-reconfigure xserver-xorg

?

---

### Post by LsrLine on 2006-06-12
it detect my drive sda and it says it's mounted to /media/tmp1 (i mounted it there), but when i go to it I can't see any of the files... i just see 
001 002 003 004 005 devices
when i type ls

as far as x is concerned, it seems to have nothing to do with xorg.conf.  I've tried sudo dpkg-reconfigure xserver-xorg and I have even tried switching the graphics card to an ati 9200 and i still get the same error when when booting up:

dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

FatalError re=entered, aborting
No GLX modules loaded

---

### Post by NoWhereMan on 2006-06-12
try:
```
sudo edit /etc/X11/xorg.conf
```
in the first lines you'll find a "section" there probably you'll read many things
and... glx
put a # before glx so that it reads
#glx
save and quit
now reboot or
```
sudo /etc/init.d/gdm restart
```

and see what happens

bye

---

### Post by LsrLine on 2006-06-12
[QUOTE=NoWhereMan]try:
```
sudo edit /etc/X11/xorg.conf
```
in the first lines you'll find a "section" there probably you'll read many things
and... glx
put a # before glx so that it reads
#glx
save and quit
now reboot or
```
sudo /etc/init.d/gdm restart
```

and see what happens

bye[/QUOTE]

same error message... nothing changed.

---

### Post by NoWhereMan on 2006-06-12
[QUOTE=LsrLine]same error message... nothing changed.[/QUOTE]
if you didn't, try to reboot. however I can't help more, here...

---

### Post by anaconda on 2006-06-12
You can use a linux liveCD for copying everything to your external USB-disk.

Then everything will be automounted, and you can yse graphical file-manager for copying.....

---

### Post by LsrLine on 2006-06-12
So does anyone else have any ideas on how I could get my data off my hard drive?  My computer has been like this for a week now :(

---

### Post by elemental666 on 2006-06-12
boot the livecd, mount your internal hd and external hd, copy to your hearts content, then reinstall 6.06 from within the same livecd session, when its done, reboot into the fresh dapper install and copy your stuff back to your internal hd...

that's the hard way, I don't know the easy way.

tip: next time around you might want to setup a backup/restore solution and use it, it'll make this situation much easier to deal with.

---

