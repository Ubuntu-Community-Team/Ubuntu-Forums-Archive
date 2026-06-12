---
title: "Torrent Files Question."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-06-10
I just downloaded a file, and it says it's in .mp3 format. I double click, and it says it's a text file, not an mp3 file.

Am I doing something wrong? Or did I download a bogus torrent? This is the 2nd time it happened... but I just figured it was something I messed up the first time.

---

### Post by bobbocanfly on 2007-06-10
Did you download the actual files using the torrent client? If you have try using a different site to find your torrents, whatever you are downloading is a bit dodgy.

---

### Post by Sianis on 2007-06-10
What program did you use to try playing the mp3 file(s)?

---

### Post by Roasted on 2007-06-10
azureus.

---

### Post by Sianis on 2007-06-10
Try open a mp3 file from this site: 

[Link]("http://www.m-base.org/sounds.html")

---

### Post by reclusivemonkey on 2007-06-10
The command file may help you ascertain what the file actually is;

```

file *filename*

```

I just created a "mp3" from a text file, and file is smart enough to know what it is;

```

monkey@mother:~/studio/audio$ cat /home/monkey/gtd/holidays.txt > ./holidays.mp3
monkey@mother:~/studio/audio$ file holidays.mp3 
holidays.mp3: ASCII text

```

---

### Post by Roasted on 2007-06-10
Why won't it let me use "file" to see what it is? I've tried everything.



jason@jason:~/Music$ file Only One
Only: ERROR: cannot open `Only' (No such file or directory)
One:  ERROR: cannot open `One' (No such file or directory)
jason@jason:~/Music$ file OnlyOne
OnlyOne: ERROR: cannot open `OnlyOne' (No such file or directory)
jason@jason:~/Music$ file Only One.mp3
Only:    ERROR: cannot open `Only' (No such file or directory)
One.mp3: ERROR: cannot open `One.mp3' (No such file or directory)
jason@jason:~/Music$ file Only
Only: ERROR: cannot open `Only' (No such file or directory)
jason@jason:~/Music$ file OnlyOne.mp3
OnlyOne.mp3: ERROR: cannot open `OnlyOne.mp3' (No such file or directory)
jason@jason:~/Music$ file Moments.mp3
Moments.mp3: ERROR: cannot open `Moments.mp3' (No such file or directory)
jason@jason:~/Music$ file moments.mp3
moments.mp3: ERROR: cannot open `moments.mp3' (No such file or directory)
jason@jason:~/Music$

---

### Post by Nythain on 2007-06-10
on the Only One issue, type file Only\ One.mp3 and see if that helps???

---

### Post by Roasted on 2007-06-11
Doesn't work. That's why I tried Moments.mp3, which is just 1 word for the name.

---

### Post by muguwmp67 on 2007-06-11
Do you know what folder you told azureus to save to?  Did you download a folder or an individual .mp3 file?

---

### Post by reclusivemonkey on 2007-06-11
> **Roasted said:**
> Why won't it let me use "file" to see what it is? I've tried everything.

```

jason@jason:~/Music$ file Moments.mp3
Moments.mp3: ERROR: cannot open `Moments.mp3' (No such file or directory)

```


I can only assume there is "No such file or directory", as the error message states. What does

```

ls -l ~/Music/Moments.mp3

```

give you?

---

