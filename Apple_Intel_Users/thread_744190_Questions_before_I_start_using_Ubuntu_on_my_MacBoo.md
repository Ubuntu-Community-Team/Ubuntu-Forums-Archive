---
title: "Questions before I start using Ubuntu on my MacBook Pro"
date: 2008-04-03
forum: Apple Intel Users
---

### Post by UFRaymond on 2008-04-03
Hello fellow linux users (maybe just mac users that are curious too),

As we speak i'm burning the .iso onto a 700MB CD to start using Ubuntu on my MacBook Pro via Live CD.  I'm not going to immediately install, I want to get a comfortable feel for the OS before I do something so drastic.

In the case I see Ubuntu fit to take up 10-20GB of my HDD, I'd like to have a few questions answered.

1)  How does one go about uninstalling Ubuntu?

2)  I'm looking for an IDE to program all types of C (C, C++, C#).  What are my best options?

3)  Is there a text editor for linux made for editing html, javascript, css, etc...

4)  This is the Mac related question...  How should I go about hooking up the newest models of Apple's wireless keyboards and their wireless apple might mouse (sp?) to my computer while running Ubuntu.

Thanks in advance!

Ray

---

### Post by Viro on 2008-04-03
> 
1)  How does one go about uninstalling Ubuntu?

The [Wiki](https://help.ubuntu.com/community/MacBookPro) contains all the information to get you started on installing Ubuntu on your Macbook pro.

> 
2)  I'm looking for an IDE to program all types of C (C, C++, C#).  What are my best options?
If you're learning to program, a text editor and makefiles serve you well. If you're set on learning to program with an IDE, go for Anjuta if you're using Gnome, KDevelop if you're using KDE. For C# development, MonoDevelop is the IDE to use.

> 
3)  Is there a text editor for linux made for editing html, javascript, css, etc...
Gedit does a handy job of editing most scripts. If you want a more web focused editor, you might want to give BlueFish a try.

> 
4)  This is the Mac related question...  How should I go about hooking up the newest models of Apple's wireless keyboards and their wireless apple might mouse (sp?) to my computer while running Ubuntu.


It's in the wiki. Try those steps outlined there, and if they do not work (quite unlikely, but still possible) come back here and get more help ;)

---

### Post by cyberdork33 on 2008-04-03
> **UFRaymond said:**
> 1)  How does one go about uninstalling Ubuntu? should be as easy as opening Disk Utility and removing the partition and resizing the OSX partition to take up the space (if on Leopard). On tiger this is not quite so easy...

> **UFRaymond said:**
> 3)  Is there a text editor for linux made for editing html, javascript, css, etc...There are MANY MANY different text editors available. You can even get into arguments about which is best. The default gedit is a good simple editor though and supports syntax highlighting.

> **UFRaymond said:**
> 4)  This is the Mac related question...  How should I go about hooking up the newest models of Apple's wireless keyboards and their wireless apple might mouse (sp?) to my computer while running Ubuntu.
They are just normal bluetooth input devices. Things are about to change a lot though as far as bluetooth is concerned when Hardy is released, and right now, it is not so good for Apple Wireless input devices.

Check the FAQ for an old guide to get things working now.

---

### Post by UFRaymond on 2008-04-03
> **Viro said:**
> The [Wiki](https://help.ubuntu.com/community/MacBookPro) contains all the information to get you started on installing Ubuntu on your Macbook pro.


If you're learning to program, a text editor and makefiles serve you well. If you're set on learning to program with an IDE, go for Anjuta if you're using Gnome, KDevelop if you're using KDE. For C# development, MonoDevelop is the IDE to use.


Hehe, I was asking about uninstallation but that's okay.  I previously installed Ubuntu on a PC, and had trouble uninstalling it.


You cannot program C, C#, or C++ to my knowledge with just a text editor ;]

Thanks though for everyone's help, I really appreciate it guys.

---

### Post by cyberdork33 on 2008-04-03
> **UFRaymond said:**
> You cannot program C, C#, or C++ to my knowledge with just a text editorIt depends what you mean by that... because you can write program code in those languages with just a text editor which many people do and use gcc to compile it.

---

### Post by morjava on 2008-04-03
> **UFRaymond said:**
> Hello fellow linux users 
3)  Is there a text editor for linux made for editing html, javascript, css, etc...



Thanks in advance!

Ray

gedit is a good text editor, it even has intelligent highlighting good for working with PHP but there are many more, amaya will let you edit the code and see immediate preview of results in the pane above the editor

---

### Post by Viro on 2008-04-04
> **UFRaymond said:**
> Hehe, I was asking about uninstallation but that's okay.  I previously installed Ubuntu on a PC, and had trouble uninstalling it.


I'm afraid there isn't any easy way of removing it. Disk Utility doesn't support merging partitions, though if you partitioned your hard drive in Boot Camp, you might be able to revert the changes.

> 
You cannot program C, C#, or C++ to my knowledge with just a text editor ;]


The most common way of programming on Linux (and even Mac OS X) is to type everything up in a text editor and then drop to the terminal and compile things with a command: gcc for C code, g++ for C++, mcs for C#, etc. 

Most of the IDEs I've worked with on Linux are a waste of time as they're too unwieldy.

---

### Post by cyberdork33 on 2008-04-04
> **Viro said:**
> I'm afraid there isn't any easy way of removing it. Disk Utility doesn't support merging partitions, though if you partitioned your hard drive in Boot Camp, you might be able to revert the changes.
Disk Utility on Leopard has a "+" and "-" button that you can use to remove or "add" a partition to the hard disk. You can also resize partitions there. No "merging" is required.

---

### Post by BIGtrouble77 on 2008-04-04
> **morjava said:**
> gedit is a good text editor, it even has intelligent highlighting good for working with PHP but there are many more, amaya will let you edit the code and see immediate preview of results in the pane above the editor

I use gedit myself for web development (ruby, xhtml, javascript, css).  I have mine loaded up with plugins and snippets.  I basically have a clone of TextMate.  Works really well for me.

---

### Post by hajk on 2008-04-04
As much as I hate to say this (being a vi-user), the OP should consider doing his programming in Emacs... As to the installing/uninstalling conundrums of GNU/Linux on an MBP, especially a recent one, why not install in a VMWare Fusion virtual machine? FWIW, I'm going to do just that on the new MBP I have on order...:guitar:

---

### Post by tchorix on 2008-04-05
I used Sourcenavigator for a while and I was quite happy with it.... now I'm in a different project where I'm just using vi and emacs (yes, I'm polytheist)... I tried Eclipse for developing some C/C++ projects, but it never worked out... it crashed too often...

If you want to follow the advice of hajk and use Emacs from coding on MacOS X, then, you better try Aquamacs... it's very well integrated with MacOs X

cheers
Tch

---

