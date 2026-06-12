---
title: "Problem with USB devices"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Cloudy on 2006-03-10
So, I have a Sandisk Cruzer Mini 1GB USB pendrive that I'd like to be able to use on my other system running Ubuntu. When I got the Cruzer Mini for christmas, it worked fine and whenever I put it in my other PC "Sandisk Cruzer Mini" would appear on the desktop as a drive and I could access it with no problems.

However, around the middle of February something happened and I'm not sure.. er, what, really. I put it in my PC as per usual and when I tried to access it I got "ERROR: Given UDI is not a mountable volume". 

I don't know what to do or what even may have caused this, anyone care to help?

---

### Post by rboss on 2006-03-10
Can you post the last few lines of /var/log/dmesg after you plugged in the USB device?

---

### Post by Cloudy on 2006-03-10
Probably not, 'cos I dunno how.. just go into /var/log/dmesg/ and .. open it with gedit?

:oops:

---

### Post by dvarsam on 2006-03-12
Just launch a Terminal window:

1. From the menu, select "Applications\Accessories\Terminal"

2. Type "cat /var/log/dmesg"

3. With your mouse, select the output you got.

4. From the "Terminal" window's menu, select "Edit\Copy"

5. And then "Paste" the output of "dmesg" into this Forum.

Then somebody could help you.

Good luck.

---

