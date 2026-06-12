---
title: "Kubuntu networking"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by Greyscalefox on 2005-08-20
Is this the right place for this?

I want to network 2 kubuntu boxes, both running kubuntu and via a cross-over cable. Help! I'm a newbie to Linux so no terminal commands (without explaining what the commands are at least). 

I'm sorry I'm being quite so useless. I kinda jumped into the deep end. I thought networking was a simple issue of plug in and go. Apparently not.

---

### Post by nemin on 2005-08-20
[QUOTE=Greyscalefox]Is this the right place for this?
[/QUOTE]Quite.
[QUOTE=Greyscalefox]I want to network 2 kubuntu boxes, both running kubuntu and via a cross-over cable. Help! I'm a newbie to Linux so no terminal commands (without explaining what the commands are at least). [/QUOTE]First, read a part of this site:
[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)
Then check if your network cards are detected correctly on both boxes. Next, set up a IP-address for each computer (they must be different!). You could use for example 10.0.0.1 and 10.0.0.2. How to do this, you can read on the link above.
[QUOTE=Greyscalefox]I thought networking was a simple issue of plug in and go. Apparently not.[/QUOTE]Often it is, though a direct connection between two compunters needs some more configuration.

---

### Post by Greyscalefox on 2005-08-20
I should have a 5 port hub arriving next week. How would I network it then?

(Its nice to see ubuntu forums help people on kubuntu as well. I had it in my head that it would be like asking M$ support to help with OS X)

---

### Post by Greyscalefox on 2005-08-20
[QUOTE=nemin]
Then check if your network cards are detected correctly on both boxes. [/QUOTE]
How?

---

### Post by Greyscalefox on 2005-08-20
I tried to enable the network connetions, they go green and then disable and go red. Whats going on?

---

### Post by Greyscalefox on 2005-08-20
Any one there?

---

### Post by nemin on 2005-08-22
[QUOTE=Greyscalefox]I should have a 5 port hub arriving next week. How would I network it then?[/QUOTE]
Plug normal UTP cables (*no* cross-over) from two ports of the hub into the two networkcards.

---

### Post by nemin on 2005-08-22
[QUOTE=Greyscalefox]How?[/QUOTE]
For me it's difficult to explain with a GUI: prefer the CLI for such things. Type in a terminal:
```
ifconfig
``` 
And post the output. What happens when you enter:
```
ifconfig eth0 up
```
Good luck.

---

### Post by nemin on 2005-08-22
[QUOTE=Greyscalefox]Any one there?[/QUOTE]Of course there's anyone here. At least, I am. Maybe you should be a little more patient ;-)

---

