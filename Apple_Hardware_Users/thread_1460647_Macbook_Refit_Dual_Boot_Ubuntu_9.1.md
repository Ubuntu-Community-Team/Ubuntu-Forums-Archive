---
title: "Macbook Refit Dual Boot Ubuntu 9.1"
date: 2010-04-23
forum: Apple Hardware Users
---

### Post by irishrally on 2010-04-23
Hi, I'm completely new to Linux/Ubuntu but am eager to learn.  

I managed to install refit and ubuntu on my macbook.  I figured out how to get wifi working but I can't seem to see all the files on my "Macintosh HD".  I made sure to check my user id and group id and tried the method in the sticky to change user id and group id.  It seemed like I was already logged in with the same ids.

I can see many of the folders on the OSX partition, "Macintosh HD" but I can't see most of the files.  I get a permission denied message.



:confused:

---

### Post by linuxopjemac on 2010-04-23
Apple made it hard to access your files. You should be able to see your stuff in the /user folder of your own if yur uid is the same.

[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94)

---

### Post by irishrally on 2010-04-23
> **linuxopjemac said:**
> Apple made it hard to access your files. You should be able to see your stuff in the /user folder of your own if yur uid is the same.

[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94)


Ok thanks, between the two links I got it to work.  But now I have my original username, one named temp, and a third one I created after reading the second link method.  The third one lets me access my files.  Can I delete the first two usernames and change the third username to the one I had for the first one?

---

### Post by linuxopjemac on 2010-04-23
so you only want to change your name and keep your uid ?

---

