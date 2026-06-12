---
title: "Problem apt-getting stuff"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by PiratePhysicist on 2007-06-25
I have a server running version 6.06.1 of Dapper Drake and I wanted to get CVS running on it,however when I execute "apt-get install cvs" I get a prompt asking to insert the CD I used to install, my problem with this is that I don't have ready access to the server, and I had borrowed the CD from a friend I only see every other week at the most and is going to be going on vacation soon. Any suggestions as to how I can get CVS on to the box without the CD?

Thanks much.

---

### Post by eljalill on 2007-06-25
Hm, not sure about your settings there...
You have an internet connection, right?
And in synaptics, the online repositories are marked (checked)? Or they are in sources.list? CVS should be in one of the standard ubuntu repositories.
Because if I am not mistaken, you should be able to get all the packes that are on the CD from the online repositories also., and for me it is available through synaptics, without a CD.

---

### Post by PiratePhysicist on 2007-06-25
Yeah, I have an internet connection, I should've said, I'm ssh'ed into it from home, it's 8 miles away in the basement of a building I don't have ready access to. Which also makes it difficult for me to use synaptics :D

When I use apt-get it downloads something and then it unpacks it, and then asks for the CD.

Sorry for being ambigous before.

---

### Post by swoll1980 on 2007-06-25
try sudo aptitude install some-program maybe that will be helpful

---

### Post by eljalill on 2007-06-25
Hm, I am not sure why it would want the CD...

But you could download the CD-Image, and if you can't burn it, create a virtual drive in which you mount it.
... just an idea.

Although I am thinking there must be a more elegant solution to this... hm...

---

### Post by swoll1980 on 2007-06-25
apt-get is funny sometimes

---

### Post by PiratePhysicist on 2007-06-25
I'll save that as a plan B, not looking forward to lynxing my way around the interwebs for the CD-image :D

---

### Post by bigken on 2007-06-25
edit out the cdrom ## in the source list and use apttitude instead of apt-get

---

### Post by PiratePhysicist on 2007-06-25
Commenting out the CDROM line in the source list worked, thanks much!

What's the difference between apt-get and aptitude?

---

### Post by bigken on 2007-06-25
aptittude will install extras needed

---

### Post by swoll1980 on 2007-06-25
Your welcome

---

### Post by avik on 2007-06-25
> aptittude will install extras needed

I though apt-get did the same, unless I'm misunderstanding you...  Especially according to [this]("http://www.psychocats.net/ubuntu/aptitude").  Basically, at this point, aptitude and apt-get do more or less the same thing.

---

### Post by bigken on 2007-06-25
if you read it it says aptitude will remove depenancies were as apt-get wont so if you remove a program using aptitude its much cleaner

---

### Post by avik on 2007-06-26
Actually, the article says apt-get will also remove dependancies if you use sudo apt-get autoremove *packagename*.  At least if you're using edgy or later.

---

