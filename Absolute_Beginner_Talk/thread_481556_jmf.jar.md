---
title: "jmf.jar"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-06-22
Anybody know anything about this file.....supposed to add multimedia ability to Open Office presentations.

Like where can I get it and where should I put it?

Phil

---

### Post by dbbolton on 2007-06-22
> **groeswenphil said:**
> Anybody know anything about this file.....supposed to add multimedia ability to Open Office presentations.

Like where can I get it and where should I put it?

Phil
where did you read about this/find the file?

---

### Post by groeswenphil on 2007-06-22
From the Open Office forum.

I think its this posting.

[http://www.oooforum.org/forum/viewtopic.phtml?t=33131](http://www.oooforum.org/forum/viewtopic.phtml?t=33131)

I'll be honest......I copied it onto a post it note and left it on my desk for some time....busy at work.
Basically, I need to get videos to show in O.O. Impress.

Thanks,
Phil

---

### Post by steve.horsley on 2007-06-22
Google is your friend:
[http://java.sun.com/products/java-media/jmf/](http://java.sun.com/products/java-media/jmf/)

---

### Post by groeswenphil on 2007-06-23
Thanks Steve,

Now, I've got the mp3.jar thingy.....but my computer tells me that I don't have permission to copy the file into the java folder. How do you do that?

I think it should go into this folder.

usr/lib/jvm/java-1.5.0-sun/lib/ext

You know, inside the jvm folder I have what looks like four or five java runtime environments.

All the best,
Phil

by the way....I'm sure I recognise your name. You something to do with music?

---

### Post by dbbolton on 2007-06-23
> **groeswenphil said:**
> Thanks Steve,

Now, I've got the mp3.jar thingy.....but my computer tells me that I don't have permission to copy the file into the java folder. How do you do that?

I think it should go into this folder.

usr/lib/jvm/java-1.5.0-sun/lib/ext

You know, inside the jvm folder I have what looks like four or five java runtime environments.

All the best,
Phil

by the way....I'm sure I recognise your name. You something to do with music?
```
sudo mv /path/to/mp3.jar / usr/lib/jvm/java-1.5.0-sun/lib/ext/mp3.jar
```

---

### Post by steve.horsley on 2007-06-23
Minor correction (remove extra space):```

sudo mv /path/to/mp3.jar /usr/lib/jvm/java-1.5.0-sun/lib/ext/mp3.jar
```

Or to get a file explorer with full rights to the whole machine (treat it with care - it can trash your whole system), use Alt-F2 and enter the command gksudo nautilus. I'm guessing you would be happier using a gui.

---

