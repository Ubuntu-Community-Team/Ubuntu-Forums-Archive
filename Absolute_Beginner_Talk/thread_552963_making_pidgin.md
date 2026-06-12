---
title: "making pidgin"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-17
Hi, I was trying to "make" pidgin 2 after doing "./configure" and it gave me this error:

root@freddy:/home/nathan/Desktop/pidgin-2.2.0# make
make: *** No targets specified and no makefile found.  Stop.
root@freddy:/home/nathan/Desktop/pidgin-2.2.0# make install
make: *** No rule to make target `install'.  Stop.
root@freddy:/home/nathan/Desktop/pidgin-2.2.0# 

it looks pretty simple. The readme just says to type make :( but where is my makefile? How do I do this right?

sv

---

### Post by ruggrat on 2007-09-17
I'm a total n00b, but I just finished installing pidgin- this is what worked for me:

User srunni has a post [here]("http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin"), (I don't know how to link directly to the post, but it is #6 on that page), that lays it all out for you.

I had the same problem you did, I think, trying to ./configure from the start, but once I did tep one in the walkthrough I linked, it worked fine.  Only problem there is that it is: 

sudo apt-get install build-dep gaim

not:

sudo apt-get build-dep gaim

Hope this helps!

---

### Post by staticvoid on 2007-09-20
cool, thank you :). I officially dub thee no longer a n00b ;)

sv

---

### Post by tombott on 2007-09-20
You could always download a deb of Pidgin from [here]("http://www.getdeb.net/app.php?name=Pidgin")

---

