---
title: "[SOLVED] How to make &amp;quot;shortcut&amp;quot; to a network drive?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by SherpaDoug on 2006-09-07
I just started using Linux on my home network where several home PCs access a common network drive.  I found the drive easily enough through places\network servers\Windows Network\Workgoup\drive\subdirectory. But I can't seem to create a "shortcut" to allow me to access this drive with only a few clicks.  If I right click and try Make Link I get *Error "Unsupported operation" while creating a link to "smb://<drive/subdirectory>"*.

Thanks,
Sherpadoug

---

### Post by meng on 2006-09-07
I don't know about "make link", but in GNOME if you are browsing files you can choose Places > Add to Places.

---

### Post by SherpaDoug on 2006-09-07
OK, it's stupid question time.
"choose Places > Add to Places."...How do I do that?

I am looking at a window in a program which help\About tells me is Nautilus 2.14.3 and is part of GNOME.  The main sub-window shows the subdirectories (folders) of the network drive.  On the left there is a sub-window titled Places that shows links to the Desktop and the local drives on the PC.  How can I add one of the network drive subdirectories as a new "Place"?

Sherpadoug

---

### Post by halitech on 2006-09-07
are you using gnome or kde?

in gnome, go to 

Places - connect to server

then select server type  as windows share

share and folder can be left blank

username - put in the network username

then click on connect and this will put an icon on your desktop that you can just doubleclick to open

---

### Post by SherpaDoug on 2006-09-07
Thanks, That is just what I needed!  I had been barking up the wrong tree.

Sherpadoug

---

### Post by halitech on 2006-09-08
glad to be of assistnace and glad it worked for you :)

ps, had to do it myself a few times to get the info correct ~L~

---

