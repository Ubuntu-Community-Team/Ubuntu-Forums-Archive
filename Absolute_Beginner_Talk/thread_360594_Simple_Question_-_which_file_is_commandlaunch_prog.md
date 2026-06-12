---
title: "Simple Question - which file is command/launch program file"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-13
Simple Question - After you download and install a program, which file is the execute, command, launch program file??  Is it always in the same folder?  I can search and find the files but I don't know which one starts the program?  I wanted to make VLC my preference for playing MP3's and I can't find execute file

---

### Post by potterzot on 2007-02-13
executable files go in a few places:

/usr/bin
/usr/sbin
/usr/local/bin

etc...

one way to find the executable is to open a terminal and type what you think is the beginning of the command and hit tab

e.g. for beep music player: type be and hit tab.  This will bring up all possible end completions.  In this case, a bunch of beagle commands and beep-media-player, which is the one I want.

hope that helps

---

### Post by rggavubt on 2007-02-13
I know how to do that.  I am trying to make VLC my MP3 player in preferences.  You have to browse for the file that starts the program??

---

### Post by 23meg on 2007-02-13
It's *wxvlc*; quite an exception.

---

### Post by rggavubt on 2007-02-13
> **potterzot said:**
> executable files go in a few places:

/usr/bin
/usr/sbin
/usr/local/bin

etc...

one way to find the executable is to open a terminal and type what you think is the beginning of the command and hit tab

e.g. for beep music player: type be and hit tab.  This will bring up all possible end completions.  In this case, a bunch of beagle commands and beep-media-player, which is the one I want.

hope that helps

Do you mean hit the keyboard tab key when in the terminal?  I typed VLC and hit the tab key and nothing happened

---

### Post by rggavubt on 2007-02-13
> **23meg said:**
> It's *wxvlc*; quite an exception.

Thanks, I found it.

---

