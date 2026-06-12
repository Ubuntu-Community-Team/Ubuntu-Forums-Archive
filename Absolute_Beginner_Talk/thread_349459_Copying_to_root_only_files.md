---
title: "Copying to root only files"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-01-30
I recently installed wine on my ubuntu 6.06. I have to copy macromedia files to it in order to work with dreamweaver on my ubuntu, the prob is that the wine folder can not be copied to cuz only root has permission. How can i copy to it?
Thanks
:confused:

---

### Post by divague on 2007-01-30
Use the dreamweaver installer, it works with the latest wine.

---

### Post by ayed on 2007-01-30
So what your saying is that I should extract the .exe and run under wine exactly how?
Sorry I just dont understand what you are syaing.

---

### Post by PriceChild on 2007-01-30
I'm not sure why your wine folder would have root permissions?

You're meant to be working in your home dir?

do a```
sudo chown username:username -R /home/username
```replacing all instances of "username" with yours :)

---

### Post by jingo811 on 2007-01-30
I would try
Alt-F2
then type "gksudo nautilus" 
then manage my files the wreckless Windows way.  (Meaning that you'll break something important if you dunno what you're doing)
But it's a quick and lazy way of doing things.

PS.
by the way I dunno how Wine works so this might be a dangerous solution!

---

### Post by PriceChild on 2007-01-30
> **jingo811 said:**
> I would try
Alt-F2
then type "gksudo nautilus" 
then [COLOR=Red]**manage my files the wreckless Windows way**[/COLOR].Emphasis added!

Please don't do this... you will destroy something without realising.

---

