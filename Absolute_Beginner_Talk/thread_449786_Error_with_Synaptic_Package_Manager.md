---
title: "Error with Synaptic Package Manager"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-05-20
I just tried to run the Synaptic Package Manager, I entered my password and got this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This was working as of yesterday. I took a guess and typed "dpkg --configure -a" into the terminal, but I ended up with this message, "dpkg: requested operation requires superuser privilege." I don't know what this means or if I even did what I was suppose to do.

---

### Post by Moop on 2007-05-20
Super user means you need to type sudo before your command. So you would type 
*sudo dpkg --configure -a* and enter your password when it asks.

---

### Post by PMatt on 2007-05-20
> **Moop said:**
> Super user means you need to type sudo before your command. So you would type 
*sudo dpkg --configure -a* and enter your password when it asks.

Thanks, but I ran into another error when i typed that in (something with Java). I want to see if I can figure it out before I post what it was.

---

### Post by PMatt on 2007-05-21
[[IMG]http://img258.imageshack.us/img258/5549/screenshotapplyingchangcj3.th.png[/IMG]](http://img258.imageshack.us/my.php?image=screenshotapplyingchangcj3.png)

I get that message and then this pops up after I abort:

E: sun-java6-doc: subprocess post-installation script killed by signal (Interrupt)

I assume that I need to install a certain java file, but I'm not really sure which one it is. Can someone help me out? Here's the link:

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by PMatt on 2007-05-21
I'm not quite sure which file to download. Can anyone help me out?

---

### Post by glennric on 2007-05-21
> **PMatt said:**
> I'm not quite sure which file to download. Can anyone help me out?

You shouldn't have to download anything.  Try to remove and purge the sun-java packages and then reinstall them.  It is possible that a configuration script was corrupted.  You might need to clean out your apt cache in the case that it is a corrupted download.  I am assuming that you have the multiverse repositories enabled as that is where the sun java 6 packages originate.

---

### Post by PMatt on 2007-05-22
Why do I keep getting this error message? I think everything removed successfully, but the message even popped up as I was uninstalling Java.

---

### Post by PMatt on 2007-05-22
How do I get rid of this? I uninstalled Java and the message is still popping up on me.

---

### Post by Moop on 2007-05-22
I don't know how to get rid of that message or even what it means. I use Automatix2 to install java and most other non open source stuff. I've never had a problem with it.

---

### Post by zvacet on 2007-05-23
You didn´t accept Java EULA.Go to the synaptic and type sun in search box and after that select wich Java do you want.During the installation you have to accept Java EULA to go on with installation.So,you accept it and installation will complete.

---

