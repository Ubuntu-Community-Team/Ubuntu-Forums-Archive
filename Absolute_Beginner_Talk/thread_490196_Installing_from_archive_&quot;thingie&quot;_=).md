---
title: "Installing from archive &quot;thingie&quot; =)"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-07-02
If I download a file for Linux, it comes in a box icon. When I open it with the archive manager, I can do nothing to install the App. So, how do I install from the terminal. Also, how does one uninstall from the terminal?

---

### Post by lisati on 2007-07-02
It depends..... Have a look at [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html) - There are often instructions on websites that let you download stuff (but not always)

---

### Post by Seisen on 2007-07-02
You need to untar the file than find the either the readme file or the install file, there it will tell how to install the program. What program is it anyway?

---

### Post by rillip on 2007-07-02
Are you running KDE?  From the description this sounds like the archive manager.  If you right click on the file, then go down to the bottom, you might see something liike "install archive" or "install package."  Take a screen shot and post it so we know exactly what we're dealing with.

---

### Post by Akuma Shiro on 2007-07-02
No particular program, really. I d/l'ed a program before looking in the add/remove, and I couldn;t figure out how to install it. Like, I got the stellarium astronomy program from a friend (it was the Linux version) and I tried to install it, and couldn't find anything in the archive bin that would allow me to install it. So I looked in the add/remove (after deleting the archive bin) and it was there, so I got it that way.

I'm trying to learn as much as I can, so I can help others as you all are helping me.

---

### Post by Akuma Shiro on 2007-07-02
> **rillip said:**
> Are you running KDE?  From the description this sounds like the archive manager.  If you right click on the file, then go down to the bottom, you might see something liike "install archive" or "install package."  Take a screen shot and post it so we know exactly what we're dealing with.

Here are screen shots....
I downloaded Firefox.

Here are the right-click options...
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/install1.png[/IMG]

When I open with Archive Manager, this is what I get. It allows me to explore the bin.
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/install2.png[/IMG]
Couldn't find anything that says "install".

When I chose "Extract to Here" all it did was crate a folder.
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/install3.png[/IMG]

Once again, in that folder, no install option
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/install4.png[/IMG]

So, I'm wondering if I have to use the terminal and dabble in command line or something.

---

### Post by nitro_n2o on 2007-07-02
Well it seems that you have firefox :) 

anyways 
you can open to terminal and go to that folder that is: 

```
cd Desktop/firefox
```

then there should be a file called configure 

so type ```
./configure
```
then u make; type ```
make 
```
then u install; type```
 sudo make install
```

hope that helps

---

### Post by eternalsword on 2007-07-02
I'm guessing that's firefox precompiled.  You can run it by opening the firefox folder you have on your desktop and double-clicking the "firefox" icon, not the "firefox-bin" file.

---

### Post by nitro_n2o on 2007-07-02
> **eternalsword said:**
> I'm guessing that's firefox precompiled.  You can run it by opening the firefox folder you have on your desktop and double-clicking the "firefox" icon, not the "firefox-bin" file.

looool :) i didn't notice that... that's true, it's all .so files :D

---

