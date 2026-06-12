---
title: "Singing in Ubuntu - Rhythm Box Folder Copy"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-22
Greetings.
This is my system:

PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)

I have learnt how to make playlists in Rhym Box; however, because my songs folder is on a FAT32 partition on Drive "0", it loses the contents of the list every time I reboot and I have to rewrite it. I think it's because of the process of going to get the songs from the first drive and I have to type in my password also.

So I think it best to take my songs folder and have it in /home/andavane.

However I am not quite sure what the correct way to do this is, and in which branch of the directory I should place it in /home/andavane.

I assume that once all my songs are installed in Drive "1", Rhythm Box won't keep losing the contents of the playlist.

Regards

John

---

### Post by jfinkels on 2007-07-22
> **Andavane said:**
> Greetings.
This is my system:

PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)

I have learnt how to make playlists in Rhym Box; however, because my songs folder is on a FAT32 partition on Drive "0", it loses the contents of the list every time I reboot and I have to rewrite it. I think it's because of the process of going to get the songs from the first drive and I have to type in my password also.

So I think it best to take my songs folder and have it in /home/andavane.

However I am not quite sure what the correct way to do this is, and in which branch of the directory I should place it in /home/andavane.

I assume that once all my songs are installed in Drive "1", Rhythm Box won't keep losing the contents of the playlist.

Regards

John

You can make whatever directories and files you want in your own personal home directory. If you want to, for example, make a "music" directory in your home folder, type the following in the terminal ("Applications > Accessories > Terminal"):```
mkdir /home/andavane/music
``` to make the directory, and type the following:```
cp -r /path/to/musicsource /home/andavane/music
``` That should work, but you should test it on a small directory to make sure the command works (I can't test it right now, not on Ubuntu).

---

### Post by Andavane on 2007-07-23
Thank you,

Ok re the 1st bit:

Code:
> mkdir /home/andavane/music

I assume that "mkdir" instructs it to "make directory"

What does:

Code:
> cp -r /path/to/musicsource /home/andavane/music do?

I am of course happy to go to read a simple guide which explains this; it's just that I have a plethora of files and books too. There is so much information, it is really not easy to go to the bit you need. And it is less easy when you are working to a schedule, and there is not much time.

Thank you in advance

Regards

John

---

### Post by doomster on 2007-07-23
the cp command copies all the data from /path/to/musicsource to the  destination /home/andavane/music

---

### Post by jfinkels on 2007-07-24
> **Andavane said:**
> Thank you,

Ok re the 1st bit:

Code:


I assume that "mkdir" instructs it to "make directory"

What does:

Code:
 do?

I am of course happy to go to read a simple guide which explains this; it's just that I have a plethora of files and books too. There is so much information, it is really not easy to go to the bit you need. And it is less easy when you are working to a schedule, and there is not much time.

Thank you in advance

Regards

John

```
cp -r src dest
``` recursively (that's what the -r option means) copies a folder and all files and folders contained in that folder to the destination.

If you ever want to read more about pretty much any command, read the 'man pages' for the command. To view the 'man' page for a command, type the following in the temrinal:```
man *command*
```for example, to read about the 'rsync' command, type the following:```
man rsync
```

---

### Post by Andavane on 2007-07-24
Extremely useful to know...
Thanks I'll do that!
John

---

