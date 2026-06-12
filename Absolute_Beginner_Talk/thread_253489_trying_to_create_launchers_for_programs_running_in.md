---
title: "trying to create launchers for programs running in wine."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-09-08
I am trying to create a launcher to programs running in wine. right now I am working on geting photoshop 7 going. the path is .wine/drive_c/Program Files/Adobe/Photoshop.exe . So I tried to create an application launcher wiht this wine /.wine/drive_c/"Program Files"/Adobe/Photoshop.exe when I try to open it nothing happens. I might as well have double clicked an empty space on the desktop.

---

### Post by terminatingzero on 2006-09-08
Give this a try and see if it works:
wine .wine/drive_c/Program\ Files/Adobe/Photoshop.exe

It has to do with the way the space in Program Files is handled in GNU/Linux.

---

### Post by TyphoonJoe on 2006-09-08
What happens if you open a terminal and type:
ls -al /.wine/drive_c/"Program Files"/Adobe/Photoshop.exe

I am guessing this path does not exist.  For my wine installation it is off of my home directory, so I wonder if you need to put this as your path:
~/.wine/drive_c/"Program Files"/Adobe/Photoshop.exe

---

### Post by onesojourner on 2006-09-08
nope still nothing. I tried to go into my adobe folder and "make link" and that has the same result. puts an Icon in the folder that does nothing.

---

### Post by onesojourner on 2006-09-08
> **TyphoonJoe said:**
> What happens if you open a terminal and type:
ls -al /.wine/drive_c/"Program Files"/Adobe/Photoshop.exe

I am guessing this path does not exist.  For my wine installation it is off of my home directory, so I wonder if you need to put this as your path:
~/.wine/drive_c/"Program Files"/Adobe/Photoshop.exe

I get this

ls: /.wine/drive_c/Program Files/Adobe/Photoshop.exe: No such file or directory

and for the second one I also get

peter@desktop:~$ ~/.wine/drive_c/"Program Files"/Adobe/Photoshop.exe
bash: /home/peter/.wine/drive_c/Program Files/Adobe/Photoshop.exe: No such file or directory

---

### Post by TyphoonJoe on 2006-09-08
Try this:

```
ls -al /.wine/drive_c/Program\ Files/Adobe/Photoshop.exe
```

If that does not work this Photoshop.exe is not where we expect. 

Simple way to find where it is (may be slow, sudo in case it is somewhere you don't have permission to view):
```
sudo find / -name Photoshop.exe 2>/dev/null
```

Once we know where Photoshop.exe is getting a shortcut will be easier ^_^

---

### Post by blakesmith on 2006-09-08
I have been trying to create a link to a wine prog as well...

wine ~/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe

..works just fine in term but not as a link, even when 'run in terminal' is checked in the Add to Panel prog... any ideas?

---

### Post by onesojourner on 2006-09-09
ok I finally got it. thanks TyphoonJoe

I ran  sudo find / -name Photoshop.exe 2>/dev/null (that is a handy one to know, thanks)

then just stuck in the quotes for the files that had spaces.

wine /home/peter/.wine/drive_c/"Program Files"/"Adobe/Photoshop 7.0"/Photoshop.exe

works like a charm.

now if I could only get my samba working like it was in breezy....

---

### Post by bodhi.zazen on 2006-09-09
> **blakesmith said:**
> I have been trying to create a link to a wine prog as well...

wine ~/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe

..works just fine in term but not as a link, even when 'run in terminal' is checked in the Add to Panel prog... any ideas?

This usually work for me:
wine "/home/User_Name/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe"

---

### Post by ferebee on 2006-09-09
I use Puppy Linux too, and over on their forum a poster suggested 
creating a small script as a launcher, and gave a example showing how.

[http://www.murga.org/~puppy/viewtopic.php?t=9536&postdays=0&postorder=asc&start=0]("http://www.murga.org/~puppy/viewtopic.php?t=9536&postdays=0&postorder=asc&start=0")

Look for the second post by Nathan F on that page.

---

