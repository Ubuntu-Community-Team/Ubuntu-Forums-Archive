---
title: "Where's the GUI?"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by thepcdoctor on 2005-08-30
I've installed Ubuntu and am stuck at first base. The install seems successful and PC boots to a login prompt. I enter username and password and then another command prompt that finishes with a $. Am I missing something here? What's happened to the desktop and how do I get there? Doesn't this load automatically? 

I'm totally new to Linux, but from what I have seem so far this seems a dog of an OS to use. ie  not at all intuitive/user friendly. Seems to be an OS for the real enthusiast.  ](*,)   Some gentle guidance to restore my initial enthusiasm would be welcome.

---

### Post by Lord Illidan on 2005-08-30
Calm down, mate..

First of all..

1. Is your graphics card an "NVIDIA" or an "ATI" card?
2. Did you perform a normal installation or a server installation?
3. Can you try logging in and then enter this simple command:

```
sudo vi /etc/X11/xorg.conf
``` 

It is case-sensitive so be careful about the caps-lock..


Try giving us the output.. We don't want the first four paragraphs.. Just scroll around until you see a section named driver. Give us the whole section.

To quit, press Escape, and then write ":q"

To shutdown, type ```
sudo halt
```

---

### Post by Gary Powers on 2005-08-30
[QUOTE=thepcdoctor]I'm totally new to Linux, but from what I have seem so far this seems a dog of an OS to use. ie  not at all intuitive/user friendly. Seems to be an OS for the real enthusiast.  ](*,)   Some gentle guidance to restore my initial enthusiasm would be welcome.[/QUOTE]

Try typing "startx" at that command prompt you're sitting at.  If you got a proper installation, that should take you to a GUI.  If that works, then you will have to edit the inittab in the /etc directory to ensure that it boots automatically into GUI mode. 

Just FYI, I've been using Ubuntu since the 1st of the year and several installations on four different computers (I like to play!) and it has never failed me.  In fact, every problem I've encountered was of my own creation :-)!

If you continue to have problems, please keep us posted and I am sure that the folks here can help you get it squared away.

Gary

---

### Post by Lord Illidan on 2005-08-30
[QUOTE=Gary Powers]Try typing "startx" at that command prompt you're sitting at.  If you got a proper installation, that should take you to a GUI.  If that works, then you will have to edit the inittab in the /etc directory to ensure that it boots automatically into GUI mode. 
/QUOTE]

Also, if typing startx gives you an error message, tell us what it is..

---

### Post by thepcdoctor on 2005-08-30
Thanks for your prompt replies
 
It's an ATI card
I've tried normal install and server install. Currently on server install.
Startx gives me '-bash:startx:command not found'
The sudo vi etc line brings up an E325 attention message. A page of text about swap file. Repairing or removing swap file then brings up a page of blue tilders (~) and locks keyboard.

Now what?

---

### Post by void_false on 2005-08-30
With a server install you dont get any GUI. Type in a console 
apt-get install ubuntu-desktop
or just reinstall you Ubuntu from scratch with **normal install**.

---

### Post by sneax on 2005-08-30
I'd suggest you completely reinstall and do a 'normal' install, to make sure everything you need is installed.

---

### Post by thepcdoctor on 2005-08-31
Thanks for your help guys. After the 5th install I finally got it running. The hangup seems to have been the network connection which was causing the 'normal' install to be incomplete.

---

