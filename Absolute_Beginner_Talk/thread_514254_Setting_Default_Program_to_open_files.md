---
title: "Setting Default Program to open files"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-07-31
I Recently installed Ubuntu 7.04 and was wandering how I set default programs.
I really like XMMS since it's so much like winamp and would like my Music to
open within it.  Also streaming shoutcast streams as well. How do I do this.

Since I am new, I don't understand where everything is yet.

Thank you.....

I really like Ubuntu ( Best easy to use Distribution ever ) !!!!!!

---

### Post by Pragmatist on 2007-07-31
I'm assuming your using GNOME.  You should be able to Right-Click a file and select "Open With" and in the future you can just click the file and the chosen application will open it.

---

### Post by smartbei on 2007-07-31
For me sometimes that doesn't 'stick'. Here is what I do:
Right click on file -> Properties -> Open With -> Select the correct program or click 'add' to add an installed program to the list of options.

---

### Post by mcduck on 2007-07-31
> **Pragmatist said:**
> I'm assuming your using GNOME.  You should be able to Right-Click a file and select "Open With" and in the future you can just click the file and the chosen application will open it.

That only opens the file with your program this time. To set the default you need to do it like smartbei said. (Right-click -> Properties -> Open With)

---

### Post by Orbital75 on 2007-07-31
Thanks guys.... I tried that but XMMS isn't in the list to choose from only Rhythm Box.
I am familiar with Window where you can just manually find the file by going to where
the program is located....

Since I am unsure of Linux's file structure..... where do I go to point to it
var, mnt, ect, dev, lib    ???

Ubuntu loaded XMMS for me with Add programs and put it in some default location.......  
Sorry, I am a widows power user but am just beginning to understand linux....  

Thanks

---

### Post by mcduck on 2007-07-31
> **Orbital75 said:**
> Thanks guys.... I tried that but XMMS isn't in the list to choose from only Rhythm Box.
I am familiar with Window where you can just manually find the file by going to where
the program is located....

Since I am unsure of Linux's file structure..... where do I go to point to it
var, mnt, ect, dev, lib    ???

Ubuntu loaded XMMS for me with Add programs and put it in some default location.......  
Sorry, I am a widows power user but am just beginning to understand linux....  

Thanks
The easy way to locate the executable file for a program is the 'which'-command. For example, 'which xmms' would tell you full path to the executable of xmms.

Anyway, most of the time the executables for all your apps are in /usr/bin so in this case the full path for you would be /usr/bin/xmms. :)

---

### Post by Orbital75 on 2007-08-01
It was located right where you stated.

Thank you, that worked great........

---

