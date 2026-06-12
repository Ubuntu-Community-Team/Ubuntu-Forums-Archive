---
title: "Installing on Ubuntu makes me go ARGH!"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by selfmade on 2006-07-23
It took me two days to get automatix. i have synaptic. these things are supposed to make installing easier yes? im trying to install a skin for BMP. it is sitting in a gar.tz file on my desktop. and ive googled intallation instructions for such a file. nothing works. i keep getting these lovely errors telling me that the file imstaring at is not on my computer! somebody please help. except for these installation problems, im really enjoying my linux machine, but its not much good to me if i cant install the things i want.

---

### Post by shoot2kill on 2006-07-23
try going to your installation path for beep, then extract the gar.tz into the skins folder, i think (i used to winamp but i think it same)

---

### Post by selfmade on 2006-07-23
that was the first thing i tried. it says i dont have the permissions to do that...

---

### Post by Perfect Storm on 2006-07-23
copy the file to /home/username/.bmp/skins

---

### Post by christhemonkey on 2006-07-23
You need to do it in a terminal if the place you want to extract it to is not writeable by normal users.
```
gksudo file-roller ~/Desktop/bmp-skin.tar.gz 
```
Obviously replacing bmp-skin.tar.gz with the real archive name.

EDIT: Apparently its not. Do what Artificial-Intelligence suggested!

---

### Post by selfmade on 2006-07-23
score! thank you. is there a place where i can learn these commands all at once, or do i have to keep posting here and looking dumb?

---

### Post by T700 on 2006-07-23
Google, specifically the Google for Linux (see my sig) is your greatest tool to avoid looking stupid--at least it is for me.  [See here]("http://www.google.com/linux?num=50&hl=en&lr=&newwindow=1&safe=off&q=linux+commands&btnG=Search") for your question.

Paul

---

### Post by mlind on 2006-07-23
> **christhemonkey said:**
> You need to do it in a terminal if the place you want to extract it to is not writeable by normal users.
```
gksudo file-roller ~/Desktop/bmp-skin.tar.gz 
```
Obviously replacing bmp-skin.tar.gz with the real archive name.

EDIT: Apparently its not. Do what Artificial-Intelligence suggested!

You shouldn't extract anything on your $HOME folder using root privileges though..

---

