---
title: "How do I edit files as root?"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Tendril on 2005-11-26
I heard that Ubuntu was sticky with this.  I run gnome, and hoary heagehog, currently.  I wish to modify a file in Gnome Bittorrent.  

I have my root password, I just don't know how to log in.  I have tried from the loading screen, without success.  It says that a the system administrator can't log in, or something along those lines.  How would I modify download.py, if it can only be modified by root?  

Any help would be great.  And, step by step instructions would be heavenly.

 //Tendril

---

### Post by gord on 2005-11-26
in ubuntu you don't login as root to have root priviliges, you use 'sudo', its neat.

basically, when you want to run something as root, you ```
sudo <program>
``` and then type your user password when you get asked.

---

### Post by Brunellus on 2005-11-26
```
$ sudo <your text editor HERE> /path/to/file
```

---

### Post by tjfitz on 2005-11-26
Another option for you is to go to "Applications", "System Tools", "Run As Different User".  This is just a graphical way of using sudo.  I suggest running "nautilus" so you can open files as root, or run the editor you want to use directly.

---

### Post by Tendril on 2005-11-26
So, I should try:

```
$ sudo <ect/altenatives/gnome-text-editor> /usr/lib/python-2.4/site-packages/BitTorrent/download.py
```

??  I tried it, and the directory didn't exist.

EDIT:

Okay.  Problem fixed.  Thank you, so much.  I used the "Run as Different User", thing.  And, now my Bit Torrent Works.  Yeah! 

 //Tendril

---

### Post by gord on 2005-11-26
```
 sudo gedit /usr/lib/python-2.4/site-packages/BitTorrent/download.py 
```

no <> in there, sorry if it was a little bit confusing. if that doesn't work then that directory/file really doesn't exsist and you should check you have the right one :)

---

