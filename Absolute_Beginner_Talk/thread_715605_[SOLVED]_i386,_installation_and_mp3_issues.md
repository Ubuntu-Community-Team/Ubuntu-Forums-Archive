---
title: "[SOLVED] i386, installation and mp3 issues"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by wkck on 2008-03-05
Hello everyone,
Hopefully I'm not repeating too many posts, but I have a few issues I couldn't find an answer to already in the forum.

I did install today and update everything and some installations worked fine after that.  But I am still having some issues.

First, I cannot get my mp3s to play.  I uninstalled the default player in hopes of finding another one that would work--and they don't.  All of my other files are working fine (videos, pictures, documents) except for the mp3s which makes me think it was the player.  It seemed like it wasn't actually importing the files--thus the not playing.

Second, a lot of my downloads won't work when I try them, "Rhythmbox Music Player cannot be installed on your computer type (i386).  Either the application requires special hardware features or the vendor decided to not support your computer type." is the message I get.  That's coming up for a few programs.  

Third, a lot of programs won't let me download giving me the message:  "
This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.  Switch to the 'synaptic' package manager to resolve this conflict."

Any suggestions would be great!  Thanks so much,
Cat

---

### Post by oedha on 2008-03-05
you have to install ubuntu-restricted-extras

go to system - administration - synaptic
go to setting - repositories ( mark all boxes, close...reload )

then open terminal :
type :==> sudo apt-get update
type :==> sudo apt-get install ubuntu-restricted-extras
type:==> sudo apt-get install vlc

---

### Post by wkck on 2008-03-05
ok thanks! where do i find that?  I did a search in "add/remove applications" but nothing turned up.

---

### Post by oedha on 2008-03-05
on add/remove...make sure you search in all available applications

PS : read my previous post....i editted it :)

---

### Post by wkck on 2008-03-05
ok i'm getting this message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i was running the second line that you gave me and it stopped on the Java stuff, I think.

---

### Post by wkck on 2008-03-05
in fact... any time i try to run something that message above pops up.

---

### Post by kpkeerthi on 2008-03-05
What happens when you run
```
sudo dpkg --configure -a
``` from the command-line?

---

### Post by wkck on 2008-03-05
OK yes!  that "sudo" fixed it.  

i got a message that i had a broken package, followed by something else not being able to be installed...  i will be back tomorrow!!

thanks for your help so far!

---

### Post by oedha on 2008-03-05
broken package:==> system - administration - synaptic 
then ==> edit - fix broken packages

---

