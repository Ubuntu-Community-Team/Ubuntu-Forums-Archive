---
title: "Xubuntu"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by lynx2cross on 2006-02-02
I'm using Ubuntu but decided to try the xfce version and I love the way it looks and feels but I'm having problems such as my sound is not working, when I try to open word documents from the file manager it wants me to associate it with a program in order for me to open it (for some of you this sounds easy to fix but I'm new to linux).  My media files won't open and when I insert a cd it won't load it's like it doesn't even detect the cd drive.  Ubuntu worked right away I didn't have to really configure anything so this is a a bummer because I really like the feel of Xubuntu.

---

### Post by aysiu on 2006-02-02
I'd say the first thing you should do is Alt-F2 ```
gnome-volume-manager
``` and save your session when you log out.

---

### Post by lynx2cross on 2006-02-02
Ok I'll try that

---

### Post by lynx2cross on 2006-02-02
Ok I got my sound to work.  One thing I have noticed is that if I want to open a word document for instance I need to go into openoffice and then do file open and select the file I want and it opens with no problem same goes for media I have open up MPlayer and select the file I want in order to play it.  In Ubuntu I could just open the folder containing the file and open it from there.  Is there a way so Xubuntu can do that?

---

### Post by etc on 2006-02-03
What filemanager are you using?  I think the default is rox-filer
If it is all you have to do is set a run action for the file

Navigate to the file, right click -> File 'Name_of_file' -> Set Run Action
A dialog will come up, then if it's a word document enter 
```
oowriter2 "$@"
```
And click Use Command, it will remember to open that filetype with oowriter2 (openoffice).
Do the same with mplayer by selecting the filetype you want to open, set the run action by replacing 'oowriter2' with 'mplayer'

---

### Post by lynx2cross on 2006-02-03
That worked like a charm, Thank you.  If I need more commands for programs is there somewhere I can find that information or is it as simple as just typing in the name of the program, although the one for openoffice I would have never thought to use "oowriter2".

---

