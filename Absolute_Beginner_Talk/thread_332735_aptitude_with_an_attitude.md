---
title: "aptitude with an attitude"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mistypotato on 2007-01-06
When I do this....

sudo aptitude install m2300w_0.51.2_i386.deb



Any idea why aptitude would keep telling me this....

[SIZE="3"]Couldn't find any package whose name or description matched [COLOR="MediumTurquoise"]m2300w_0.51.2_i386.deb[/COLOR].deb[/SIZE]

even though the file is in the current directory?

Thanks

---

### Post by aysiu on 2007-01-06
Because it's not looking in the current directory. It's looking at your /etc/apt/sources.list sources.

If you want to install anyfile.deb, use this command: ```
sudo dpkg -i anyfile.deb
```

---

### Post by raul_ on 2007-01-06
Or just double click it

---

### Post by mistypotato on 2007-01-06
Thanks for the help....:-D 
Still didn't work :(  

[SIZE="3"]sudo dpkg -i m2300w_0.51.2_i386.deb

dpkg: error processing m2300w_0.51.2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 m2300w_0.51.2_i386.deb
[/SIZE]

---

### Post by Sasa_Ivanovic on 2007-01-06
maybe you misstyped the name, type only the part of the name and press tab

---

### Post by mistypotato on 2007-01-06
[SIZE="3"]When I double click on it, it starts going then blotto...end of fun :( 

It DOES say "all dependencies satisfied" whic I think is good?

Here's the error....

(Reading database ... 93685 files and directories currently installed.)
Unpacking m2300w (from m2300w_0.51-2_i386.deb) ...
dpkg: error processing m2300w_0.51-2_i386.deb (--install):
 trying to overwrite `/usr/share/foomatic/db/source/driver/m2300w.xml', which is also in package foomatic-db
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 m2300w_0.51-2_i386.deb
e)
[/SIZE]

---

### Post by mistypotato on 2007-01-06
Anyone else got any ideas on this?

---

### Post by aysiu on 2007-01-06
That's a weird error. [This thread](http://www.ubuntuforums.org/archive/index.php/t-7435.html) may have some useful suggestions to try.

---

