---
title: "Unix/Linux/Ubuntu noob question about scripts"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Radu43 on 2007-03-06
I need to run two commends to run my VPN client.
Is there a shortcut I can use to run this commends. 

1./etc/init.d/vpnclient_init start
2. vpnclient connect @@@@@@

:popcorn: 

thank you

---

### Post by maniacmusician on 2007-03-07
sudo /etc/init.d/vpnclient_init start && vpnclient connect @@@@@@@

Is that what you wanted?

---

### Post by Radu43 on 2007-03-07
> **maniacmusician said:**
> sudo /etc/init.d/vpnclient_init start && vpnclient connect @@@@@@@

Is that what you wanted?

this puts it in one line. which is great. 

But can I make it an icon on my desktop, so I just click and the commend gets executed?

Thanks you for your help

---

### Post by hscottyh on 2007-03-07
Paste this the text editor and save it to a file:
gksudo /etc/init.d/vpnclient_init start && vpnclient connect @@@@@@@

Then navigate to that file, right click and select properties. Go to the permissions tab. Check the box that says: "Allow executing file as program". You should then be able to double click on the file to run it.

You could also add this to your menu just as easy.

---

### Post by 3rdalbum on 2007-03-07
Right-click the desktop (or the panel and choose Add To Panel > Custom Application Launcher) and set the one-line command as the command to run in the launcher. Presto!

---

### Post by Radu43 on 2007-03-09
that is what i was looking for.

thank you

---

