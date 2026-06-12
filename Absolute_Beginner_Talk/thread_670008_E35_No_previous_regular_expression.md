---
title: "E35: No previous regular expression ?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kiroro on 2008-01-17
I was following instructions and trying to install my 8800GT driver. 
I did this in the terminal:
sudo vi /etc/default/linux-restricted-modules*

Then a file was opened and i need to change DISABLED_MODULES=&#8221;" to DISABLED_MODULES=&#8221;nv&#8221;. However, when I tried to type nv or anything, an error occurs: E35: No previous regular expression... How am I able to edit that file? Many thanks!

---

### Post by kiroro on 2008-01-17
Problem solved! I learned how to operate vi through here: [http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

---

### Post by kpkeerthi on 2008-01-17
Vi is powerful. But you could always use a much simpler editor **nano** if you are kinda stuck.

---

