---
title: "can someone tell me how to do this (text quoted)"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by thespinesplitter on 2005-10-06
> Jule Slootbeek wrote:

    Debian-users,

    another something i've been trying to figure out for a while.
    I have a nVidia GeForce MX 420 running the latest drivers, but whenever i try to run a opengl prog, like glxgears i get this:

jule@dolphy:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).



Make sure that the libGL.so.1 symlink in /usr/X11R6/lib
points to the real libGL.so.1.2 from nVidia (not the one
from the xlibs-mesa package).  I have had this happen to
me (though with the ATI drivers instead of nVidia) when
OpenGL apps would stop working after that symlink disappeared.


-Roberto Sanchez


how do i edit this????

plz, i think it can put and end to my forthnight-long quest to fix my ATI drivers

---

### Post by thespinesplitter on 2005-10-06
oh c'mmon

---

### Post by thespinesplitter on 2005-10-06
this is so frustrating, everything worx except 3D appz i've only tried OGL but that isnt doing to good as i said

---

### Post by Mustard on 2005-10-06
I'm not exactly sure, but I'm think it wants a soft link between the two files, which I would think you would create with a 'ln' command.  I'm not very experienced with using that command, so I wouldn't know for sure.

---

### Post by PsyberOneZero on 2005-10-06
I think he wants you to do someting to this effect:
```
#sudo ln -s /usr/lib/libGL.so.1.0.7667 /usr/lib/libGL.so.1
```
Keep in mind I'm using the 7667 nvidia driver from breezy, so check Syanptic for your version.  Also look in the Installed Files tab it will show you exactly what files are installed and where.

---

### Post by thespinesplitter on 2005-10-06
so how do i know which is the ATI libGL, im sure it is installed as easyubuntu2.3 installs the real ATI drivers

---

### Post by mlomker on 2005-10-06
> so how do i know which is the ATI libGL, im sure it is installed as easyubuntu2.3

Considering the number of posts that I've seen about 'easyubuntu' I'd say that it isn't quite so easy.  Are you using Hoary or Breezy?  Have you tried the built-in drivers?  Have you tried my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911")?

---

### Post by PsyberOneZero on 2005-10-06
[QUOTE=thespinesplitter]so how do i know which is the ATI libGL[/QUOTE]

Sorry, I misread the first post, but it's a similar process.

Do a search in Symantic for fglrx, if it shows up with a Green box, look in the installed files tab, there should be one of the file with libGL.so.1.xx.xxxx or a similar pattern just use that file to link to libGL.so.1 as in my first post.

If it's not installed, read mlomkers how-to

hell read it either way, it's really good for ATi poeple.

---

### Post by thespinesplitter on 2005-10-07
frankly im sick of it, i hear everyone whos using it and it does not work for me


edit: either...

---

### Post by mlomker on 2005-10-07
[QUOTE=thespinesplitter]frankly im sick of it, i hear everyone whos using it and it does not work for me
[/QUOTE]

What are you referring to?  I don't recall you asking for help with my how-to.

---

