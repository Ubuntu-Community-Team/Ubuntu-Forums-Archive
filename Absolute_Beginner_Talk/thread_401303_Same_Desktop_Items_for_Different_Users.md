---
title: "Same Desktop Items for Different Users"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by berng on 2007-04-04
How can I put some items on a desktop so those items show on the desktop for all the Users?

---

### Post by hyper_ch on 2007-04-04
hmmm, probably the simples way to achieve this is symlinking....

- make a new "Desktop" folder in /home
- chmod it to 0777 (so all users can access it
- copy/move all your stuff there
- delete your desktop folder
- symlink it from your home folder (~) to the new one...

But there might be better options to achieve that :)

---

### Post by sirhalos on 2007-04-04
No what you want to do is go to /etc/skel and create a folder Desktop and in that folder create your desktop icons. You can easily do this by opening up a root Nautilus. Anything in /etc/skel gets created to a new user.

For more information on /etc/skel visit the link on Linux From Scratch [http://www.linuxfromscratch.org/blfs/view/stable/postlfs/skel.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/skel.html)

---

### Post by hyper_ch on 2007-04-04
sirhalos:

The way I understand it he wants to share stuff among the Desktop of different users... not having something initially upon creating a new user.

---

### Post by berng on 2007-04-04
Yes, set up some items so they are available for everyone but still allow individual users to have their own items. 
Won't the symlink answer will give every the same desktop items?

---

### Post by hyper_ch on 2007-04-04
then make a "shared" folder and symlink that...

---

