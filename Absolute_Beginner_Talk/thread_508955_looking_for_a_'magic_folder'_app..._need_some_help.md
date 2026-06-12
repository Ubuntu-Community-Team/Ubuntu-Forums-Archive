---
title: "looking for a 'magic folder' app... need some help"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by deezay on 2007-07-24
i'm lookin for an application that would reside on the desktop maybe in a taskbar or launch bar or something. but when you drag a certain file and release it on this app it will automatically send it to a folder of your choice.. aka a picture you downloaded that is saved onto the desktop from the web gets sent to a picture folder, music to a music folder, etc etc etc etc.. i know vista has something like this. it's called magic folder or something. i was curious if anyone knew of anything like this for linux. feel free to post with some links of your suggestions. thanks alot.

---

### Post by Gen2ly on 2007-07-24
I definitely like the idea!  If you want to learn basic programming you should learn to write a script for this.  It should be that difficult.  Just would have to specify file endings ".end" and a simple line to mv them to the folder required.

---

### Post by deezay on 2007-07-24
i messed with vb during a quarter at itt... and i dont really recall much of it. is this something that could be done with python? if it's nothing too difficult i may tinker around with it. anyone else?

---

### Post by Keen101 on 2007-07-24
the title "magic folder" caught my attention right away. :)

I haven't heard of anything like it before, but it sounds neat. It doesent sound that hard to make.


a script sounds like it might work, but I am not a programmer either. :D



good luck,

-keen101

---

### Post by Al3xK3aton on 2007-07-24
Can't you just make a shortcut to the folder and drag it there? Why do you need a program to drag-and-drop files?

---

### Post by grishenko2000 on 2007-07-24
I thought the idea was pretty cool so I hacked up a shell script that can work on the desktop.

just cut and paste the following into a text file
```

#!/bin/bash

while [ $# -ge 1 ];
do
    case $1 in
        *.mp3)
            mv $1 ~/Desktop/Music
            ;;
        *.jpg | *.gif)
            mv $1 ~/Desktop/Pictures
            ;;
        *.doc | *.txt)
            mv $1 ~/Desktop/Documents
            ;;
        *)
            exit 0
            ;;
    esac
    shift
done

```

then in change it to be excutable with ```
chmod +x (name of file)
```

then you can create a launcher on the Desktop and drag and drop files into it.

At this stage i cant get it working on a taskbar or anything.

you need to change the directories for the filetypes to where you want then and can easily extend the script for other file types by extending the case statement.

alternatively you could make it a cron job that runs every couple of minutes to clean up the desktop.

---

### Post by Gen2ly on 2007-07-25
Nice very well reasoned out.  I'm not sure you'd need more than that, thats perfectly resonable.

---

### Post by deezay on 2007-07-26
pretty nice, i appreciate the help guys/gals. i'll give this a whirl and see what all i can do with it. once again.. thanks!

---

### Post by deezay on 2007-07-26
seems as if there is a space in the file name it doesn't put it into a folder... i thought that '*' pretty much covered that. how can you you get this script to recognize a space so it will continue to the files extention? many thanks!

---

### Post by grishenko2000 on 2007-07-26
I dont know how i missed it ... its one of the main rules in shell scripting 101

to make it work with files with spaces just put " around every instance of $1.
i cant seem to find a simple way to make it case insensitive but you could modify it as follows.
```

case "$1" in
        *.[mM][pP]3)
            mv "$1" ~/Desktop/Music
            ;;

```

with square brackets and the upper and lower case letter.

if anyone has a simple way to make it case insensitive I would love to know about it.

---

### Post by b20963a2 on 2007-07-27
> **grishenko2000 said:**
> if anyone has a simple way to make it case insensitive I would love to know about it.

Can't you convert the filename to all lowercase (or uppercase) first and then pass it to your case statement?

---

### Post by grishenko2000 on 2007-07-27
yeah good point I was googling to make a shell script case insensitive when I should of thought about that.

so for those who still care about this thread.
```

while [ $# -ge 1 ];
do
    filename=`echo "$1" | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZ/abcdefghijklmnopqrstuvwxyz/'`
    case "$filename" in
        *.mp3)
           mv "$1" ~/Desktop/Music
            ;;
        *.jpg | *.jpeg | *.gif)
           mv "$1" ~/Desktop/Pictures
            ;;
        *.doc | *.txt)
           mv "$1" ~/Desktop/Documents
            ;;
        *)
            echo "not moving"
            exit 0
            ;;
    esac
    shift
done
```

---

### Post by sucius on 2008-06-29
I am not a coder, so I don't know if it is possible; but is there a chance to make this a screenlet?

---

