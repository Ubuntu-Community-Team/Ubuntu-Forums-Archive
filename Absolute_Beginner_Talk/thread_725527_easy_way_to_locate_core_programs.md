---
title: "easy way to locate core programs??"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Shortspan on 2008-03-15
Just curious if anyone knows how to easily locate the core location of programs.  I would compare this to right clicking on a program (application) in Windows and getting *properties* and getting a complete directory tree to the location of the base program for editing (as in permissions, etc.)  I have also run into problems when trying to open a video and it asks to "open with".
If I try to chose another application (like vlc or gxine) rather than the default (mplayer) I have to find the base program to make the switch.  This can be frustrating, especially, when there are sometimes multiple files with the same name.  And they don't have extensions like exe. for easy identification.  I apologize if there is an obvious answer, but I haven't found it yet.  It could be in my manual "Beginning Ubuntu Linux" but I'm still looking.

Thanks.

Michael

---

### Post by Oldsoldier2003 on 2008-03-15
> **Shortspan said:**
> Just curious if anyone knows how to easily locate the core location of programs.  I would compare this to right clicking on a program (application) in Windows and getting *properties* and getting a complete directory tree to the location of the base program for editing (as in permissions, etc.)  I have also run into problems when trying to open a video and it asks to "open with".
If I try to chose another application (like vlc or gxine) rather than the default (mplayer) I have to find the base program to make the switch.  This can be frustrating, especially, when there are sometimes multiple files with the same name.  And they don't have extensions like exe. for easy identification.  I apologize if there is an obvious answer, but I haven't found it yet.  It could be in my manual "Beginning Ubuntu Linux" but I'm still looking.

Thanks.

Michael

```
which <programname>
```

---

### Post by jordanmthomas on 2008-03-15
This might be a good read for you:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

Basically, binaries ( or more correctly executables) are stored in folders like /bin, /usr/bin, /usr/local/bin, etc  
Configuration files are typically stored in /etc
General files programs use (like images and such) are in /usr/share

If you want to find where on your system a particular "command" is located, you can use something like this
```
which firefox
```
Which, on my system, is in /opt/mozilla/bin/firefox

Hope this kind of hekos, but I'm not 100% sure I knew what you were asking.

edit
I got beat :(

---

### Post by forrestcupp on 2008-03-15
Open up Synaptic and search for the package you want to know about.  Then highlight that package and push the Properties button.  Click the 'Installed Files' tab and it will tell you the directories that everything is in.

---

### Post by bruce89 on 2008-03-15
I don't see why'd need to know where the execuatables are. I assume this is something Firefox related.

---

### Post by Shortspan on 2008-03-15
Thanks guys;
   It looks like the "which" command seems to work.  But I was hoping for a much easier method, like one right click as in Windows.  At least I should be able to find the executable files.  
   When I'm online I may want to open a music file but a particular application (the default one) may not work.  Since I have other alternatives to open the music file to hear it I would like the option to "open with" a different program to see if it will read the music file and play it.  For some music or video programs I have downloaded tons of lib files to get the correct codec but without effect.  In Windows I usually just opened into another program to get it working.  Quicktime files are especially a pain.
  Anyway, thanks again.  And, I couldn't find the "which" command in the Ubuntu manual... go figure.  It has locate, find, and whereis but no which.

---

### Post by jordanmthomas on 2008-03-15
Do you mean something like this?
Right click a file and go to open other program.
Then it gives you a nice list you can choose from.

---

### Post by Shortspan on 2008-03-15
Jordanmthomas....
    Yeah... as in, Holy Ubuntu!  That's it.  Is that from Ubuntu or another distro?

---

### Post by Bubba64 on 2008-03-15
It is a standard right click open with other configuration the color is the desktop setup.

---

### Post by jordanmthomas on 2008-03-15
> **Shortspan said:**
> Jordanmthomas....
    Yeah... as in, Holy Ubuntu!  That's it.  Is that from Ubuntu or another distro?

It's not Ubuntu, but if I'm not mistaken there's no reason it wouldn't work the exact same way.

---

### Post by Shortspan on 2008-03-15
> It's not Ubuntu, but if I'm not mistaken there's no reason it wouldn't work the exact same way.

That's what I thought, but I can't get Ubuntu Mint to do it. 

 Maybe I'm just slow (alright, I "**am**" slow) but I can't figure it out.  I'm still curious. What distro is that?  I have about 20 to 30 distros lying around here.  It almost looks familiar.

---

### Post by jordanmthomas on 2008-03-15
> **Shortspan said:**
> That's what I thought, but I can't get Ubuntu Mint to do it. 

 Maybe I'm just slow (alright, I "**am**" slow) but I can't figure it out.  I'm still curious. What distro is that?  I have about 20 to 30 distros lying around here.  It almost looks familiar.

It's Arch, but how on earth can you tell what distro is being used by a screenshot?

---

### Post by forrestcupp on 2008-03-15
> **Shortspan said:**
> That's what I thought, but I can't get Ubuntu Mint to do it. 

 Maybe I'm just slow (alright, I "**am**" slow) but I can't figure it out.  I'm still curious. What distro is that?  I have about 20 to 30 distros lying around here.  It almost looks familiar.

Open up nautilus and find a media file.  Right click it.  The top of the menu should say 'Open with' and the default program.  Right under that should say 'Open with' and an arrow.  Highlight that and it should give you a list of programs that can open it, with 'Open with other application' at the bottom.  If you click that it should give you a window with all of your programs and an option to enter a custom command.

If you really don't have that, then right click the file and choose Properties.  In that window, there should be an Open With tab.  Click that and you can choose what program to open it with.

---

### Post by Shortspan on 2008-03-15
> how on earth can you tell what distro is being used by a screenshot?

By the Gui and icons. It has some features like other distros but I can't remember which one(s) (Vector, Goblin, or Zenwalk?).  The icons are softer.  Thanks for the reply.   Looking up the Arch Linux distro site, I see there are some add-on downloads for file utilities.  There may be something similar for Ubuntu or Debian based Distros.
Thanks

---

### Post by jordanmthomas on 2008-03-15
> **Shortspan said:**
> By the Gui and icons. It has some features like other distros but I can't remember which one(s) (Vector, Goblin, or Zenwalk?).  The icons are softer. 

Those are the default gnome icons and that's the same file manager Ubuntu / Mint use.  :o
The window manager is awesome if you care.  I can tell distros apart by their default themes, but certainly not one that's been customized at all.  You must have a sixth sense or something.  :lolflag:

---

### Post by Shortspan on 2008-03-15
I stand corrected.  I found a video file that I had on the hard drive in my file system and I did "indeed" get a drop down menu with other options to open the file.  My problem must be Firefox related entirely.  I apologize for bothering everyone.  I seem to be learning in baby steps.  
I do appreciate the info concerning the "which" command.

Thanks

---

### Post by jordanmthomas on 2008-03-16
Ah, you're having trouble getting firefox to use the correct program?
If you direct it to use gnome-open (which gnome-open will tell you where it is :) ) It will automatically use the right program to open files.

---

