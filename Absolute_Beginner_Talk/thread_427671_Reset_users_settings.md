---
title: "Reset users settings ?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by MinstrelBoy on 2007-04-29
Hi there
Got Ubuntu 7.04 working fine, even the wireless network (3Com 3CRUSB10075 just works as soon as you plug it in £8 from eBay) 
My problem, well actually my sons, is that he fiddled around with the users settings privileges and now nearly all the administration menu has disappeared, add/remove is gone, and theres no shutdown option on the Quit window.
I think he might have unticked Administer the system from the User Privileges.
So the question is, is there an easy way to reset his users settings, to restore things to normal, or will we have to re-install Ubuntu ?
Thanks
MinstrelBoy

---

### Post by oilchangeguy on 2007-04-29
since there's no way to determine just what your son has done to the computer. your best course of action will probably be to re-install ubuntu.

---

### Post by Jeff24K on 2007-04-29
> **MinstrelBoy said:**
> 
I think he might have unticked Administer the system from the User Privileges.
So the question is, is there an easy way to reset his users settings, to restore things to normal, or will we have to re-install Ubuntu ?
MinstrelBoy

Is this one machine we're talking about, and do any other users have administrator rights? If so it's as easy as System > Administration > Users and Groups from a privledged account, selecting the account name, Properties, User Privledges tab, and fixing things up by making sure everythign is checked.

If this is a machine where your son was the only user/administrator and you haven't enabled root logins the fix is a little more complicated, but not awful. There may be a more graphical way using some sort of "recovery CD", but I would boot a live CD like Ubuntu Desktop install CD, mount your hard drive, and edit /etc/group to add your son's account name to the 'admin' group (group names are on the left, with the list of members of that group on the right). Save/exit and reboot and all should be well enough for your son to adjust the rest using the above menu selections.

---

### Post by Metacarpal on 2007-04-29
Another option:

Reboot.  When you see the message to press a key for the Grub menu, press it.
Select the option with "Recovery Mode" in it.

This will bring you to a command line.  Type:

```
usermod -G admin *username*
```
(replace *username* with your son's username)

Then do it again, only this time, type "adm" instead of "admin"

That should set him right up.

---

### Post by MinstrelBoy on 2007-04-30
Thanks for pointing me in the right direction.
I fixed the problem of most of the administration menu missing and add/remove missing by ...
When grub starts choose the recovery mode option.
type sudoedit /etc/group
changed the line   admin:x:117   to    admin:x:117:andy     save file, (andy is my sons username)  reboot all fixed.   Went into system, administration Users and Groups and re-setup his user privileges.

The problem with shutdown and restart missing from the Quit screen.
Go to system   administration   login window    local tab
put a tick in Show Actions menu

Happy boy, who was even happier when I installed Scribus DTP and Abiword.

---

