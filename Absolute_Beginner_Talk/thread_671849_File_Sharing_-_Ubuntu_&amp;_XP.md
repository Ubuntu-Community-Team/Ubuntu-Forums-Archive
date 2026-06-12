---
title: "File Sharing - Ubuntu &amp; XP"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-01-19
My desktop is running Ubuntu 7.10 and my laptop is running Windows XP Home.  I have a Linksys wireless WRT54G router.  The desktop is connected via ethernet to the router and my laptop is connected via 802.11g.

In windows XP, under My Computer -> Properties -> Computer Name, I set my laptop's name to "poisontongue" and the workgroup to "Anarchia."

On the desktop, under System -> Administration -> Network -> General, I've set the Host Name to "Messiah" and the Domain to "Anarchia."  I have samba installed (and running).  At the command prompt, if I type smbd -V I see: "Version 3.0.26a." 

**Are these equivalent settings for windows/samba file sharing?**

On the laptop, if I go to "My Network Places," I see my local file shares on the laptop, but I do not see the file shares from the desktop.

On the desktop, if I go to Places -> Network, I can see my laptop and access all the files.

Back on the laptop, if I select "View Workgroup Computers" I see my laptop & I see Messiah (the desktop).  If I double click on the desktop, I get prompted for a username & password.

The username / password I use to log into my desktop normally does not work.  

**How do I configure a username and password for this, and is there a tutorial on the best method to do this?**

---

### Post by Nolander on 2008-01-19
[Here]("http://ubuntuforums.org/showthread.php?t=202605") is the tutorial i use.
hope it helps!

-nolander

---

