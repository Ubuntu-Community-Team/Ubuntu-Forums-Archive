---
title: "command to list folder contents and write to text file"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by aleska on 2007-03-07
I'm still in my first year of using ubuntu (now playing with kubuntu a bit too), and am not super strong on bash or other CLI skills.  I'm looking for help on the right command to use to do the following:  
I want to run a command which will look at a particular folder, and its subfolders and write all the files contained in them to a text file.  So, for example, I have a folder /music.  In /music I'd have many other folders /artistA , /artistB , etc. Under those would be album folders, and then finally the actual files song1.mp3, song2.mp3, etc.
I want to run a command which will look through /music and all its subfolders and list all the files contained in them and have it saved as a text file.
In the list that goes to text, I also want it to display the appropriate path.

so the output in the text file would look something like a typical m3u or m3u8 playlist file...

/music/artistA/albumA/song1.mp3
/music/artistA/albumA/song2.mp3
/music/artistA/albumB/song1.mp3
/music/artistA/albumB/song2.mp3
/music/artistB/some album title/some song name.ogg
/music/yet another artist name/white album/time_to_learn_some_bash.mp3
...

etc. etc. you get the picture.

I believe that this is probably something very simple to do; but I don't have the foggiest what commands to use, the syntax to follow, or anything.

Thanks so much in advance!
-aleska

---

### Post by 23meg on 2007-03-07
```
find -type f -print > filename
``` should work.

---

### Post by musings on 2007-03-07
Hi aleska,

It will be a combination of the 'ls' command in a terminal, with some options to list the full path, and then piping the output to a text file.

It will look like:

```
ls [some options] > output.file
```

A read of man ls in a terminal should give you the options you need.

Regards, Gary

---

### Post by coxc24 on 2007-03-07
ls -R1 /your/music > output.txt

This will list the directorys and then the files contained in each directory in a file called output.txt in your working directory.

---

### Post by aleska on 2007-03-07
Thank you all!
I've just had a bit of fun trying these suggestions out and reading through the man for **ls** and **find**.  I find these simple real world problems are what help me to learn best.  To be honest, most of my needs in file hunting and reading contents of directories have been met sufficiently through gui's like nautilus and konquerer.  So, this was a great experience for me: having a need that really required command line action! :-D

What I find particularly interesting is that **ls** using the **-R** option seems to group folder contents together.   Specifically, rather than printing the following:
> /folderA/folderB/file1
/folderA/folderB/file2
/folderA/folderB/file3
it prints:
> /folderA/folderB:
file1
file2
file3
I could see where this would come in handy; but, for my purposes of creating output in m3u playlist format, it isn't the right solution.  Searching through the man pages, I tried a variety of different options, but couldn't find any way to turn off that folder contents grouping.  If I missed something, please let me know; I'm definitely interested in learning.

It appears that the suggestion by 23meg is very close to what I need.
```
find -type f -print > filename
```
In particular what I like about find, is that I could use expressions to limit results (i.e. find files with specific extensions AND meet some other criteria but NOT including xyz).  If **ls** has similar capabilities, and I just overlooked it, please let me know.  This is helpful in my particular case, b/c I'll want to weed out non-music files like jpg album art.

Again, thanks to you all: 23meg; musings; and coxc24! :)

---

