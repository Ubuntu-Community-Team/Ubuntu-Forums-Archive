---
title: "I was going to Play chess on Utunbu."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-12
and I was just looking around...and I found 3d option..

and when I pressed it, it says talk to administrator to install

 OpenGL Python bindings and the GtkGLExt Python bindings.

How can I install those...weird..things?

my VGA card is 7800 GT.

---

### Post by Campingman on 2007-05-12
I got 3d chess working a while back and wrote this in my notes as how I got it to work, I cannot remember exactly if they were in synaptic
Install python-gtkgltext1-1.1.0-2 feisty-i386.deb
Aptitude install python-opengl ([http://sourceforge.net/project/showfiles.php?group_id=5988](http://sourceforge.net/project/showfiles.php?group_id=5988))

This may help

---

### Post by rocketboys on 2007-05-12
> **Campingman said:**
> I got 3d chess working a while back and wrote this in my notes as how I got it to work, I cannot remember exactly if they were in synaptic
Install python-gtkgltext1-1.1.0-2 feisty-i386.deb
Aptitude install python-opengl ([http://sourceforge.net/project/showfiles.php?group_id=5988](http://sourceforge.net/project/showfiles.php?group_id=5988))

This may help

Thanks for the response!

but I don't really know what to do after I got to the site you told me.

which one do I have to download, and how do I install it..?

I'm really new to this..

:'(

---

### Post by Campingman on 2007-05-12
I am really sorry for being vague but It was a while ago.
python-gtkgltext1-1.1.0-2 feisty-i386.deb  is a deb package, I cannot remember where it was downloaded from, if you do a search for 3dchess on the forums you should find it (i must have found it this way), when downloaded just double click on it.

You can install the other in the terminal with the command
sudo aptitude install python-opengl ( i listed the link as an alternative)

---

### Post by Campingman on 2007-05-12
I have found that deb package for you
[http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)
download the feisty package and then double click, if all is ok it should install.

Hope all is OK

---

### Post by fenian on 2007-05-12
I used [this link]("http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/") to set up 3d chess.

---

### Post by rocketboys on 2007-05-12
> **Campingman said:**
> I have found that deb package for you
[http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)
download the feisty package and then double click, if all is ok it should install.

Hope all is OK

Thank you for the response, I finally got it!

:)

---

### Post by ubnewbie2 on 2007-05-12
and thanks for this thread - it got mine working too.

So, what is the best chess program for feisty anyway?

---

### Post by perce on 2007-05-12
> **ubnewbie2 said:**
> and thanks for this thread - it got mine working too.

So, what is the best chess program for feisty anyway?

Crafty is a good player I think; at least it always beated me badly ](*,) You can install also opening books for it fromm the repository. You need multiverse enabled because it's not completely free.

---

### Post by Enverex on 2007-05-12
Am I the only one that got a chuckle out of "Utunbu"?

---

### Post by rootkowski on 2007-05-22
Can you get this game work on feisty 64-bit? I've been trying different things, installed lots of libraries (from tarballs) still nothing. Any idea?

Thanks

---

