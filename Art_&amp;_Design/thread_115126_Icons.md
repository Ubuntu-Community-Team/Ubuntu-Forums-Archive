---
title: "Icons"
date: 2006-01-09
forum: Art &amp; Design
---

### Post by leonneku on 2006-01-09
Hi,

How can i change the icons to my own googled icons?
When i go to the map where the default icons are stored and i want to add one of my own i get a message which say i don't have permission to add one and i must be root.

How can i become root for that map and why do i need to be root?I'm the only user on this laptop and i don't see why i have no full acces to everything.

I'm new to Linux so maybe this post is stupid but i hope somebody can help me.I searched a lot to find a answer but all i find is other nice things to change my desktop :D 

Thanks,Leon

---

### Post by endersshadow on 2006-01-10
Simply move it using sudo:

```
sudo mv /path/to/your/file.png /usr/share/pixmaps/
```

You don't have full access because it's a security risk.  Read up [here](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/) on why full access is such a bad thing :)

And you do have full access, really...it just makes you authenticate that you're you before it gives you it.

---

### Post by aysiu on 2006-01-10
See the third link of my signature.
You can also install icon themes locally. They'll appear in /home/leonneku/.icons

---

### Post by leonneku on 2006-01-10
Thanks,this will help me.I have some work to do now so i can't try it out.
I will read the articles later and i hope i get a better idea abaut the root.
I'll let you know if it worked and once i'm ready with all the changes i post a
screen of my desktop if your interested in that.There's nothing the same anymore since i installed Ubuntu last week ;) Even the speed of my laptop changed with all those nice things but i want to try everything before i seriously try to find a compromis between speed and "eye candy".

Leon

---

### Post by leonneku on 2006-01-10
It does not work with me :( 

The terminal says it's an unknown folder and can't move it.I also tried it with a theme from Fuscian to the themes folder.What am i doing wrong?I copied the text from the terminal so maybe someone can see what i'm doing wrong.

Here is the text:

leon@ubuntu:~$ sudo mv /home/leon/desktop/imageshack.png usr/share/pixmaps/
Password:
mv: cannot stat `/home/leon/desktop/imageshack.png': Onbekend bestand of map
leon@ubuntu:~$ sudo mv /home/leon/desktop/imageshack.png usr/share/pixmaps
mv: cannot stat `/home/leon/desktop/imageshack.png': Onbekend bestand of map
leon@ubuntu:~$ sudo mv /home/leon/desktop/imageshack.png usr/share/pixmaps/amsn
mv: cannot stat `/home/leon/desktop/imageshack.png': Onbekend bestand of map
leon@ubuntu:~$ sudo $#^&&@#@#$ grrrrr..... let this terminal explode hehehe
sudo: 0^: command not found
leon@ubuntu:~$

Thanks,Leon

---

### Post by aysiu on 2006-01-10
Try doing it graphically, then.
Alt-F2: ```
gksudo nautilus
``` This'll open a window with temporary root privileges. Just drag the icon into /usr/share/pixmaps.

---

### Post by endersshadow on 2006-01-10
Well, you can do gksudo nautilus...but you tried to move it to usr/share/pixmaps, and not /usr/share/pixmaps.  Remember the leading / and you'll be all set :-D

---

### Post by leonneku on 2006-01-10
:p Thanks :-) Reading was never my strongest side.
I go try it now the right way and the alt+f2 trick is also good to know.
The good thing is that all that playing in the terminal help me alot to understand things.In the beginning it was to much information but i think i get some grip on it now.

Thanks again and sorry for my stupidity 

leon

---

### Post by leonneku on 2006-01-10
Now my frog is in the pixmaps :) 

But it didn't work again in the terminal.I checked everything but it don't work.
Could there be a reason for or is it normal that these things sometimes not work?Alt+f2 was easy and i'm sure it will solve my problem with my desktoptheme.

Leon

---

