---
title: "multimedia codecs"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Haus Neuerburg on 2007-07-15
Hi,
how do I check which codecs I've already installed? Where do they go to after sudo apt get(ting) them? Is there a simple native netry to display them?

---

### Post by Gausian on 2007-07-15
imo the easiest way is to open the synaptic package manager and do a search

---

### Post by felicity on 2007-07-15
You can also go to the menu Applications > Add/Remove, then choose 'Installed Applications' in the top-right corner, then choose 'Sound and Video' on the left-side.

---

### Post by Malta paul on 2007-07-15
System >Administration >Synaptic package manager, then search 'codecs' 
A good Reference:[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Have fun:o

---

### Post by Haus Neuerburg on 2007-07-15
no native entry? The Synaptic search did not really bring any light into the dark as it revealed that I've only 2-3 codecs installed, which can't be as I know I've installed more and it didn't show all available codecs either. I searched for "codecs" in Description and Name.
@ felicity: there's no add/remove in the xfce applications menu available....:-(

I'm using xubuntu dapper 6.06 and xfce desktop 4.2

---

### Post by Malta paul on 2007-07-15
when you look at the codecs, click properties >installed files.
This may help you, I hope  :)

---

### Post by forestpixie on 2007-07-15
are you trying to find something particular - or just all of them?

---

### Post by Malta paul on 2007-07-15
If you are using Ubuntu 7.04 you could use: >Places >search for files, 
Then look for your codecs in 'File System'

---

### Post by forestpixie on 2007-07-15
or search in terminal for codecs

sudo updatedb
sudo locate <whatever>

I think the OP has dapper

---

### Post by Haus Neuerburg on 2007-07-15
@ forestpixie thnx sudo locate....was exactly what I was looking for: so I have a wonderful list and can see at one glance what is there and what isn't

how do I put "[solved]" before the title? with editing my first entry?
Rgds Haus Neuerburg

---

### Post by forestpixie on 2007-07-15
go to your first post and edit - then you used to go advanced and you can edit the title and click the resolved button - but it might have changed.

anyway glad it helped :)

---

### Post by Haus Neuerburg on 2007-07-15
'ta

---

