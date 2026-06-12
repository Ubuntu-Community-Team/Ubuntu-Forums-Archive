---
title: "Argh!"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by capt_cope on 2006-05-11
Allright guys I've been searching the forums to the point of tears, and I just can't find this answer. I know it's probably been asked hundreds of times, but hey, what's one more time between friends? I'm trying to get my sound to work in et, but I can't edit the file I need to because I'm not root. I can't log in as root, though I've allready assigned a root password. When I try to log in as root I get a message "Root login not allowed" Is there some way to edit this file without root login? if not how do I allow root login?

---

### Post by aysiu on 2006-05-11
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by nanotube on 2006-05-11
hi
you use "sudo" to do things as root in ubuntu.
for more info, read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Sutekh on 2006-05-11
[Ubuntu Wiki - Root and Sudo]("http://wiki.ubuntu.com%5CRootSudo")

Just append **sudo** to the beginning of the edit command and supply your user password
```
sudo gedit /<path of file>
``` 
If you want to browse your files as root use this command from the Terminal
```
gksudo nautilus
```again providing your password.

---

### Post by capt_cope on 2006-05-12
The first guide got me what I needed, thanks a lot for the responses. I don't know if it's the fact that I'm running kubuntu, but gedit didn't do anything, just came back as no command.

---

### Post by mcduck on 2006-05-12
[QUOTE=capt_cope]The first guide got me what I needed, thanks a lot for the responses. I don't know if it's the fact that I'm running kubuntu, but gedit didn't do anything, just came back as no command.[/QUOTE]
sure, Gedit is the text editor used in Gnome desktop. With KDE, you need to replace the with some KDE editor (is it Kate?). Or use nano instead, it's command-line so it works with both ;)

---

