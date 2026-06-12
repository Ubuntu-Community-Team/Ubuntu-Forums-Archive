---
title: "How to find an application's.... .exe equivilant?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2007-08-14
I'm trying to set my MP3's to play with a program other than VLC (which made itself default) but it isn't on the list of applications under "open with."

It's Listen Music Player, btw, but I need to know this process in order to change other file associations as well.  I got the player from add/remove applications - so I don't know where it installed to or anything like that.

I can get to a file browser to let me pick the application I want - but it's not exactly windows, and there aren't exactly .exe files.  So how do I go about finding "applications" in my file system?  I've searched for it's name and found a variety of files named "listen" in bin, usr, x11, etc.... but none of them will open the player when selected...

Thank you in advance.

---

### Post by tadada on 2007-08-14
try typing it's name in the terminal if it runs then create a launcher with the same text add a name and description and it should run then ( keyword is should (I no genius in Linux used windows as long as I could remember) I think that is the process)

---

### Post by raijinsetsu on 2007-08-14
If you're looking for a specific executable, in a terminal, type "which PROGRAM" where PROGRAM is any program you can run.
As for which program invokes your Listen media player, you should be able to find it in your Menu, and right click on it to find the path...

---

### Post by yellowband on 2007-08-14
you want to look in your filesystem's bin directories (binary files).

check out directories like /usr/bn /usr/share/bin etc

---

### Post by mikewhatever on 2007-08-14
Try using 'which' command.> which listen

---

### Post by imnotryan on 2007-08-14
Alright...

typing "listen" in terminal opens the program...

However when I go to "open with other" and "use custom command" and input listen.  It still does nothing, doesn't open the player, and with the player open, won't load the mp3 to it...

Do you guys think that my problem is that I still haven't found the "right" command to get it to launch by double clicking an mp3 file.....  Or am I having another issue that might be related to this specific program?

---

### Post by ugm6hr on 2007-08-14
> **imnotryan said:**
> Alright...

typing "listen" in terminal opens the program...

However when I go to "open with other" and "use custom command" and input listen.  It still does nothing, doesn't open the player, and with the player open, won't load the mp3 to it...

Do you guys think that my problem is that I still haven't found the "right" command to get it to launch by double clicking an mp3 file.....  Or am I having another issue that might be related to this specific program?

It is likely you have to put the full command in:
*/usr/bin/listen*

Typing a command in Terminal checks */bin*, */usr/bin* (and possibly others).  But *most* installed applications are in */usr/bin*.  Have a look for it there.

---

### Post by guguma on 2007-08-14
If it should play mp3 files and it does not. Then it is a codec problem, even though VLC plays them.

Also it seems that you may still not have not solved the association problem but I have no idea how to do it.

---

### Post by imnotryan on 2007-08-14
I'm starting to think in a new direction - the program will ONLY play a song that is in it's playlist...  Perhaps this program can not open and play an MP3 in the manner that I'm attempting.  Maybe it prefers to be treated like itunes - you open it - than select from it's library (which it does like itunes) a song.

So thank you guys for all the help, and it did not go to waste because now I know how to change other associations which I already just did (making swiftweasel default instead of firefox, now if only I could get swiftweasel to recognize my printer, that firefox recognizes)

I tried to get away from VLC because it pops and cracks while playing most of my MP3's but I think i'm just gonna go with yet another player.

---

### Post by ajgreeny on 2007-08-14
Right click on an *mp3* icon in *nautilus* and go to *properties* then the *open with* tab.  There you may be able to chose the default program to open the file type by marking the radio button displayed.

---

