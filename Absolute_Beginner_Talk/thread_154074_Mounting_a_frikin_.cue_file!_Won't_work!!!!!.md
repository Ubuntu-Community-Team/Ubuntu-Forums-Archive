---
title: "Mounting a frikin .cue file! Won't work!!!!!"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by pkroks on 2006-04-02
Damn! I have been trying to mount a .cue file, I can't do it... Don't know why. Probably some noob thing I have forgotten to do. 

Anyway, I tried following this sites instructions: [http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso](http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso)

I get an error saying: 

```

mount: mount point /mnt/isoimage/ does not exist
```

Now to me that means I gotta create a directory with it or something. :dunno:


I also tried installing CDEmu. I did that. Now I have mounted the file on the first drive/virtual drive. When I got to browse the disc under /media/iso   there is nothing there. WTF

So I entered the command to see what devices and images are mounted. It gave me what was supposed to be there, this---> 

```

Drive Loaded Comment
  0:     1   zulpi111.cue
  1:     0   NO_CD_LOADED
  2:     0   NO_CD_LOADED
  3:     0   NO_CD_LOADED
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED
  6:     0   NO_CD_LOADED
  7:     0   NO_CD_LOADED

```

But I still can't find the mounted image. WTF

This is annoying!

---

### Post by hollywoodb on 2006-04-02
CUE files are not ISO images. You need to use cdemu.  Also, the BIN file is the actual disc image, CUE file is a cue sheet.  CUE file is useless without corresponding BIN file. MPlayer can play BIN files natively if by chance you're trying to view media from the image.

I haven't actually used cdemu myself, but if all else fails you can convert the BIN file to ISO.

[CD Image Conversion Utilities]("http://wiki.linuxquestions.org/wiki/CD_Image_Conversion")

---

### Post by patrick295767 on 2006-04-02
Look there : [http://cdemu.org/](http://cdemu.org/)
in install.
  
It worked well for me.
   
=========
  
If you need a frontend, Kcdemu exists too.
cdemu 	 Kernel module to simulate CD drives + CD with cue/bin files 	 GPL v2 	 users operating with CD images 	a very usefull tool because creating images can already be created and burned by k3b, but mounting them cue/bin is not that easy. [see KCDemu in the KDE Wishlist, too]
=======

 Greetings

---

### Post by pkroks on 2006-04-02
[quote=hollywoodb]CUE files are not ISO images. You need to use cdemu. Also, the BIN file is the actual disc image, CUE file is a cue sheet. CUE file is useless without corresponding BIN file[/quote]

I don't think you read my post correctly. I said I had tried cdemu. It gave me the output and said the .cue file was mounted or whatever. I have got the corresponding .bin file.

---

### Post by adamkane on 2006-04-02
You need to create a directory to mount to:

```

sudo mkdir /mnt/isoimage

```

Let me know if this helps.

This Nautilus-Script should help, if you routinely mount cdrom images:
[http://www.ubuntuforums.org/showthread.php?t=149963](http://www.ubuntuforums.org/showthread.php?t=149963)

---

### Post by pkroks on 2006-04-02
Nope. Still doesn't work after entering the command to make the directory. I was supposed to use cdemu with that right? Or how do I mount it otherwise?

---

### Post by adamkane on 2006-04-02
This should work. Report any error messages. 

Specify your own "filename.cue" and "mountdir". 

Ubuntu uses /media rather than /mnt, but either directory should work.

mount:
```

sudo mkdir -p /media/mountdir
cdemu 0 filename.cue
sudo mount -t iso9660 /dev/cdemu/0 /media/mountdir

``` 
unmount:
```

cdemu -u 0
sudo umount /media/mountdir 
sudo rmdir /media/mountdir 

``` 
I suggested you use Thread 2 and 3 of my mountiso post, but that is only necessary if you routinely mount bin/cue files.

---

### Post by ctothej on 2006-06-08
> sudo mount -t iso9660 /dev/cdemu/0 /media/mountdir

This should really be:

```
sudo mount -t iso9660 /dev/cdemu0 /media/mountdir
```

Otherwise, works perfectly. Thanks!

---

