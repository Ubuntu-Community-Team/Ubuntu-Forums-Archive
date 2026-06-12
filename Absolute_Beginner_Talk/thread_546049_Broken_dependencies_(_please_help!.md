---
title: "Broken dependencies :( please help!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by 71CH on 2007-09-08
my computer is telling me that I have broken dependencies and told me to 'sudo synaptic'.  when I do that it tells me virtualbox needs to be reinstalled but that it can't find an archive for it.  I don't particularly need virtualbox.  is there a painless way of fixing all of this?  thanks.

---

### Post by Malta paul on 2007-09-08
Hi, An easy way to remove Virtual box would be : System>Administration>Synaptic Package Manager> Search.   Type in Virtual box then when found right click on the 'Green boxes" related to virtual box, and 'Mark for removal'
Hope this is of help:wink:

---

### Post by 71CH on 2007-09-08
problem is i can't even open up synaptic because of this problem

---

### Post by 71CH on 2007-09-08
please help

---

### Post by Malta paul on 2007-09-08
I had my Synaptic Package Manager get screwed up a while back, and reinstalled my system from the live disk after FIRST backing up my files!
One thing you could try is reboot in the 'Recovery Mode' from the grub menu. This may tell you what is wrong or even fix it. To enter graphic mode after the command prompt type "Exit'
Wish you luck:(

---

### Post by 71CH on 2007-09-08
i think i got more info
i tried to install virtualbox and it became all screwy
this is what i get in terminal when i type in 'sudo dpkg -r virtualbox'

keedai@keedai-laptop:~$ sudo dpkg -r virtualbox
dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox

can anybody help?

---

### Post by Malta paul on 2007-09-08
It may be an idea to see if you can find the Virtualbox folder and delete it.
Have a look in Places>Home folder then Ctrl-H to look at your hidden folders they will have a 'Dot' in front.
 Good luck:(

---

### Post by 71CH on 2007-09-08
nope :(

---

### Post by 71CH on 2007-09-08
fixed problem
this link helped

[http://ubuntuforums.org/showthread.php?t=531979&highlight=remove+virtualbox]("http://ubuntuforums.org/showthread.php?t=531979&highlight=remove+virtualbox")

---

### Post by Malta paul on 2007-09-08
Great news, well done:guitar:

---

