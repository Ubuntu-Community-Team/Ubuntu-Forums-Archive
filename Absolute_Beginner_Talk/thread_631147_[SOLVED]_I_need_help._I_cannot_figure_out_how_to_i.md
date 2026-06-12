---
title: "[SOLVED] I need help. I cannot figure out how to install third party software...."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by janesac1978 on 2007-12-04
I cannot make sense of how to download and run programs like adobe flash, Java and real time. The forum post and the Ubuntu help just confuse me more... I tried the download manager on he add and remove programs but it only allowed read only so it was no help. How do I do itÉ I am new to linux and I just cannot seem to figure it out Help me please...

---

### Post by harold4 on 2007-12-04
It sounds like you're looking for browser plugins.  The following will take care of flash and java for firefox.

```
sudo apt-get install flashplugin-nonfree sun-java6-plugin
```

---

### Post by frodon on 2007-12-04
I advice you to read thoroughly these 2 links :
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You should find almost all the answers to your questions in.

---

### Post by Sef on 2007-12-04
> adobe flash, Java and real time

Applications > Add/Remove 

Then change the default to 'All Available Applications'

Then just do a search for them:

Flash:  Flash

Java:   Sun Java 6 (select the top one)

Real:  Real Player?

As for installing in general,  read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by tact on 2007-12-04
I am not clear on what you tried and what is going wrong...  Try this:

You click on Applications menu, then Add/Remove .... ok?

Then a program called Add/Remove Programs comes up right?

In the search box type "ubuntu restricted"   (omit the quote marks)

Are you using ubuntu or kubuntu or ?

If its ubuntu then tick the box for Ubuntu Restricted Extras....  then click "Apply Changed"

Does this then download the software and install it for you?  If not what does happen?

---

### Post by janesac1978 on 2007-12-05
Thanks you guys are great......All your suggestions helped me a great deal to understand how UBUNTU works; answered all of my current questions and many of my future ones....

---

