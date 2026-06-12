---
title: "help: Application opens, and suddenly disappears."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by tsa.web on 2008-04-18
I'm an absolute beginner with Linux, so give me a break. I want to learn, and we all have to start somewhere.

My problem is that whenever I try to play a video in Totem or VLC, the application will open for about 2 seconds, and then just completely disappear. When I run it via terminal, I get this:

taylor@linux:~$ vlc
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

I just installed ubuntu actually and I've been searching the web wondering what to do now as far as codec installation goes. I have installed some codecs and enabled the other repository areas. I'm thinking that maybe my problem is hardware stuff. If so, how do I fix that? Also, I installed the "GNUbiks" application, and it disappears as well, except it gives me a "Segmentation fault (core dumped)". Pidgen IM is doing the same stuff.

Obviously, I'm in desperate need of help, so any would be appreciated. Thanks.

---

### Post by Kevbert on 2008-04-18
First try a memory check (it's an option in Grub).  Assuming you installed via CD, is the CD OK ?

---

