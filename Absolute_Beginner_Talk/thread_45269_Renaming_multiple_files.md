---
title: "Renaming multiple files"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by bagg on 2005-06-29
I have a bunch of mp3s that have the artist name in the file name. Such as

01 Artist - song1.mp3
02 Artist - song2.mp3
03 Artist - song3 .mp3
etc...
etc...

I want to remove the '0x Artist -' part because I like to store my songs in a Artist\Album\Songs fasion. I think it can be done using cut, and removing the first x characters of the filename, but I can't figure it out. I have read the man pages, but it's not making much sense to me. Can someone help me out? 

TIA

---

### Post by Sionide on 2005-06-29
Hmm, I'd probably be looking into writing a bash script for something like that but it's no easy task..

---

### Post by bagg on 2005-06-29
[QUOTE=Sionide]Hmm, I'd probably be looking into writing a bash script for something like that but it's no easy task..[/QUOTE]


Thats what I figured, and why I asked.

---

### Post by poofyhairguy on 2005-06-29
Try easytag:

[http://www.ubuntuforums.org/showthread.php?t=45166](http://www.ubuntuforums.org/showthread.php?t=45166)


It does batch stuff.

---

### Post by cwaldbieser on 2005-06-29
[QUOTE=bagg]I have a bunch of mp3s that have the artist name in the file name. Such as

01 Artist - song1.mp3
02 Artist - song2.mp3
03 Artist - song3 .mp3
etc...
etc...

I want to remove the '0x Artist -' part because I like to store my songs in a Artist\Album\Songs fasion. I think it can be done using cut, and removing the first x characters of the filename, but I can't figure it out. I have read the man pages, but it's not making much sense to me. Can someone help me out? 

TIA[/QUOTE]

For the above format of songs, the following one liner should work:

```
ls | awk ' {printf("mv \"%s\" \"%s\"\n", $0, $4) | "bash"}'
```

Explanation:
1) ls lists all the files in the directory.  This list is piped to awk.
2) An awk action is executed for ever line of the script (the default match).
3) The awk action executed is to print the command mv <filename> <4th field of filename>.  The fields in the filename are delimited by spaces.
4) The last part of the awk action pipes the printed command to the bash shell.  The shell happily renames the file.

---

### Post by bagg on 2005-06-30
Awesome, I will give that a try, Thanks for the responses

---

