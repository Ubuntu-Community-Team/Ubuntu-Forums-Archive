---
title: "Mass renaming of Folders"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-08-13
I've recently converted my music collection so its now all at the same bitrate mp3 using Sound Converter 0.9.4 but a bug in this means the folders it created have "%20" instead of spaces (this is apparently fixed in 0.9.6 but this is only available for gutsy I believe). So is there a quick way to mass rename these folders (like a find and replace function)?

---

### Post by purdticker on 2007-08-13
If you know any perl you could do it pretty quickly in there...

If you know how to use openoffice.org calc you can do it that way as well...

1. Open terminal
> 
cd /your/music/directory
find . > out.txt


Import the data in out.txt to OpenOffice.org Calc... use formula's to make a bunch of mv commands to paste into terminal

replace()
concatenate()
mid()
left()
right()
etc.

For a one-time-thing, this will work...

---

### Post by annda on 2007-08-13
install gprename - it's a batch renamer using perl
```

sudo apt-get install gprename
```

---

### Post by capink on 2007-08-13
Thunar also has a bulk rename functionality. Just select all the files you want to rename and right click rename.

Edit: Make sure you have thunar installed. If not:

```
sudo apt-get install thunar
```

---

### Post by &#12465;&#12452;&#12488; on 2007-09-20
> **annda said:**
> install gprename - it's a batch renamer using perl
```

sudo apt-get install gprename
```
GPRename doesn't seem to be able to pull off recursive renaming. :( It's pretty useless for me that way. Isn't there any application that'll mass rename folders recursively? I've been googling my *** off.

> **purdticker said:**
> If you know any perl you could do it pretty quickly in there...
But if you don't, it's not so quickly done.

---

### Post by caelum on 2007-12-25
> **Matuku said:**
> I've recently converted my music collection so its now all at the same bitrate mp3 using Sound Converter 0.9.4 but a bug in this means the folders it created have "%20" instead of spaces (this is apparently fixed in 0.9.6 but this is only available for gutsy I believe). So is there a quick way to mass rename these folders (like a find and replace function)?

I have just found Métamorphose File -n- Folder Renamer. It says "A cross platform file and folder mass renamer, allows many different renaming operations in a GUI."

After downloading/installing, it works for me!

---

### Post by erginemr on 2007-12-25
You may also give a try to krename, a KDE based renaming utility.

---

### Post by vanadium on 2007-12-25
The Find command allows you to find directories, and you can execute a command, e..g the "rename" command on each item it finds.

"man find" learns that we can find all directories this way

find music/ -type d

To rename a directory, you can use the command

rename 's/%20/\ /g' "Directory%20with%20wrong%20spaces"

Use the -n option to test, i.e. you see how the dir will be renamed, but it won be effectively renamed,

Now, we use find's exec option to do this for any directory we find

find music/ -type d -exec rename -n 's/%20/\ /g' {} \;

You see that I added -n here so that on a first run, you can see if everything will be as expected. Remove the -n to have the rename be carried out effectively.

---

