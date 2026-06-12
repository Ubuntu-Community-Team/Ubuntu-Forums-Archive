---
title: "Java just won't work"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by AutumnPhoenix on 2008-01-30
I am new to linux...xubuntu at that.  Java just won't work.  I tried to install it in terminal,[http://www.java.com/en/download/help/5000010500.xml#rpm](http://www.java.com/en/download/help/5000010500.xml#rpm) I tried to install it in the system --> add/remove

Java is "installed" in my menu.  And it's checked in firefox...I've rebooted firefox and my entire computer several times.

I've cleared the chache and all the other things even passwords. 

I've looked over all the "tricks" and I a)have done them b) don't understand them.

I just want to chat 

Currently when I run a java chat all I see is a grey box

---

### Post by emarkd on 2008-01-30
You don't have to do the manual install for java.

First, enable all the software repositories:
    1.  Launch Synaptic by clicking on System > Administration > Synaptic Package Manager
    2.  On the menu, select Settings > Repositories
    3.  Select all the boxes except Source code (unless you want that)
    4.  Click close
    5.  Back on the main Synaptic screen, Click Reload to update your local cache

Now you can use the search feature to find sun-java6 and install it

---

### Post by ubuntu-freak on 2008-01-30
Give my [how-to](http://ubuntuforums.org/showthread.php?t=661833) a go and get everything working. 
 
Remember to 
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Updates Firefox on what plugins you have.
 
Nathan

---

