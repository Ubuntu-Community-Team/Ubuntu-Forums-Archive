---
title: "Installing files"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Katocan on 2006-04-28
Hey, how would I install a file which is on my computer, I wanna install flash 4 linux but can't find it Synaptic. So I downloaded it to my computer but can't figure out how to install it ](*,)

---

### Post by Jagot on 2006-04-28
[QUOTE=Katocan]Hey, how would I install a file which is on my computer, I wanna install flash 4 linux but can't find it Synaptic. So I downloaded it to my computer but can't figure out how to install it ](*,)[/QUOTE]

This is the way:

[http://help.ubuntu.com/starterguide/C/ch03s06.html#id2528834](http://help.ubuntu.com/starterguide/C/ch03s06.html#id2528834)

However, if you are interested in being able to install stuff manually then you can check these out:

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Katocan on 2006-04-28
Thanks for links.
I still need help with something though :(.

When I type
```
sudo make install
```

It returns an error saying
```
make: *** No rule to make target `install'.  Stop.
```

Anyone got any idea what this is?

---

### Post by yoink23 on 2006-04-28
Make sure you are in the right directory? (the one with the stuff to install)

---

### Post by Katocan on 2006-04-28
Yup I am.

---

### Post by yoink23 on 2006-04-28
sorry, probably a stupid question, but did you forget to type "make" before "make install" ?

---

### Post by Katocan on 2006-04-28
When I type make, this is displayed
```
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by yoink23 on 2006-04-28
Can you link to the file you downloaded?

---

### Post by Katocan on 2006-04-28
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by yoink23 on 2006-04-28
Ok, I'm not sure if you know this, so bear with me if I'm talking down to you.  Did you do this?
```
tar xjf f4l-0.2.1.tar.bz2
```

Since it's bzipped instead of gzipped it's necessary.  Or maybe you extracted graphically in which case we're headed down the wrong road.

Edit: just saw on their forum that you need to have the qt development files...try:
```
sudo apt-get update && sudo apt-get install qt3*
```

---

### Post by Jagot on 2006-04-29
Looks like you're building from source.  Make sure you have the build-essential package:

```
sudo aptitude install build-essential
```

---

### Post by Katocan on 2006-04-29
Hmm weird, I done what you guys said to do and it still dosn't work :(

---

### Post by Katocan on 2006-04-29
I still get the same errors as before, has anyone else got anymore advice on what I could do?

---

