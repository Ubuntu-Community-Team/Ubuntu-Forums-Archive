---
title: "What is the difference between sudo and gksudo?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Arazu on 2008-04-20
I've seen both suggested. I use sudo even though I'm not sure what it means. My noob self assumes it allows the execution of commands with root access.

---

### Post by SOULRiDER on 2008-04-20
sudo is for running command line applications.
gksu (its not gksudo) is for running applications with a GUI.

---

### Post by Oldsoldier2003 on 2008-04-20
> **SOULRiDER said:**
> sudo is for running command line applications.
gksu (its not gksudo) is for running applications with a GUI.

actually gksudo is a valid command. (its a link to gksu)

---

### Post by SOULRiDER on 2008-04-20
> **Oldsoldier2003 said:**
> actually gksudo is a valid command. (its a link to gksu)

I had no idea, thats good to know :)

---

### Post by Arazu on 2008-04-20
> **Oldsoldier2003 said:**
> actually gksudo is a valid command. (its a link to gksu)
Thanks. I was going to say that it works. 

But I'm still confused. I've read both for editing a file. For example:

sudo gedit /bob
gksudo gedit /bob

I don't get it. Can someone suggest a book?

---

### Post by Oldsoldier2003 on 2008-04-20
> **Arazu said:**
> Thanks. I was going to say that it works. 

But I'm still confused. I've read both for editing a file. For example:

sudo gedit /bob
gksudo gedit /bob

I don't get it. Can someone suggest a book?

when you launch gedit you should us gksu. normally its not an issue but in rare circumstances using sudo to runa graphical apllication can create a problem where permissions get messed up.

---

### Post by SOULRiDER on 2008-04-20
Check out [https://lists.ubuntu.com/archives/ubuntu-users/2008-April/141552.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-April/141552.html) and [http://linux.about.com/cs/linux101/g/gksu.htm](http://linux.about.com/cs/linux101/g/gksu.htm)

---

### Post by Oldsoldier2003 on 2008-04-20
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) gives a good rundown of the sudo vs gksu for graphical applications issue

---

### Post by PeterJS on 2008-04-20
Both work perfectly fine. The differences between sudo and gksudo is where it expects to receive the password from. sudo expects the password on stdin, ie keyboard input from the launching terminal itself. A purely graphical launcher, like a menu item, won't have an associated shell, so it will have no way of getting the password from the user. gksudo on the other hand expects a password in the graphical window that it pops up when it is launched. So you could run gksudo from a terminal, it'd be a little bit silly, but it would work no problems. gksudo's strong suit is that since it's graphical it doesn't depend on stdin, so if you create a menu item with gksudo, it will work exactly as you expect it to, it will graphically prompt for a password and then proceed.

---

### Post by Arazu on 2008-04-20
Thanks all. I'll look at that link. And I will use gksu when I edit a file. From now on. 

Thanks again!

Edit: Maybe not based on the informitave replys while I was posting this. Thanks all.

---

### Post by Arazu on 2008-04-20
Or not based on the very informative post above. 

Thanks again.

---

### Post by Oldsoldier2003 on 2008-04-20
There is a fairly large difference in opinion regarding th use of gksu vs gksudo. Honestly, I look at it like this- even though you can get away with launching graphical apps with sudo, sooner or later it will bite you in the rump. So I chose to use the proper command instead of falling into a bad habit that may eventually cause me grief.

Either way its a personal decision, and many people go through their Linux experience without ever experiencing an adverse effect from using sudo to launch a graphical ap. my motto in the end is "better safe than sorry".

---

### Post by joshrobinson on 2008-04-20
i just enable a root password in the terminal and use
su

before ubuntu came around i used suse then openSuse
so i was so used to using su, that sudo just throws me off

---

