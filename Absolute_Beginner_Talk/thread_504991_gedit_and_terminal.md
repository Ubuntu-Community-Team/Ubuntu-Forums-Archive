---
title: "gedit and terminal"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-19
In terminal, what is the command to open gedit and still use terminal while gedit is open?

---

### Post by meierfra on 2007-07-19
gedit filename&

---

### Post by bodhi.zazen on 2007-07-19
You need a space between filename and the &

You can also 

gedit &

---

### Post by woodsonoversoul on 2007-07-19
cool. Thanks guys.

Question 2:
How do I save a file from gedit into a protected directory like var/www?

I'm trying to edit some files directly through terminal, prior to this I've been saving them on my desktop then copying them through terminal, which is a pain when you have to do it repeatedly

---

### Post by meierfra on 2007-07-19
If you start gedit with 
```
sudo gedit  
```(or sudo gedit filename) you can save the file anywhere you want to. 

But be aware of the security risks if you run a program as root.

For your web page you might consider keeping the files in /home/username/public_html. These files can be viewed on the web via 
```
your_web_ address/~username.
```

---

