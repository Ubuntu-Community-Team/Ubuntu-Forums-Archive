---
title: "folder permissions"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-03-27
I've been putting all my games into my /opt folder.  However it has permissions rwxr-xr-x and is owned by root with group root.

I've changed the permissions of files inside the /opt folder though to my user, but I'm just wondering... is there any harm in changing permissions and owner of the /opt folder?



Also, is it a good idea to put games there or is there a better place I should put them?

---

### Post by ahsile on 2008-03-27
opt is a fine place to put them. a better solution for the permissions may have been to create a 'games' group and add you and root to it. at least, that's how I would have done it....

---

### Post by forrestcupp on 2008-03-27
It's a lot safer to just make a place in your /home folder to put them in.  That way you don't have to mess with permissions, and you're not going to mess up something that may really need to use /opt.

---

