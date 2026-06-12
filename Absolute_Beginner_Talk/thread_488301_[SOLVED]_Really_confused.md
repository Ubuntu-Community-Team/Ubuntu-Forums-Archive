---
title: "[SOLVED] Really confused"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-30
Does anyone have any idea why I'd be able to make a folder in a volume and copy files to it but not be able to make a link to the folder I created?

---

### Post by eentonig on 2007-06-30
Nope, must be something you're doing wrong.

Can you check the permission on the folder? Who is the owner?

---

### Post by forestpixie on 2007-06-30
I'm the owner apparently with read/write - I've been having trouble getting permissions right since I reinstalled.

---

### Post by Alterax on 2007-06-30
Let's try looking at this from the other side:  What are your permissions in the directory that you are trying to create the link inside?  Could be a problem with the destination and not the source permissions.

--Alterax

---

### Post by forestpixie on 2007-06-30
Not sure now - looking at properties/permissions sheet 

I seem to have read/write folder access - but file access is - - -

I know I can copy stuff in and edit doc within directory.

---

### Post by forestpixie on 2007-06-30
bump

---

### Post by pistcivet on 2007-06-30
You want to make a link to a folder?
```
ln -s /folder/i'm/linking/to /link/to/that/folder
```
Maybe you're forgetting the "-s"
or getting the order backwards. (the target goes first)

What code are you using exactly?

---

### Post by forestpixie on 2007-06-30
I don't think it's that - it's down to screwed up permissions from after the reinstall.

It all went pear shaped after that! If I  have to reinstall just to sort permissions I shall scream!
:)

---

### Post by coolen on 2007-06-30
I've had troubles with backed up files after a reinstall. Go to the parent folder of the one you're linking to, and try
```
sudo chown -R username *
sudo chgrp -R username *
```
If that doesn't work, try it in the source directory, too (assuming you own that directory).
Good luck.

---

### Post by pistcivet on 2007-06-30
Well, if permissions are messed up,
You'll have to get busy with chown and chmod.

I royally screwed up permissions in a folder tree once,
took around 30 minutes to fix it all.

folders have to be 755 (drwxr-xr-x)
files have to be 644 (-rw-r--r--)    (some files might also be executable)
and all owned by proper user and group.

Good luck! :)

---

### Post by forestpixie on 2007-06-30
nope unfortunately not still same

---

### Post by hyper_ch on 2007-06-30
well, for symlinks you need root privileges:

```

sudo ln -s /path/to/destination /path/from/origin

```

---

### Post by forestpixie on 2007-06-30
> **hyper_ch said:**
> well, for symlinks you need root privileges:

```

sudo ln -s /path/to/destination /path/from/origin

```

i assume that if I'd gksudo nautilus I would have had root priveleges, if that's the case I couldn't do it then either!

I've been trying for 2 days to get this sorted and am now bald :D

---

### Post by hyper_ch on 2007-06-30
try it in the console

---

### Post by forestpixie on 2007-06-30
like to but not sure what I actually need to put! never had to do this - two days ago make link worked ! :)

tried this to make desktop link to college folder in volume 

```
kevin@kevin-desktop:~$ sudo ln -d /home/Desktop/college /media/hda5/College
ln: accessing `/home/Desktop/college': No such file or directory
```


edit - doing it other way round

kevin@kevin-desktop:~$ sudo ln -d /media/hda5/College /home/Desktop
ln: creating hard link `/home/Desktop' to `/media/hda5/College': Invalid cross-device link


Edit - and using -s instead of -d :D didn't work either
kevin@kevin-desktop:~$ sudo ln -s /home/Desktop/college /media/hda5/College
ln: creating symbolic link `/media/hda5/College/college' to `/home/Desktop/college': Operation not permitted

---

### Post by hyper_ch on 2007-06-30
it's not "-d" but "-s" and you need to switch it around... first comes WHERE you want to link TO and then comes WHERE you want to link FROM

```

sudo ln -s /media/hda5/College /home/Desktop/college

```

---

### Post by forestpixie on 2007-06-30
kevin@kevin-desktop:~$ sudo ln -s /media/hda5/College /home/Desktop/college
ln: creating symbolic link `/home/Desktop/college' to `/media/hda5/College': No such file or directory

---

### Post by coolen on 2007-06-30
> **forestpixie said:**
> kevin@kevin-desktop:~$ sudo ln -s /media/hda5/College /home/Desktop/college
ln: creating symbolic link `/home/Desktop/college' to `/media/hda5/College': No such file or directory

Are you sure /media/hda5/College exists?
If it's empty, try deleting it and recreating it from the terminal.

---

### Post by hyper_ch on 2007-06-30
pls post:

```

ls -al /media/hda5

```

---

### Post by forestpixie on 2007-06-30
here is the output of ls -al

```
kevin@kevin-desktop:~$ ls -al /media/hda5
total 292
drwxrwxrwx 5 kevin kevin  16384 1970-01-01 01:00 .
drwxr-xr-x 5 root  root    4096 2007-04-15 12:56 ..
-rwxrwxrwx 1 kevin kevin 195183 2007-06-28 14:07 bookmarks.html
drwxrwxrwx 7 kevin kevin  16384 2007-06-30 06:28 College
drwxrwxrwx 2 kevin kevin  16384 2007-06-23 07:55 Recycled
-rwxrwxrwx 1 kevin kevin   2482 2007-06-29 06:53 sources.list
drwxrwxrwx 5 kevin kevin  16384 2007-06-30 06:29 .Trash-kevin
-rwxrwxrwx 1 kevin kevin   3084 2007-06-29 06:33 xorg.conf
kevin@kevin-desktop:~$ 
```

and thanks for your help thus far :D

---

### Post by forestpixie on 2007-06-30
bump

---

### Post by forestpixie on 2007-06-30
again

resolved with a reinstall

---

