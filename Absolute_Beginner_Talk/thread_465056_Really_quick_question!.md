---
title: "Really quick question!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-06-05
does anybody know how to access a routers configuration remotely?? i have a linksys wrt54g.
locally i just have to type 192.168.1.1, but what about remote?

---

### Post by Corvinis on 2007-06-05
You have to configure this on the router first..... afterwards just connect to [http://youriphere:theportyouconfiguredhere](http://youriphere:theportyouconfiguredhere)

Fill in login data and you're done....

Quick and simple way to find out your external ip: [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by Rocket2DMn on 2007-06-05
In the router settings go to Administration and enable the radio button for Remote Management.  This is not recommmended as it opens up your router to anybody.
If you must, make sure you have a very good password.

---

### Post by adt41287 on 2007-06-05
is there any port setup by default? 
im at work and dont have local access to set it up.
thanks for the quick response!

---

### Post by Rocket2DMn on 2007-06-05
default port is 8080 I think.  Maybe you should enable https while you're at it.

---

### Post by Corvinis on 2007-06-05
Remote access isn't enabled by default

---

### Post by adt41287 on 2007-06-05
nice... ok thanks!!

---

### Post by Corvinis on 2007-06-05
Just a tip.... when you do enable it .... make it a good pass like rocket said... and use a random port if you can.... something like 23039 or whatever you can remember..... that way it's not as easy to discover

---

### Post by adt41287 on 2007-06-05
it wouldnt even let me access it without using secure :D
thanks for the tip!

---

### Post by AnRa on 2007-06-05
The password travels as plain-text so it doesn't matter how good it is, a man-in-the-middle attack is enough to steal it.

A better way would be to access to your machine via SSH and from there configuring the router.

---

