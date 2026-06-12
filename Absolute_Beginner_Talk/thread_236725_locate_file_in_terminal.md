---
title: "locate file in terminal"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-08-15
lets say i'm looking for the location of resolv.conf
how do I find it with the terminal?
I tried with 'find' and 'which' but both dont work
'find' does work when i'm in the right directory (/etc) but then i would realy need to look for the file if I know where the file is in the first place...

---

### Post by mcduck on 2006-08-15
'locate resolv.conf'

---

### Post by Klaidas on 2006-08-15
How about 
```
cd / && find -name resolv
```

---

### Post by Iowan on 2006-08-15
**find / -name resolv*** ???

---

### Post by Klaidas on 2006-08-15
No, I mean change directory to / and then find -name nameoffile

---

### Post by RichJacot on 2006-08-15
It appears either of the above approaches will work.  I use this method:

find / -name resolv.conf
or
find / -name resolv.*

The / says where to start looking, i.e. root.  If you knew it was somewhere down in /etc you could just do: " find /etc -name resolv.* "  Which would be much quicker.

Rich

---

### Post by anaconda on 2006-08-15
I usually use

whereis resolv.conf

---

### Post by kerry_s on 2006-08-15
I use the deskbar in the add to panel. You can do all kinds of things with that sucker, it can be used just like a terminal to execute commands, search files and folders, search the web with your browsers search engine, look up words in the dictionary, math, money conversion,etc.... It's really a much over looked app that is part of gnome.

---

### Post by seshomaru samma on 2006-08-15
Thank you all
I can now find files easily!

---

### Post by petersjm on 2006-08-15
```
locate FILENAME
```
This does it for me!

---

### Post by Kurt` on 2006-08-15
I've always used:

find / -name "blah"

or

find / -iname "blah" <- if you don't know the case, like "BlAh"

If you know what section a file is in (say, you're looking for a logfile in /var, replace / with /var in the examples above.

---

