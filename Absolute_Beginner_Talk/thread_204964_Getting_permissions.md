---
title: "Getting permissions"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by qwew on 2006-06-27
From what I understand, when you install Ubuntu the first (in my case, only) account you make gets admin/root priviledges.

But when I try to, for example, delete some files from a folder (by doing **Places** -> **Computer** -> **Folder** and then selecting and pressing del, not using the terminal), it simply says "Cannot move "whatever" to the garbage because you do not have permissions to change it or its parent folder." When I look in Properties for that file it'll have the boxes on the Permissions tab grayed out, and it says the owner is root.

What am I doing wrong here?

---

### Post by 23meg on 2006-06-27
> What am I doing wrong here?You're probably trying to delete a system critical file / directory that's owned by root. What exactly are you trying to delete and why?

---

### Post by paulyche on 2006-06-27
No. The first account doesnt have root priviledges. To become root (be sure you want to do this) you have to run nautilus as the root user. You can do this by pressing alt-F2 and typing gksudo nautilus.

What are you tring to delete? Are you sure it's not important?

---

### Post by aysiu on 2006-06-27
The first account *does* have root privileges, but they have to be invoked properly:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by 23meg on 2006-06-27
[QUOTE=qwew]From what I understand, when you install Ubuntu the first (in my case, only) account you make gets admin/root priviledges.[/QUOTE][QUOTE=paulyche]No. The first account doesnt have root priviledges.[/QUOTE]The default user is a sudoer, which means it can elevate to root status with the "sudo" command.

---

### Post by nanotube on 2006-06-27
you are probably running into a 'sudo' problem.
please click on the link in my sig to go to the faq, and you will find some explanation about root permissions, etc.

---

### Post by paulyche on 2006-06-27
> The default user is a sudoer, which means it can become root with the "sudo" command.

True, but I've always found that a tricky distinction to communicate. I've always explained sudo to mean 'get the root user to do this'

---

### Post by aysiu on 2006-06-27
[QUOTE=paulyche]True, but I've always found that a tricky distinction to communicate. I've always explained sudo to mean 'get the root user to do this'[/QUOTE]
It's actually quite a bit complicated:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by 23meg on 2006-06-27
[QUOTE=paulyche] I've always explained sudo to mean 'get the root user to do this'[/QUOTE]That would be incorrect terminology, since root isn't really a user; it's just a status of exemption from all access restrictions. Note the substitute term "superuser", which also stresses this. 

Root is meant to be used sparingly, in a strictly controlled manner, hence the need for sudo. sudo is actually short for "superuser do"; thus "sudo foo" means "do foo as superuser".

---

### Post by aysiu on 2006-06-27
[QUOTE=23meg]That would be incorrect terminology, since root isn't really a user; it's just a status of exemption from all access restrictions. Note the substitute term "superuser", which also stresses this. 

Root is meant to be used sparingly, in a strictly controlled manner, hence the need for sudo. sudo is actually short for "superuser do"; thus "sudo foo" means "do foo as superuser".[/QUOTE]
Well, yes and no.

Root isn't a user you can log into with a root username and a root password (unless you enable these things), but if you run a process as *sudo* and then look at ```
top
``` you'll see those processes are being run by root.

---

### Post by 23meg on 2006-06-27
[QUOTE=aysiu]Root isn't a user you can log into with a root username and a root password (unless you enable these things), [/QUOTE]
The very fact that you can enable logging in as root means you have the privilege to become root.
[QUOTE=aysiu]but if you run a process as sudo and then look at "top" you'll see those processes are being run by root.[/QUOTE]I'd say not *by* root but *as* root, since, again, root isn't a user per se.

---

### Post by qwew on 2006-06-28
> **23meg]You're probably trying to delete a system critical file / directory that's owned by root. What exactly are you trying to delete and why?[/QUOTE]

Actually, I was just trying to remove some search engines from the firefox folder, as the plugin designed to do that doesn't work on the standard set of engines for some reason. Not exactly system critical.  said:**
> The first account does have root privileges, but they have to be invoked properly:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Thanks, that article explained alot!

---

### Post by aysiu on 2006-06-28
[QUOTE=qwew]Actually, I was just trying to remove some search engines from the firefox folder, as the plugin designed to do that doesn't work on the standard set of engines for some reason. Not exactly system critical. ;)[/QUOTE] Well, it's not system-critical, but it is system-*wide*, so you need root privileges for that.

Firefox has two sets of search plugins: one in /usr/lib/firefox/searchplugins, the other in ~/.mozilla/firefox/*profilename*/searchplugins.

The first is supposed to be standard for all users. The second contains the ones you added manually. In theory, this makes sense, but in practice... you don't always want the default search plugins on every account... or on *any* account.

---

### Post by qwew on 2006-06-28
Yeah, I noticed.

Anyway, it's sorted out now so thanks again. :)

---

### Post by dolphinsonar on 2006-08-29
> **aysiu said:**
> The first account *does* have root privileges, but they have to be invoked properly:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Once again, the winking cat has shown me the light.  I was in a cave, now I am in a meadow.  Thanks aysiu.  Cookies to you!

---

### Post by aysiu on 2006-08-29
Thanks, as long as they're chocolate chip cookies.

---

### Post by Toxicity999 on 2006-08-29
They're only Chocolate Chip with that special keebler night elf chocolate! (the blood elves have a version... but not the most tasty...)

O.P.: For future reference you can also own specific files or directorys with chown. Use this only on non system critical things! And to everyone else I always thought os someone with sudo powers as all the magic powers of root with none of the hassle... in the sense that you have to think before you do things that much longer... I suppose that's an odd way to look at it, but I try... heh.

---

