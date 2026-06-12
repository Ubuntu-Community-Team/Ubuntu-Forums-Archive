---
title: "Mouse click and sound"
date: 2008-05-10
forum: Apple Hardware Users
---

### Post by Gamma6 on 2008-05-10
I have 2 issues. Firstly I'm using Ubuntu 7.10 on a MacBook Intel 2.0ghz 1gb ram 80 gb hd. I dual boot Mac OSX 10.5. 


Problem 1 - Sound doesn't work. Nothing at all. Tried many ways of fixing, but still no luck. My device choices are HDA Intel (alsa mixer) and Realtek ALC855 (oss mixer)

Problem 2 - Right click mouse with 1 button. Bet you heard about that one too many times before. I have tried to edit my system file, but it won't give me access to save (yes I'm admin on both os's)

---

### Post by Uinluan on 2008-05-10
I am having the same problem also.  This is the only problem I am having with this install.  I have tried all the different fixes and they have not worked.  I was hoping someone would have a new suggestions.  I have a 2.4 iMac 24" Aluminum

---

### Post by Uinluan on 2008-05-10
Sorry its late.  I re-read my post.  I am not having a problem with the right click because if you tap with three fingers on the mouse pad it works. My problem is actually on 8.04

---

### Post by Uinluan on 2008-05-10
Ok.. very late at night but this is when I do some of my best work.  As I have written above I was having problems with my sound on an iMac 24" Aluminum model.  I found this link 

[http://ubuntuforums.org/showthread.php?t=616845&highlight=intel+sound+problem](http://ubuntuforums.org/showthread.php?t=616845&highlight=intel+sound+problem)

With this link I was able to fix my sound problem in about five minutes.  I hope this can help someone else.  Again I am running 8.04 on a 24" iMac Aluminum

---

### Post by Gamma6 on 2008-05-10
Ok thanks I will see how it works!:)

---

### Post by Gamma6 on 2008-05-10
It won't let me save over it. Apparently I do not have the permissions. I'm admin too...:(

---

### Post by cyberdork33 on 2008-05-10
> **Gamma6 said:**
> It won't let me save over it. Apparently I do not have the permissions. I'm admin too...:(
how are you trying to do it? what commands are you running?

---

### Post by Gamma6 on 2008-05-10
I just tried to edit the file with a text editor.

---

### Post by Uinluan on 2008-05-11
You probably need to type

sudo gedit <filename>  

It will most likely ask you for your password

go in make your change and then save it

---

### Post by Gamma6 on 2008-05-11
Hmm not working. The file was edited but no luck. Volume controls to full. Is there any place I should be putting the code? I just put it from the first line...

---

### Post by Uinluan on 2008-05-11
Actually I put mine and the bottom of the file.  There was actually an entry there but it was the wrong one so I deleted it and put mine in, saved it, rebooted and everything worked after the reboot.

---

### Post by cyberdork33 on 2008-05-11
> **Gamma6 said:**
> Hmm not working. The file was edited but no luck. Volume controls to full. Is there any place I should be putting the code? I just put it from the first line...
you should be following the wiki page for your macbook. I am not sure which version you have, but the wiki pages are below:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

