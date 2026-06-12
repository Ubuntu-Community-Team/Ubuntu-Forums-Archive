---
title: "Developing applications for Ubuntu"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by elygirang on 2005-09-29
:confused: 
 
Ok. So my brother received his copy of Ubuntu 5.04 from the mail and I got interested. Borrowed the CD, tried it at home, and found out that Ubuntu is the easiest-to-use Linux operating system I have yet seen so far.
 
I have been a programmer and I.T. Instructor for almost 15 years now but most of my development is done under the Windows platform. I am an absolute beginner in Linux, so I think it would take a while before I get used to Linux.
 
I need some advice from you guys on developing applications for Ubuntu, which I plan to release as FREE SOFTWARE (of course). I have read articles about different programming tools for Linux but have not decided yet which tool to use.
 
Does anyone know of a visual development environment for creating GNONE apps? I have heard of some such as Lazarus/Free Pascal (a Delphi clone) and Mono/MonoDevelop (a cross-platform .net environment).
 
Need help on this guys!

---

### Post by davmac on 2005-09-29
Have a look at Glade. There's a good primer/tutorial at [http://eddy.writelinux.com/](http://eddy.writelinux.com/)
It might also be worth asking this in the "Programming Talk" forum - although I'd put money on there being a couple of threads that cover this already...
HTH,
Dave Mac

---

### Post by paul.hendrick on 2005-09-29
Hi,
welcome to linux! :)
to start off with unix development, i'd always say start with python + glade.
glade is a gui designer which lets you place your buttons etc and then creates an xml file which is basically the layout of your application interface.
then with python (or any other language supported by libglade - there are lots) you can tell your program to use this xml and its widgets.
this site: [http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/)
has a good tutorial. it uses tepache - which is an addon for glade for code-generation. very good.

---

