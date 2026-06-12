---
title: "Opening windows apps with Wine question"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by DKYang on 2007-03-28
Hey everyone,

I have installed Wine and know how to use it if I want to install a windows apps on ubuntu, but how can I open the app that I already have installed on my XP. I am dual booting both Ubuntu and XP on my laptop. If you don't know what I'm talking about then watch this video:

[http://www.youtube.com/watch?v=Q564OEmseXE](http://www.youtube.com/watch?v=Q564OEmseXE)

He starts to do what I'm talking about at 2:10.

He replied back and doesn't know how it works because he didn't need to do anything.

I thought I would had to mount my windows partition or something, but I don't really know.

Anyone have any idea on how to make this work? 

Thanks.

---

### Post by halitech on 2007-03-28
you would have to mount the windows partition fisrt and then from a terminal, run

```

wine /path/to/windows/file/you/want/torun/app.exe

```

actually, thinking about it I dont think that would work because the files would not be within the "windows" install in WINE. could give it a shot, might work

---

### Post by crispy_420 on 2007-03-28
Just associate .exe files with wine.

Right click any exe file and go to properties. Select "Open With" along top of new window. Select "add", wine won't be on the list there so we select "use custom command" at bottom. Then just type wine. That in effect will issue a command with out a command line. Now when you double click it will issue a command in the background. There are other options but this is by far the easiest yet, and you never need to open a terminal.

Example: double click of mediaplayer.exe = wine /hda2/program files/mediaplayer.exe

The issue you may have is the need to mount the windows partition. There are plenty of guides on that in these forums. Just watch out for NTFS, I've heard of people who have used read/write drivers and have toasted their NTFS partitions and made them unreadable.

---

### Post by NicoleM on 2007-03-28
bumping this so it doesn't disappear..i'm also interested.  I haven't yet installed wine so I can't try things or make any guesses yet but i have world of warcraft isntalled on ym windows drive and it would be nice to not have to relog when i want ot play :)

edit: guess i had this window open for a while before i replied...didn't realize ther ewas a reply just 10 minutes ago.  thanks! :)

---

### Post by zvacet on 2007-03-29
```
winefile
```

One of drive look in your phisical windows [I don´t remember wich one but it i not hard to find out).Try that way.

---

### Post by crispy_420 on 2007-03-29
So did my solution work for you?

---

