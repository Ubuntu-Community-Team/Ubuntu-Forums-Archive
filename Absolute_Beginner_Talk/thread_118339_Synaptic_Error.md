---
title: "Synaptic Error"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-16
What's this.
I get it every time I start synaptic.

W: Couldn't stat source package list [http://kanotix.com](http://kanotix.com) ./ Packages (/var/lib/apt/lists/kanotix.com_files_debian_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kanotix.com](http://kanotix.com) ./ Packages (/var/lib/apt/lists/kanotix.com_files_debian_._Packages) - stat (2 No such file or directory)

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by jasmuz on 2006-01-16
Umm...you need to edit your /etc/apt/sources.list and eliminate those references...Why would you have 2 Kanotix repositories in Ubuntu?

---

### Post by Jaygo333 on 2006-01-16
[QUOTE=jasmuz]Umm...you need to edit your /etc/apt/sources.list and eliminate those references...Why would you have 2 Kanotix repositories in Ubuntu?[/QUOTE]

How do I edit them and frankly, I don't know what Kanotix is. Probably the other sources I had to add into sources.list to install FreeNX (which I have't gotten to work yet). 

How do I remove them.

:mad:h34r: Jaygo333 :mad:h34r:

---

### Post by newuser111 on 2006-01-16
sudo gedit /etc/apt/sources.list

and remove the lines with kanotix in them

---

### Post by Jaygo333 on 2006-01-16
Sanks.1?1
It worked. 
WoHoo... No more Errors.1?1

:p:h34r: Jaygo333 :p:h34r:

---

