---
title: "ubuntu, linux, and networking"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by AndEat on 2006-02-25
A big fan of Ubuntu and never looking back to the window (unless I have too.....) I'm looking for more information and thought I would ask here. So a few questions....

1. Where can I find complete and detailed information on how linux (and Ubuntu) networking works? From A - Z. Parts and whole. Top to bottom. This fits into the OS as a whole, which I've picked up quite a bit but am still in the dark about a lot of things.

2. Where can I find information on networking in general, outside of a course (which i have no time/money for right now anyway)

any suggestions appreciated. thank you! :KS

---

### Post by linuxusr50 on 2006-02-25
When looking at linux as a whole as a beginner, I found this guide to be a very useful reference.

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)


As far as networking goes, I used the MAN pages and google alot.  Networking itself is a very big topic and don't know how in depth you are wanting to go.

try ```
man -k network | less
``` from a terminal window to get a list of some more common networking tools.

---

### Post by cwaldbieser on 2006-02-25
[QUOTE=AndEat]A big fan of Ubuntu and never looking back to the window (unless I have too.....) I'm looking for more information and thought I would ask here. So a few questions....

1. Where can I find complete and detailed information on how linux (and Ubuntu) networking works? From A - Z. Parts and whole. Top to bottom. This fits into the OS as a whole, which I've picked up quite a bit but am still in the dark about a lot of things.

2. Where can I find information on networking in general, outside of a course (which i have no time/money for right now anyway)

any suggestions appreciated. thank you! :KS[/QUOTE]

For general netwoking questions, this site has some nice overviews (search for networking, ethernet, etc):
[http://www.howstuffworks.com/]("http://www.howstuffworks.com/")

---

### Post by AndEat on 2006-03-03
Thank you

Great start.........but I want to know more more more I suppose......to a great depth of knowledge, like how the OS itself handles networking....where all networking parts of the OS are.......hmmmm

any other suggestions by anyone greatly appreciated

---

### Post by Estariel on 2006-03-03
At what level do you want to start? Do you want to understand how the linux kernel sends IP packages? (no idea how)

If you want to start at a higher level, you could start by understanding the different protocols that can be used.

In a heterogeneous network (linux, windows, osx) often SAMBA is used.

I find their official documentation very useful: [http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

In a homogeneous Unix network, often NFS is used. I don't know anything about it, but I'd go from the wikipedia article and read the external links:
[http://en.wikipedia.org/wiki/Network_File_System](http://en.wikipedia.org/wiki/Network_File_System)

Hope I could help,
Estariel

---

