---
title: "GUI vs Command line"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Tomlin on 2007-03-18
I've been an Ubuntu user since 5.10 (but still consider myself sort of a noob). I've just built a new 'puter and installed 6.10 on it. I've always done the **unthinkable** and logged in as root. The main reason was the ease of use as far as the GUI was considered. I know a "REAL" linux guy/gal uses the command line, but it's nice to be able to dbl-click on a .gz file to extract it to where you want it, for instance.

Logging in as a regular user seems to render the GUI pretty much useless unless you know the name of the GUI app you want to use. Then, you can open a terminal and type in "sudo filename" and that gives you the rights you need.

As I said before, I still consider myself an "unskilled" linux user.

Is there something I can do as far as "permissions" to allow a regular user the option of using the GUI more? The above "application manager" is a good example, Where is that app (what is it actually called)?

I know I can open a terminal and type "**tar xvfz file.gz -C /directory**". The point is I like using the GUI far more than the CL.

Thanks

---

### Post by h0ax on 2007-03-18
Logging in as root is almost as insecure as wind0wz

That's the whole reason it's a problem in the first place, it defaults to giving the first account setup Administrator rights...

Linux is about the CL -> some like GUI better some like CL better - eh 

if you're logged in as a user and double click a gunzip file does it not just ask you for your password first?

---

### Post by 67GTA on 2007-03-18
You can right click on a tar file and select "extract here" without root privileges. You would do better to learn some terminal commands and use the su or sudo commands.

---

### Post by aysiu on 2007-03-18
> **Tomlin said:**
> 
Is there something I can do as far as "permissions" to allow a regular user the option of using the GUI more? The above "application manager" is a good example, Where is that app (what is it actually called)? Yes. This link will help you with that:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Tomlin on 2007-03-18
Thanks for the replies,

> **h0ax said:**
> Logging in as root is almost as insecure as wind0wz

That's the whole reason it's a problem in the first place, it defaults to giving the first account setup Administrator rights...

Linux is about the CL -> some like GUI better some like CL better - eh 

if you're logged in as a user and double click a gunzip file does it not just ask you for your password first?

No. It allows me to choose where to extract to (in this case /opt) which is NOT owned by the user, then gives an error. The problem is the owner is root.


> **67GTA said:**
> You can right click on a tar file and select "extract here" without root privileges. You would do better to learn some terminal commands and use the su or sudo commands.

Yes, that works, as long as the .gz file is in a directory owned by the user. When I typed **sudo cp filename.gz /opt**, then right clicked on the .gz file in that directory, it didn't give me the option to extract "here" because root owned the directory.

Usually, if I want to say, change a file owned by root, I'll fire up a terminal and type in sudo gedit. I type in the password and edit/save the file. However, if you don't know the actual name of the app your looking for, it's a little tougher.

Guess I'll just have to get used to the CL.

---

### Post by aysiu on 2007-03-18
> **Tomlin said:**
> 
Guess I'll just have to get used to the CL. Or you could read the link I posted before.

---

### Post by belikralj on 2007-03-18
I'm not sure what you mean. But from what I gather my advice is to run

sudo nautilus

and then rightclick on the file go to properties and change the read, write, execute permitions to allow other users  to use the file.

hope this halps

---

### Post by Tomlin on 2007-03-18
> **aysiu said:**
> Or you could read the link I posted before.

Thanks for the link. You must have posted while I was composing my response.

---

### Post by Tomlin on 2007-03-18
> **belikralj said:**
> I'm not sure what you mean. But from what I gather my advice is to run

sudo nautilus

and then rightclick on the file go to properties and change the read, write, execute permitions to allow other users  to use the file.

hope this halps

Doh!!!

That'll work!

Thanks

---

### Post by aysiu on 2007-03-18
> **Tomlin said:**
> Doh!!!

That'll work!

Thanks
Actually, that's not a good idea for two reasons:

1. You should use *gksudo* and not *sudo* with graphical applications. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2. Changing permissions and ownership on system files is a quick way to break your system. ```
gksudo nautilus
``` will allow you to move files around, copy them, delete them. But you should not change permissions or ownership on any directories you do not currently have access to.

---

### Post by Tomlin on 2007-03-18
> **aysiu said:**
> Actually, that's not a good idea for two reasons:

1. You should use *gksudo* and not *sudo* with graphical applications. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2. Changing permissions and ownership on system files is a quick way to break your system. ```
gksudo nautilus
``` will allow you to move files around, copy them, delete them. But you should not change permissions or ownership on any directories you do not currently have access to.

Agree on BOTH. I was thinking more along the lines of just being able to change files like "/etc/fstab" and "/etc/X11/xorg.conf". I don't change permissions (anymore - ended up re-installing once).

Good tip on the "gksudo" too.

Thanks again.

---

