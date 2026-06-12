---
title: "Compiz Theme? How to install?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-08-26
Hi,

Im trying to install a compiz theme. 
[http://www.gnome-look.org/content/show.php?content=44180](http://www.gnome-look.org/content/show.php?content=44180)

Can anyone tell me how to do this? I pretty much know nothing about it, and I doubt if I even have compiz installed. 

A small step by step guide would be nice, to get it working.

Thanks a lot :)

---

### Post by mostwanted on 2006-08-26
First of all, you need to use Quinn's Compiz packages and not the universe Dapper ones.

Make sure that whatever process you use to start Compiz starts *cgwd *instead of *gnome-window-decorator* (cgwd must be installed obviously). Then go into System -> Preferences and choose "CGWD theme chooser" (might be called something else). You can import the theme file from there and change your theme.

---

### Post by aktiwers on 2006-08-26
> **mostwanted said:**
> First of all, you need to use Quinn's Compiz packages and not the universe Dapper ones.

Make sure that whatever process you use to start Compiz starts *cgwd *instead of *gnome-window-decorator* (cgwd must be installed obviously). Then go into System -> Preferences and choose "CGWD theme chooser" (might be called something else). You can import the theme file from there and change your theme.

Mange tak Mostwanted

I did this

**Setting up the repository ...**

    First, open your /etc/apt/sources.list in an editor.
 sudo nano /etc/apt/sources.list
 **DAPPER DRAKE instructions**

   Then, insert one of these lines (each are various mirrors, and you can get deb-src from them too if you wish.)
  deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

and then did a ```
sudo apt-get install cgwd
```

Then update manager report that there is updates to install (a lot of lib stuff) and I update.

Then I write this in terminal and get the following error.

```
aktiwers@HAL:~$ cgwd
cgwd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
aktiwers@HAL:~$
```

Any idea?

Thanks

---

### Post by Dinerty on 2006-08-26
[http://www.ubuntuforums.org/showthread.php?t=224499&highlight=libGL.so.1](http://www.ubuntuforums.org/showthread.php?t=224499&highlight=libGL.so.1)

this thread any help?

---

### Post by aktiwers on 2006-08-26
> **Dinerty said:**
> [http://www.ubuntuforums.org/showthread.php?t=224499&highlight=libGL.so.1](http://www.ubuntuforums.org/showthread.php?t=224499&highlight=libGL.so.1)

this thread any help?

Thanks it worked!

But after importing the theme it doesnt run?

How do I make it run by defualt?

---

### Post by Christian Christiansen on 2007-12-09
I've got it running:)
But I liked one of the themes which used gnome-window-decorator but now I can't get that to work:(

Any ideas?

---

### Post by jordanmthomas on 2007-12-09
1.  This thread is ancient.
2.  Try running this:
```
gtk-window-decorator --replace
```
to switch back to the gnome window decorator.

...or did you actually follow the instructions in this thread?

---

### Post by Christian Christiansen on 2007-12-10
I think I followed the instructions on this thread but I'm not sure. Anyway thanks for the help.

---

