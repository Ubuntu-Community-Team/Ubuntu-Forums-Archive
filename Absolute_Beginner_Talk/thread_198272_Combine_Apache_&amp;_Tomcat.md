---
title: "Combine Apache &amp; Tomcat"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-06-16
I have set up a website under the apache2, and it works well. Then I install tomcat5 to handle the JSP, but seems the apache and tomcat works independently. I wanna my apache server can handle JSP, I mean, I wanna apache automatically assign tomcat to handle the JSP.

I installed the libapache2-mod-jk2, and do some configure, but now I cannot access my apache server, no matter I add the port number to the URL or not. Seems like the tomcat conceal the apache.

---

### Post by jmguillemette on 2006-06-20
I too am looking to link apache and tomcat together.. I'll post here again when i have succeeded.

---

### Post by NeoRc on 2006-06-21
Actually, I have succeeded. But the next day when I open up my computer, seems everything changed back. And then I cannot fix it again.

---

### Post by killernurd on 2006-07-18
You installed libapache2-mod-jk ?

Followed the instructions in the Tomcat documentation?

EDIT: Boy, do I feel silly.
Sorry... missed that you had.

Also, for some reason, I had it working, and then it stopped working now... not sure why. We'll see, I suppose.

---

