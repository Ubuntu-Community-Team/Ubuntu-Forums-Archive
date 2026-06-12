---
title: "Newbie wants file server and web dev server"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by EggplantMan on 2008-03-29
Hello, I'd like to setup a server at home for the following purposes:

File Server- to just store files like photos, videos, music, etc that can be accessed by my 3 home PCs (Vista and XP).

Web Development- I'd like to be able to also use this server for playing around with CMS's such as Joomla and Drupal. 

I've installed the Ubuntu Server in a Virtual PC to play around with but I'm a little lost without a GUI.  Is there a way to install a GUI for the Ubuntu server?  If not, can I do everything above with the Ubuntu desktop if there is an easy to install a LAMP solution?  Would Ubuntu desktop or server have the file server capabilities or would I need to install something like Samba?  

After living 15 years in a Windows world, I'd like to try out Linux solutions (and save some $$ too).  :)

Thanks

---

### Post by Joeb454 on 2008-03-29
If you want to install a webserver etc. Then install the server edition on a spare PC, and choose the components you want to install (LAMP etc.)

When all of this is done, log in, and run ```
sudo aptitude install ubuntu-desktop
``` :) Hope this helps

---

### Post by Vixis on 2008-03-29
choose what you want to install
> sudo tasksel

---

### Post by EggplantMan on 2008-03-29
Thanks Joeb454 and Vixis.  I'll try those suggestions this weekend.

---

