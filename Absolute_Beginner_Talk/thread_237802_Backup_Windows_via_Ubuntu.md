---
title: "Backup Windows via Ubuntu?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by willywilly on 2006-08-16
Is there some tool to backup my hda1 partition with XP on it?

Mind though that that partition is 40GB (with 5GB of data on it) and my /home dir is only 10GB max. So I can't just make an image of that partition, I guess.

Your help is appreciated. :)

---

### Post by goatflyer on 2006-08-16
Assuming your drive C is mounted on /media/hda1, you could do a file-level backup with:

```


mkdir ~/backups
cd ~/backups
tar -cvzf mybackup_hda1.tgz /media/hda1


```

---

### Post by kepos on 2006-08-16
i think there is. but i'm not shure. i would suggest you to use Norton Ghost. i use it and it's good. it can compress your data so it willbe probably less than 5gb.

---

### Post by willywilly on 2006-08-16
Mhm. Thank you. :)

And how would I then go about reinstalling that?

Sorry for my simple questions but I'm fairly new to this.

---

### Post by arkham on 2006-08-16
5GB of data should compress down to the size of a DVD (4.7 GB) fairly easily - so you could use a DVD burner that to back up your Windows install.  Not sure what you mean about then installing it again - what exactly are you trying to do?

---

### Post by willywilly on 2006-08-16
By reinstalling I ment that I could just unpack the .tgz I created into hda1 - e.g. when WindowsXP killed itself and needs a new install.

---

### Post by willywilly on 2006-08-16
I just red a bit more about this matter - will this work at all? This is what I would like to do when Windows would stop working:

1. Launch Ubuntu
2. Reformat hda1 (NTFS)
3. Unpack my .tgz package containing a working version of XP into hda1
4. Launch Windows

Does Windows survive this?

---

### Post by willywilly on 2006-08-17
:/

---

### Post by kepos on 2006-08-17
i'm not so shure that just copying will work. try googling for free disk cloning tools.

---

### Post by willywilly on 2006-08-17
I found a tool called [partimage]("http://www.partimage.org/"), which will do just what I wanted. But I can not seem to install it. Aptitude can't find it and when I download their binary, I get two files ("partimage" and "partimaged") which I can't launch (nothing happens).

What do I have to do to install partimage (which seems to be quite a popular tool)? I don't think I have enough know-how to compile the sources myself, so I'd need a more simple way. ;)

---

### Post by waldschm on 2006-08-17
Hey Willy, I had some trouble finding a suitable solution for this myself. I tried using tar to create a tarball of the partition but that ultimately wasn't quite right for me, if you want to try that see this forum
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

What I use to backup now is partimage, don't try to install it in Ubuntu, well you can but you have to make sure to unmount filesystems and such before you image them. An easier solution is to download and burn the iso of the System Rescue CD [http://www.sysresccd.org/](http://www.sysresccd.org/). This is a livecd with partimage included so you don't have to install or mess with umounting. I would recommend trying it out as it worked well for me.

---

### Post by msak007 on 2006-08-17
Try using [this ]("http://psychocats.net/ubuntu/partimage.html")site for a reference on how to install / use partimage if you still want to give it a shot.

---

