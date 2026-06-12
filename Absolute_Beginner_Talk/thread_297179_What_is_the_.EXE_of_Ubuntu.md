---
title: "What is the .EXE of Ubuntu"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-11-10
So I am trying to run VLC media player.  I am trying to set it as the default player when the popup window pops-up on websites that have a streaming radio player.  The dropdown list only shows REAL currently.

How do I track down the "run" file for VLC?  In windows it used to be the .exe.  What is the equivalant file for ubuntu?

---

### Post by GarethMB on 2006-11-10
It's hidden. You just need to type ```
vlc
``` into a terminal or a run dialogue

There should be a package in synaptic for inline use of VLC, maybe mozilla-plugin-vlc...

```
sudo aptitude install mozilla-plugin-vlc
```

You may need to have uni/multi verse

---

### Post by tubasoldier on 2006-11-10
All programs that can be executed simply by typing the name are all located in /usr/bin  

/usr is for the user files. These are files that the indidual users can use. crazy huh?
/bin is for the binarys. The executable programs.

---

### Post by dolphinsonar on 2006-11-10
> **tubasoldier said:**
> All programs that can be executed simply by typing the name are all located in /usr/bin  

/usr is for the user files. These are files that the indidual users can use. crazy huh?
/bin is for the binarys. The executable programs.I

THERE IT IS!!

Thanks!

---

### Post by localuser on 2006-11-10
> **dolphinsonar said:**
> How do I track down the "run" file for VLC?

To find any executable that's installed go to the command prompt and enter
```
$ whereis xxx
```

In this case you would substitute vlc for xxx in the code window.  If the executable is installed then its location will be displayed.

You will often find several entries returned from the whereis command

* "bin" directories are for "binary" files or executables
* "lib" directories are for "library" files where code procedures are generally stored
* "man" directories are for help files

---

### Post by digby on 2006-11-11
> **tubasoldier said:**
> All programs that can be executed simply by typing the name are all located in /usr/bin  

/usr is for the user files. These are files that the indidual users can use. crazy huh?
/bin is for the binarys. The executable programs.

If I may be annoyingly pedantic for a moment, /usr actually stands for unix system resources.


Also, using the which command will return only the locations of the executable files.  whereis will also return source and man page files.

---

### Post by dolphinsonar on 2006-11-11
Pedantics appreciated.  Thank you.

Is there a central list of these commands?  I am guessing there is a command on the command line that tells you what all of the commands are, but since the cart is pulling the horse, I don't know what that is.

> **digby said:**
> If I may be annoyingly pedantic for a moment, /usr actually stands for unix system resources.


Also, using the which command will return only the locations of the executable files.  whereis will also return source and man page files.

---

### Post by digby on 2006-11-11
> **dolphinsonar said:**
> Pedantics appreciated.  Thank you.

Is there a central list of these commands?  I am guessing there is a command on the command line that tells you what all of the commands are, but since the cart is pulling the horse, I don't know what that is.
If you google around for something along the lines of command line intro or bash intro, there are some good resources.  A lot of what I learned initially came from an [IBM resource]("http://www-128.ibm.com/developerworks/linux/lpi/101.html") and [this book]("http://product.half.ebay.com/Unix-System-Administration-Handbook_W0QQprZ68748QQtgZinfo") (half.com link where you can get it for less than $1).

---

### Post by mark_g on 2006-11-11
Thanks digby, I've been a linux user for a couple of years now. Always thought usr stood for 'user'. Your explanation makes a lot more sense though :)

---

### Post by JayTee on 2006-11-11
Suddenly I've become a big fan of pedantics.

---

