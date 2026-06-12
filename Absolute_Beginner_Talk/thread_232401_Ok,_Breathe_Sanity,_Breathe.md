---
title: "Ok, Breathe Sanity, Breathe"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Geek Sanity on 2006-08-08
So far, in the last 24 hours, 

I have gotten XMMS working and able to play mp3's and ogg both.  

I have downloaded and installed Frostwire.  

I thought I had Java, I downloaded it from the sun Java site, and installed from the command line, it looked like it installed, but I still cannot do any of the Java related things (as for example, there is a board game I like to play online called Ticket 2 Ride, and I can't play because it won't recognize that I have Java installed) And Frostwire won't open/run.  Not even a splash page.  

So, how did you guys get Java working.  Oh, btw.  I am running Hoary, which has been working fairly well, until this.  How do I upgrade to Breezy and then Dapper if necessary?

---

### Post by Jagot on 2006-08-08
You may just need to select the correct Java version if you have it installed:

```
sudo update-alternatives --config java
```

---

### Post by Geek Sanity on 2006-08-08
Ok, which one:

> There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/kaffe/bin/java
      3        /usr/bin/java-sablevm
*+    4        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number:


---

### Post by Jagot on 2006-08-08
OK, that means you didn't get the Sun Java installed.  Read this:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Geek Sanity on 2006-08-08
Thank you, I am working through it as we type.

---

### Post by Geek Sanity on 2006-08-08
Do I have to have the SDK, or can I run without it?

---

### Post by Jagot on 2006-08-08
Unless you want to develop Java applications you don't need it.

---

### Post by Geek Sanity on 2006-08-08
Ok, according to the test page, it's working correctly.  Is that good?  It should be working for everything else, right?

---

