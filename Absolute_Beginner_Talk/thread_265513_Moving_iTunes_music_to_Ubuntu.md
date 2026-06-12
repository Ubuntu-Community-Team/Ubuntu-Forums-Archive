---
title: "Moving iTunes music to Ubuntu"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by coolbian57 on 2006-09-26
I was thinking about common sensing this one and just taking the CD's i have and re-copying them.  But i still think the knowledge would be useful and may give me some insight on how to use Ubuntu more efficiently.  This would save me a lot of time...  Does anyone have any suggestions, comments, questions?

---

### Post by hearnden on 2006-09-26
There are a million ways you could do this.  Personally, I tend to hold on to my music longer than I hold on to any music player or pod managing application, so I like to organise my music just through the file system.  All your music files (mp3s?) should be somewhere in your iTunes folder, so you can just copy them into wherever you want keep your music.  So here's my recommendation.

1.  Make sure all you tags are up to date (artist, album, track name, ...).  You can use something like easytag to manage them.
2.  Ensure all your music files have unique names.  You may want to rename your files according to album-track, or just title, or artist-title, or whatever (easytag can do this very easily).
3.  Copy all your mp3s into somewhere you will manage them.  e.g.
```

$ cd <whereever-your-iTunes-folder-is>
$ cp -i $(find . -name *.mp3) ~/music

```

This will copy all mp3s find in your iTunes folder (and any sub folders) into ~/music.  That's why it's important they have unique names.  The -i switch will inform you of any name clashes though.

4.  Structure your music folder how you see fit (not how iTunes or any other app wants you to).  I personally organise my music folders as artist/album/tracktitle.  easytag can do this for you (which is why it is important to have your ID3 tags filled in).

5.  Point your music player of the month to your ~/music folder.


Like I said, there are many ways you can solve your problem, but I use this method because
1.  I like to control where my music is, and have it all in one place.
2.  Changing players won't re-layout my music.

And this will teach you a little bit about moving files around (and mounting ntfs partitions if you're moving files from windows xp).

---

### Post by hearnden on 2006-09-26
whoops, I meant 'mv' instead of 'cp' if you want to move, rather than copy, your music files.

---

### Post by theknave on 2006-09-26
So wait, I would say:

```
$ cd <C:\My Music>
$ cp -i $(find . -name *.mp3) ~/music
```

That doesn't seem right, it seems too easy.

---

### Post by mostwanted on 2006-09-26
1) Open nautilus window inside iTunes music folder
2) Open nautilus window inside new music folder
3) Ctrl+a, ctrl+c in iTunes music folder
4) Ctrl+v in new music folder
5) "File -> Import folder" in your preferred music app.

---

### Post by hearnden on 2006-09-26
If all your music is in C:\My Music, then here's what may be all you need to do:

```

$ mkdir ~/music
$ sudo mkdir -p /windows
$ sudo mount -t ntfs -o umask=0222 /dev/hdaX /windows
$ cd "/windows/My Music/" 
$ cp -i -R * ~/music

```

The first command makes sure you have a 'music' folder in your home directory.  The second and third commands mount your Windows partition so that Ubuntu can read your Windows files.  You'll need to replace /dev/hdaX with the name that corresponds to your Windows partition (see 
[here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") for more info).  The fourth and fifth commands just copy all your music to Ubuntu.  Note that this has to be a copy, because Linux can only safely read NTFS partitions; writes (i.e. deleting your music from Windows) are not yet stable.

---

