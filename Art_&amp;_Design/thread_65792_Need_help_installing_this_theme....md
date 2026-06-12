---
title: "Need help installing this theme..."
date: 2005-09-15
forum: Art &amp; Design
---

### Post by ry_ry on 2005-09-15
Hi,

I'm trying to install this theme from gnome-look.org:
tAqua
[http://gnome-look.org/content/show.php?content=26990](http://gnome-look.org/content/show.php?content=26990)

I downloaded the compressed file but the install.sh shell script does not work in Ubuntu 5.04. I tried typing ./install.sh and ./install and I get an error message. I even tried double clicking the install.sh icon but it only opens in gedit instead of giving me the option of run. I tried dragging the compressed file into the Theme Manager but it gives an error of file invalid.

Any ideas how to install this theme? Will I have to do it manually and how do I do that? There's a brief comment on how to do it manually at that website but they don't provide enough details on which folders go where.

Thanks for any help.

---

### Post by krusbjorn on 2005-09-15
What is the error message you recieve?

Are you sure that install.sh is executable?
If not, in terminal:
chmod +x install.sh

---

### Post by ry_ry on 2005-09-15
Hey thanks krusbjorn!  :) 

That was it, the file permissions were not set to execute.

---

### Post by krusbjorn on 2005-09-15
Glad you got it worked out! :)

---

