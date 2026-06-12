---
title: "Pitivi isn't working!!"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Darrious on 2006-08-28
As the title says pitivi isn't working. It says I'm missing gstreamer 0.10.4 and I'm missing libxml2 amd glib2. I've tried to install it as a deb package, but it doesn't work very well. Here is there website, [Pitivi]("http://pitivi.sourceforge.net/") If anyone could offer anything else than that would be nice. I've tried Cinelerra, LIVES, Diva ([http://www.diva-project.org/](http://www.diva-project.org/) Hope I can get this to work) and Kino. Thanks

---

### Post by norwyn on 2006-09-03
Anyone knows how to install PiTiVi?
Any information would be great!

Thanks in advance.

---

### Post by norwyn on 2006-09-03
[EDIT] You can install PiTiVi (in dapper) through synaptic. 
Or you could just write:

```
sudo apt-get install pitivi
```

---

### Post by alexmoon on 2007-02-21
I managed to install it ok with synaptic, but every time I try to open it ... nothing happens.

I open it by going to "applications" -> "Sound & Video" -> "Pitivi Video Editor", and it then comes up with a section on the bar saying that "starting Pitivi", which then disappears without anything happening. I've also tried to get to it by opening video files (in Mp4 and .VOB formats) with Pitivi, but the same thing happens - it says it's opening the file, but then it just disappears without any noticable effect.

I'm using Ubuntu 6.10. Any ideas on what I'm doing wrong, or what I could use instead? (I want to be able to edit a few movies in these formats (Mp4 and .VOB) in fairly simple ways to use them as part of a lecture.)

Thank you!

---

### Post by timjayko on 2007-02-24
I have the same exact problem as last person who posted here on edgy as well =( any help would be appreciated

---

### Post by jjmatt on 2007-05-11
try opening it from the command line:

Alt+F2 -> gnome-terminal

then type 

```
pitivi
```

and post the results

EDIT: actually I just tried this with my working (kind of) pitivi and I got this error

```
$ pitivi 
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 60 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

```

What version of pitivi do you have installed? if you're using edgy you are probably not using the latest version, try upgrading to the newest one.

---

