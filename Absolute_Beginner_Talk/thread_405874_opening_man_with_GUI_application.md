---
title: "opening man with GUI application?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by proalan on 2007-04-10
Quick question regarding the manuals accessed via the 'man' command via the terminal 

e.g.

```
man bluefish
```

is it possible to pipe this command so that the manual can be viewed in a suitable GUI viewer?

---

### Post by lamalex on 2007-04-10
there's probably a better way to do it, but you could do
```
man bluefish > bluefish.txt and then open it with text editor
```

---

### Post by proalan on 2007-04-10
well that was my initial thought, 

I suppose my real question is if theres a suitable external GUI application I could use instead of just dumping it to a text file

---

### Post by mcduck on 2007-04-10
Just go to System/Help/System Documentation. Yelp handles both man and info pages. (Take a look at the left side of screen, 'Manual Pages" and "GNU Info Pages" ;)

You can open also open man pages in yelp by typing the 'man appname' into Yelp's search box. For example 'man imagemagick' opens Imagemagick's man page instantly.

---

### Post by proalan on 2007-04-10
> You can open also open man pages in yelp by typing the 'man appname' into Yelp's search box. For example 'man imagemagick' opens Imagemagick's man page instantly.

cheers mate exactly what i was after, just one of those things i forgot in my old age:oops:

---

### Post by ardchoille42 on 2007-04-10
You can open a terminal and do
```

yelp man:tar

```
and yelp will open and show the tar man page, but you can use any man page. This also makes it scriptable. Here's a script I just wrote for it
```

#!/bin/bash

myobject=`zenity --entry --width=200 --title="Manual Page" --text="Please enter a man page to open..."`
if [ $myobject != "" ]
then
    yelp man:$myobject
else
    exit
fi


```

You can save that bash script to any location, chmod it a+x and then make a launcher from it. Works great for a nice gui man page reader. I added a menu entry with "sh /path/to/yelpman.sh" so I can open it with the gnome menu.

---

### Post by vikram on 2007-04-10
If you use Konqueror(KDE filemanager) you can view man and info pages by typing :

man:/commandname
info:/commandname

many other similar plugins available

into the location bar

---

### Post by Endolith on 2007-12-07
What a great idea!  I hate command lines and their garbage interfaces.

[LIST=1]
[*]Open Deskbar Applet and type "yelp".
[*]Click the "Launch **Help**" option.
[*]Type the man page's name into the search bar and press Enter.
[/LIST]
It may find multiple related pages.  But what it *should* do:

[LIST=1]
[*]Open Deskbar and type the man page's name
[*]Select the "View Help for *manpagename*" option.
[/LIST]
Someone needs to write [a handler]("http://live.gnome.org/DeskbarApplet/Extending")!

---

