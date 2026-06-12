---
title: "trouble installing a splash screen"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-02-22
Hey all
I'm trying to install this splash screen: [http://www.gnome-look.org/content/show.php?content=50468](http://www.gnome-look.org/content/show.php?content=50468)
with the walkthrough from the same site:  [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

when i enter '/usr/lib/usplash/usplash-theme-fingerprint.so'  in the terminal
i get this output: 
kaboom@kaboom-laptop:~/Desktop$ /usr/lib/usplash/usplash-theme-fingerprint.so 
10bash: /usr/lib/usplash/usplash-theme-fingerprint.so: cannot execute binary file

im fairly new to linux so it could have been a simple mistake earlier in the process, but i am pretty sure i got all the prior steps right.

my machine is a compac evo N620c and i'm running dapper
thanks in advance
chris

---

### Post by Stemp on 2007-02-22
> when i enter '/usr/lib/usplash/usplash-theme-fingerprint.so' in the terminal

Why are you entering this line ? It's not in doc.

---

### Post by kaboom on 2007-02-22
when i entered this line
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so 
/usr/lib/usplash/usplash-theme-fingerprint.so 10
it didn't seem to be doing anything so i was assuming it was split into two lines.  

thanks for the reply
chris

---

### Post by onlybui on 2007-02-22
Ya I would like to know how to install it cause the instructions dont seem to work....

have u tried this....?

[http://www.ubuntuforums.org/showthread.php?t=344033&highlight=usplash](http://www.ubuntuforums.org/showthread.php?t=344033&highlight=usplash)

---

### Post by kaboom on 2007-02-23
> **onlybui said:**
> Ya I would like to know how to install it cause the instructions dont seem to work....

have u tried this....?

[http://www.ubuntuforums.org/showthread.php?t=344033&highlight=usplash](http://www.ubuntuforums.org/showthread.php?t=344033&highlight=usplash)

i haven't tried it.  i ended up messing around with too many values and messed up my ubuntu to the point that it wouldn't boot properly; so i reinstalled and gave up on the splash screen.  maybe i'll have another go at it later.

---

