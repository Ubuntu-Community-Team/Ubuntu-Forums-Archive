---
title: "source.list file help"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by DarkOdysseus on 2006-09-12
I am trying to get the wxPython module. It says to put this in source.list:
    
    # wxPython repository on Starship
    deb [http://starship.python.net/crew/robind/wxPython/apt/](http://starship.python.net/crew/robind/wxPython/apt/) binary/
    deb-src [http://starship.python.net/crew/robind/wxPython/apt/](http://starship.python.net/crew/robind/wxPython/apt/) source/

and then follow some additional steps that I am familiar with. but all goes well until I try to save it. It says its read only and I cant do anything because I am not the owner. wtf.  Can someone please help a drastic noob in confusion. I love python but am very new to linux.

---

### Post by DSn0wMan on 2006-09-12
Try using sudo

sudo gedit /thepatheto/sources.list

---

### Post by jordanmthomas on 2006-09-12
Press Alt + F2
type
```
gksudo gedit /etc/apt/sources.list
```

This will allow you to edit the file as root (the owner of the file)

**edit**
beaten as usual

---

### Post by DarkOdysseus on 2006-09-12
I get the following error message:

could not save the file /ect/apt/sources.list.
Unexpected error: file not found

---

### Post by jordanmthomas on 2006-09-12
That's because it should be
/[COLOR="Red"]etc[/COLOR]/apt/sources.list

---

### Post by DarkOdysseus on 2006-09-12
its actually because I am retarded. lol
thank you very much. it worked beautifully

---

