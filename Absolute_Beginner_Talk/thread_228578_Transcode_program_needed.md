---
title: "Transcode program needed"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2006-08-03
I currently use VLC to transcode my mp3's to ogg's on my ubuntu box.  It does a great job but you can only do one file at a time.  I am looking for a program that will transcode multiple mp3's at once kind of like a batch file.

Thanks for any help

---

### Post by OU812 on 2006-08-04
I've never used it, but you could try

[http://www.linuxhardware.org/article.pl?sid=06/02/08/042226](http://www.linuxhardware.org/article.pl?sid=06/02/08/042226)

john

---

### Post by croak77 on 2006-08-04
I use mp32ogg to convert. It does single songs or by directory. If you want a GUI, there's soundconverter (GNOME gstreamer) or soundkonverter (KDE).

---

### Post by Elaztic on 2006-08-10
I use mp32ogg through the terminal converting whole directories at a time.
Works fine for me.
I just use it for my mp3 player so I can't really hear the little differences in quality if there are any.

Type mp32ogg -help or -? for options and howto.

---

### Post by Elaztic on 2006-08-11
I am pretty new to Linux so this might just be a very noob question:
Just found out that mp32ogg doesn't support spaces in the names of directories. Is this a common Linux terminal 'thing' or am I doing something wrong?
Eksample: /usr/bin/mp32ogg /home/<user>/music/new music
where <user> is the name of the current user.

Is there a work-around since I would have to rename all my mysic directories?

---

### Post by croak77 on 2006-08-13
> **Elaztic said:**
> I am pretty new to Linux so this might just be a very noob question:
Just found out that mp32ogg doesn't support spaces in the names of directories. Is this a common Linux terminal 'thing' or am I doing something wrong?
Eksample: /usr/bin/mp32ogg /home/<user>/music/new music
where <user> is the name of the current user.

Is there a work-around since I would have to rename all my mysic directories?

You need "\". It would bw /home/<user>/music/new\ music/. Or you can use tab completion.

---

