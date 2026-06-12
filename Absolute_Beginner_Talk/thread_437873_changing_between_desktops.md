---
title: "changing between desktops"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-09
sorry if this seems more appropriately posted elsewhere...
i did, and as yet have not received a reply, so, here goes:
after posting here earlier about an old machine running slow with ubuntu, i got some suggestions re. Xubuntu, which i installed successfully and quite like;
however, i now have 3 desktop environments using up a wopping 6gig of precious 20gig space..
so, first question:
if i decide to go with, say, Xubuntu, how do i safely, cleanly get rid of the kde and gnome?

second question,
if i decide to keep one or both of these, how do i switch back and forth (is it necessary to go back to the login prompt all the time, or is there a sleeker way of doing it)

thx for those patiently reading and responding to these baby-steps type of questions,
bambino rufio

---

### Post by starcraft.man on 2007-05-09
> **rufi_dukes said:**
> sorry if this seems more appropriately posted elsewhere...
i did, and as yet have not received a reply, so, here goes:
after posting here earlier about an old machine running slow with ubuntu, i got some suggestions re. Xubuntu, which i installed successfully and quite like;
however, i now have 3 desktop environments using up a wopping 6gig of precious 20gig space..
so, first question:
if i decide to go with, say, Xubuntu, how do i safely, cleanly get rid of the kde and gnome?

I'm pretty sure you can go, if you get errors there are supplemental commands to force it out (sometimes they just don't want to leave :p)

```
sudo aptitude remove ubuntu-desktop
```

```
sudo aptitude remove kubuntu-desktop
```

> **rufi_dukes said:**
> 
second question,
if i decide to keep one or both of these, how do i switch back and forth (is it necessary to go back to the login prompt all the time, or is there a sleeker way of doing it)

You can get a different log in screen from gnome look [here.]("http://www.gnome-look.org/index.php?xcontentmode=150") 

The GDM controls your log in screen and whats on it, so if you find one with sessions right on the front you will find it easier to switch. There is however no other way to switch to my knowledge other than log out and change sessions.

EDIT: Whuups, I just thought that if you remove both gnome and kubuntu you'll probably using xdm, I guess you'll have to google to find a new theme for that, I'm no xubuntu expert.

> **rufi_dukes said:**
> 
thx for those patiently reading and responding to these baby-steps type of questions,
bambino rufio

Your welcome, any more questions please feel free to ask :)

---

### Post by finer recliner on 2007-05-09
> **rufi_dukes said:**
> 
second question,
if i decide to keep one or both of these, how do i switch back and forth (is it necessary to go back to the login prompt all the time, or is there a sleeker way of doing it)



you have to go back to the login screen if you want to switch desktop managers. you can either log the current user out. or click switch user, and log in a second time on the same comp (but with a different desktop manager).

---

