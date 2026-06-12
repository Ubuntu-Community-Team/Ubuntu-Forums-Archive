---
title: "[SOLVED] Incorrect Disc Space?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2007-09-23
Hello Everyone.
I seem to be having a problem with disc space.

I have ubuntu gutsy installed on a 100gb hard drive.  It's formated with ext3, so the total disc space is 90.3gb.  After installing ubuntu and saving a handful of files to my computer I had a total of 64gb in free space.

Now it's three weeks later and my system only shows 37.3gb in free space.  The strange thing is, I don't have that much stuff on my drive.  

I was having this same problem under feisty.  The only reason I can think that it's doing this is:  

I use Pan to download files from a usenet server and I un-par these files with a program called "Parnrar" under wine.  After I unpar the files, I transfer everything over to my external hard drive.  I had this program set up to delete the par files when finished.  

So now nautilus says there's only 37.3gb of free space, but my home directory is only holding 935MB.  I am the only user on this computer.  There is nothing in my .Trash directory.

Does anyone know how I might be able to fix this?  I want to reclaim this disc space.

Thanks in advance for the advice!

---

### Post by por100pre1 on 2007-09-23
Did you take a look with Baobab?

```
sudo apt-get install gnome-utils
```

Any particular kind of files you use often? try locating them:

```
locate *file-type*
```

---

### Post by Skidpad on 2007-09-23
FileLight is another sweet program to literally see what's taking all of your disk space.  You can get it in Synaptic.  [Here]("http://www.methylblue.com/filelight/") is the page if you want to see a screenshot.

The only downside (if you see it that way) is that its a KDE app.

---

### Post by NewRubberSoul on 2007-09-23
I really appreciate both of you for helping me out on this one.  The solution was suprisingly simple.  I used por100pre1's advice and did:

```
locate par
```

after searching through the results, I noticed that there were files in:  

/home/brian/.local/share/Trash/

Which I assume is where this program (under wine) thinks the "Recycle Bin" is.  I was confused because they didn't show up in my trash can.  Needless to say, it was filled with junk.  It even took me about twenty minutes just to delete everything in that file.  Turns out it wasn't a matter of incorrect disc space, like I thought.

Thanks again for the help!  This is one of the reasons I love Ubuntu.

-Brian

:guitar:

---

### Post by por100pre1 on 2007-09-24
Glad to help. 8)

---

