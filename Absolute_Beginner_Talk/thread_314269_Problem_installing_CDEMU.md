---
title: "Problem installing CDEMU"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by feap on 2006-12-07
I'm trying to mount a video bin/cue file Daemon Tools-style (no, direct mounting in Linux only works with isos and Mplayer won't play the bin directly either) and downloaded the tar for CDEMU but can't get it to install.

I extracted the tar to its own directory under home folder and I use the instructions on:
[http://cdemu.sourceforge.net/#install](http://cdemu.sourceforge.net/#install)

I didn't do Step 1 as I have no clue what it means. I get stuck with step 4 as I get:

"bash: make: command not found"

Also, no go with the general instructions from here:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

./configure gives me "no such file or directory", sudo make install gives "sudo: make: command not found".

Why does this have to be so complicated? How do I get this thing to install or are there other easier solutions available?

---

### Post by Bachstelze on 2006-12-07
```
sudo apt-get install build-essential
```

then try running your *make* again.

---

### Post by taurus on 2006-12-07
To build something from source, you need the build-essential package first...

```
sudo aptitude update
sudo aptitude install build-essential
```
Are you sure you're in the right directory when you ran the "./configure" command?  What's the output of this command then?

```
ls -la
```
Yes, mplayer can play .bin video

```
gmplayer filename.bin
```
Otherwise, you can use bin2iso to convert it to iso and mount it and play it with any media player...

---

### Post by feap on 2006-12-07
> **HymnToLife said:**
> ```
sudo apt-get install build-essential
```

then try running your *make* again.

Ok, I tried but I get a prompt to insert my Dapper Drake CD but I don't have a CD. (This is not the first time this has come up and one reason why I moved away from XP; why does Ubuntu require a CD when it's a free OS.) So I had to stop the process and apparently it didn't finish as make still doesn't work.

edit:

Yes, I was in the right directory. And I got Mplayer to finally work with the bin file with the command taurus provided: I didn't remember Linux filenames are case sensitive (yet another stupid "feature"). It's weird that drag-and-drop doesn't work from File Browser to Mplayer window. Oh well, command prompt works.

Thanks a lot for very quick help! I'm off to watch some quality Cheech & Chong :D

---

### Post by taurus on 2006-12-07
You need to edit /etc/apt/sources.list and put a # in front of the first line regarding CD-ROM.  Then, it won't ask you to insert a CD-ROM in the drive anymore.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Then,

```
sudo aptitude update
sudo aptitude install build-essential
```

---

