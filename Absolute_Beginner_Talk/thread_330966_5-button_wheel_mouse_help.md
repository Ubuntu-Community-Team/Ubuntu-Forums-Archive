---
title: "5-button wheel mouse help"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by thaKing on 2007-01-03
i have a 5-button laser wheel mouse and i'm wondering if it is possible to use the two buttons on the side? i'd like to use them as Forward and Backward buttons while using Firefox...

---

### Post by zmuth734 on 2007-01-03
Here is what I used for my logitech mx 518 mouse to get the side buttons to work:
[http://ubuntuforums.org/showthread.php?t=327131](http://ubuntuforums.org/showthread.php?t=327131)

I recommend you find something like that for your specific mouse.  What mouse do you have?

---

### Post by thaKing on 2007-01-03
i have a M$ laser mouse, exact model i'm not sure (not sitting in front of the machine at this time...)

---

### Post by crispy_420 on 2007-01-03
I had luck with this one: [HERE]("http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx518").

Everything works fine for me but it killed the scroll wheel on my keyboard, a Logitech Elite keyboard. Still looking to fix that but no big deal for me.

---

### Post by zmuth734 on 2007-01-03
Here's a link to side buttons for 5 button mice in firefox...
[http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374)

Maybe when you figure out what mouse it is type it into the forum search with "side buttons" and see what comes up.

---

### Post by thaKing on 2007-02-02
ok, i've found my mouse type and followed the instructions listed here:
[http://ubuntuforums.org/showpost.php?p=1069100&postcount=5](http://ubuntuforums.org/showpost.php?p=1069100&postcount=5)

however, when i restarted X i got an error and now i can only log in with no GUI...how do i correct this? i assume (i'm a complete n00b with linux so bear with me) that i have control over everything just no GUI...if this is true i should be able to edit the files, etc...

**note:** the only difference between the linked article and what i did was in step 4...it says to edit the /etc/X11/imwheelrc/startup.conf file...however, i did not have the file but had this instead: /etc/X11/imwheel/startup.conf and used that file to edit instead..

---

### Post by h2gofast on 2007-02-02
For starters, before you do any editing of your xorg.conf file, you should back it up.  
Open a terminal window, gterm, xterm, aterm, it doesn't matter.
sudo cp    /etc/X11/xorg.conf   /etc/X11/xorg.conf.bak
Then if you make mistakes and are stuck at the command line because X won't start:
sudo cp /etc/X11/xorg.conf.bak    /etc/X11/xorg.conf  

Three ways to do this.  
One is to boot the livecd and navigate to the drive ubuntu is installed on.  On that drive you will find /etc/X11/xorg.conf and you can use gedit to put it back the way it was.  If you can figure it out from the post you tried this with.  The configuration file is case sensitive and must be word perfect or it will bork.

Two is at the login, simply login and 
sudo dpkg-reconfigure xserver-xorg 
Answer the questions as best you can, the defaults are usually fine, and it should give you a functional, but not necessarily optimized xorg.conf which will be in effect on reboot.


Thirdly, 
If you are going to edit X you might as well learn to use vi or vim because gedit is not available when X isn't running.  Old Schoolers like to debate the merits of vim versus emacs, or nano.  All are acceptable.  Here's how to do it in vim.

Login.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo vim /etc/X11/xorg.conf
type the letter "i"  this puts you in insert mode.  I'm assuming you have access on another machine to post here so you might be able to get an idea what you changed.  
Use down arrows to get to the line of text you altered, change them back.
Press the esc button.  
Type ":wq"
sudo reboot

Good luck.

---

### Post by thaKing on 2007-02-02
good news, i have a backup...i may not know much about linux, but i know to make backups... :)

i'll give that a try and let you know...in the meantime, if that code is supposed to work, why didn't it work for me? i have the exact same mouse as listed...

---

### Post by thaKing on 2007-02-02
restored backup file and now got GUI...thanks!

still would like to figure out how to get my mouse buttons to work properly...

---

