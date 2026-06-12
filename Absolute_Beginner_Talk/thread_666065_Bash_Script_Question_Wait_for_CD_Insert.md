---
title: "Bash Script Question: Wait for CD Insert"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by zds on 2008-01-12
Anyone know how I can get a bash script to wait until a cd is inserted before running the next command?

I've been searching for about an hour with no luck...

Thanks.

---

### Post by Xavieran on 2008-01-13
Simply add this before the command that you wish to be done after the cd is insterted...

```
zenity --question --title "Insert CD" --text "Please insert a CD into your CDROM drive"
```

Zenity is a simple gui maker for BASH scripts and other scripting languages...you can learn more about zenity by typing man zenity at a prompt...

P.S...You probably could add some sort of check to see if there is one in the drive but I haven't advanced to that stage yet...hope this helps though! :)

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html#sect_07_01_01]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html#sect_07_01_01")

And this should help you with your BASH scripting in general...

[http://http://tldp.org/LDP/Bash-Beginners-Guide/html/intro_01.html]("http://http://tldp.org/LDP/Bash-Beginners-Guide/html/intro_01.html")

This link contains stuff about using if statements to check for directories...leading us away from the annoying "I had the Disc in the drive before you asked me!!" sort of statements ;)

```
echo "Checking..."
if [ -f /media/cdrom/a-file ]
    then 
    echo "CDROM is in the drive"
    else
    zenity --question --title "Insert CD" --text "Please insert a CD into your CDROM drive"
fi

```

That should work...you might have to do a bit of debugging coz I haven't tested it...:)

---

### Post by zds on 2008-01-13
Well, ok that makes sense.

But how do I do it in just a shell (i.e., on a machine I'm ssh'd into)?

Thanks.

---

### Post by ac4000 on 2008-04-18
```

#!/bin/bash
NOCD=1
# Wait for CD
while [ $NOCD -eq 1 ]; do
        cdparanoia -qQ &> /dev/null
        NOCD=$?
done
# Proceed
echo "CD Inserted"

```

---

