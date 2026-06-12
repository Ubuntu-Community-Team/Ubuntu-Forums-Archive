---
title: "[SOLVED] What does kint?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by suweihsut on 2008-01-29
I saw "kinit:no resume image, doing normal boot..." in boot time, what is kinit? what can kinit do? Thanks.

---

### Post by suweihsut on 2008-01-29
I saw "kinit:no resume image, doing normal boot..." in boot time, what is kinit? what can kinit do? Thanks.

---

### Post by tgalati4 on 2008-01-29
Weak answer:  Kernel initial process--similar to /sbin/init which is the core process that runs linux.  When booting, kinit looks for a snapshot of RAM saved to disk (known as hibernate-to-disk).  If this disk image exists, kinit will load it into memory, if not, it will do a normal boot.

---

### Post by Ex-windows on 2008-01-29
Here is 1 page with a description. I typed kinit into yahoo there were several pages hopes this gets you on the path to fixnf things>

[http://java.sun.com/j2se/1.5.0/docs/tooldocs/linux/kinit.html](http://java.sun.com/j2se/1.5.0/docs/tooldocs/linux/kinit.html)

---

### Post by bodhi.zazen on 2008-01-29
threads merged, please do not make duplicate threads ;)

---

### Post by suweihsut on 2008-01-30
Ok! I get it.

---

### Post by suweihsut on 2008-01-30
I think you gave me the link containing  content that  is not the same as i am talking about.

---

### Post by Ex-windows on 2008-01-30
> **tgalati4 said:**
> Weak answer:  Kernel initial process--similar to /sbin/init which is the core process that runs linux.  When booting, kinit looks for a snapshot of RAM saved to disk (known as hibernate-to-disk).  If this disk image exists, kinit will load it into memory, if not, it will do a normal boot.

 I offered a way to find an answer ie heres a link and try search. 
Didn't think it a such a weak thing to do :confused:

---

### Post by tgalati4 on 2008-01-30
Sorry for the misunderstanding.  I meant that MY answer was weak, because I couldn't find a concise answer without posting the actual code--which would be gibberish to someone who didn't understand kernel programming.  The kinit under Unix is a different process for kerberos authentication (logins and passwords).

---

### Post by Ex-windows on 2008-01-30
Cool,  Hope I didn't come across as an A** Cuz I was feelin extremely stupid enuff after reading your post lol Especially since I checked 5 or 6 sites and they all said pretty much the same thing and Ii felt it was a valid link to provide. Which at this point in my linux carreer is The most I can offer in most instances and hopefully steer folks towards some info/help. Anyway Thanks for reposting, my self esteem has risin to new levels :lolflag: Take care

---

