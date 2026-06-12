---
title: "Can't find print server"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by phil.munck on 2008-03-16
The System>Administration>Printing cannot find the print server on my network.  I can ping the server and look at it by entering the IP address (192.168.1.202) into my browser.  Gutsy Gibbon does everything I need except print.

---

### Post by cmnorton on 2008-03-17
Where is the print server located and is it Windows, Linux, or something else. Try logging into the server with smbclient, and that will give you an idea of the settings you need. I strongly recommend using a browser with address localhost:631. You'll need to assign yourself admin privs first, and then give your password when prompted.

I have found using the CUPS configuration to be much easier than using the built-in printing configuration, although Ubuntu's is much easier to use than certain other distrobutions.

---

### Post by phil.munck on 2008-03-28
Thanks for replying.  You're at a level of competence that is beyond me.  How do you apply a smbclient and how is the browser involved?  I don't have any trouble accessing the Internet with several browsers (as long as I don't try to do it with wireless).
I'm pretty much resigned to having to use Windows if I want to do any printing at home.

---

