---
title: "Is this how Jackfield is to be ran?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-10
Here's exactly what I'm doing...

1) download each file from
[http://svn.kryogenix.org/svn/jackfield/trunk/jackfield/](http://svn.kryogenix.org/svn/jackfield/trunk/jackfield/)
2) download national geographic (natigeo) widget from apple.com and
saved it to /home/shane/widgets (i've tried with it zipped and
unzipped)
3) edited Control.py to say "WIDGET_DIRS = ["~/Library/Widgets","/home/shane"]"
4) used the command "LD_LIBRARY_PATH=/usr/lib/firefox python
~/Desktop/jackfield/Widget.py /home/shane/"

I also tried the command with the .zip file unzipped as
"LD_LIBRARY_PATH=/usr/lib/firefox python ~/Desktop/jackfield/Widget.py
/home/shane/NatiGeo.wdgt.zip_FILES/"

And this results in the following message...

```
LD_LIBRARY_PATH=/usr/lib/firefox python ~/Desktop/jackfield/Widget.py
/home/shane/
Traceback (most recent call last):
 File "/home/shane/Desktop/jackfield/Widget.py", line 256, in ?
   w = Widget(pth)
 File "/home/shane/Desktop/jackfield/Widget.py", line 64, in __init__
   raise "Not a complete widget"
Not a complete widget

```

---

### Post by shanepardue on 2006-11-10
I think I'm on to something. Where is the file this says I'm missing?

```
LD_LIBRARY_PATH=/usr/lib/firefox python ~/Desktop/jackfield/trunk/jackfield/Widget.py ~/widgets
Traceback (most recent call last):
  File "/home/shane/Desktop/jackfield/trunk/jackfield/Widget.py", line 257, in ?
    w.run()
  File "/home/shane/Desktop/jackfield/trunk/jackfield/Widget.py", line 185, in run
    mask, imgwidth, imgheight = self.__getMask()
  File "/home/shane/Desktop/jackfield/trunk/jackfield/Widget.py", line 169, in __getMask
    self.closeIcon = gtk.gdk.pixbuf_new_from_file(
gobject.GError: Failed to open file '/home/shane/Desktop/jackfield/trunk/jackfield/WidgetResources/JackField/active-close-button.png': No such file or directory

```

---

### Post by davim on 2006-12-30
try this: [http://ubuntuforums.org/showthread.php?t=320835&highlight=jackfield](http://ubuntuforums.org/showthread.php?t=320835&highlight=jackfield)

---

### Post by d3v1ant_0n3 on 2006-12-30
I've yet to see a report of anyone actually getting Jackfield to actually *do* anything so far. I'd love to see it working.

---

### Post by shanepardue on 2006-12-30
I'm gonna wait til it's a litte more developed. I tried at it for awhile, but it was too much of a pain.

---

