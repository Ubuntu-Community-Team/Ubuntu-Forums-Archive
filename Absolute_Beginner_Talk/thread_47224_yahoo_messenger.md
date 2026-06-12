---
title: "yahoo messenger"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by kryptonite on 2005-07-07
im trying to install the debian version of yahoo messenger. ive saved the ymessenger_1.0.4_1_i386.deb to my pc. 
I have also typed dpkg -i ymessenger_1.0.4_1_i386.deb at root but i get this error message; 
dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ymessenger_1.0.4_1_i386.deb


im  a newbie and im absolutely clueless on how to proceed from here. 
Any help would be greatly appreciated

---

### Post by Kvark on 2005-07-07
One thing I'd try is "sudo alien --install file", it might work.

But have you checked out Gaim? ...it is installed out of the box, quite neat and can handle yahoo plus several other chat protocols.

---

### Post by kryptonite on 2005-07-07
Thanks, it works great ...

---

### Post by kryptonite on 2005-07-07
quick clarification about your first comment :
would this work
sudo alien dpkg -i ymessenger_1.0.4_1_i386.deb ?? 

my apologies if this sounds stupid

---

### Post by polo_step on 2005-07-07
[QUOTE=Kvark]But have you checked out Gaim?[/QUOTE]
I tried it and had a lot of trouble with it not keeping my settings.

I managed to get it to work by inputting them from the Gaim taskbar pulldown menu rather than from the menu on the running program.

Why the latter doesn't work, I dunno, but eveything seems OK now.

---

### Post by ozzie123 on 2005-07-08
Are you sure you downloaded the right debian file? Because I've just installed YMessenger and it works great (not as good as in windows though)

---

### Post by gammyhand on 2005-07-08
[QUOTE=ozzie123]Are you sure you downloaded the right debian file? Because I've just installed YMessenger and it works great (not as good as in windows though)[/QUOTE]
 Does yahoo messenger linux version support webcam?

---

### Post by byen on 2005-07-08
[QUOTE=gammyhand]Does yahoo messenger linux version support webcam?[/QUOTE]
 no... the linux version is a stripped down,lame and useless...i cant even voice on it either. sucks but ..oh well

---

