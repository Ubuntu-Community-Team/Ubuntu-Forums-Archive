---
title: "A Question about Synaptic Package Manager"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by vlaklak on 2007-11-14
Hi!  I am using Ubuntu 7.10.    It's fun to use also "my opinion" much more easy to handle than 7.4 and 6.10 and Windows XP.

But unfortunatly I could'nt figure out how to reach the downloads from Synaptic Package Manager.   Where is the downloads?  I only see the "VLC", but I can not reach any other programs which are downloaded from  Synaptic Package Manager.

Could you give me some tips please?

---

### Post by paul.matthijsse on 2007-11-14
Hello, you mean you don't find your downloaded programs in the menu? Not all apps have menu entries. What did you download/install for example, and are you using Gnome, KDE or another window manager?

---

### Post by Partyboi2 on 2007-11-14
> **vlaklak said:**
> Hi!  I am using Ubuntu 7.10.    It's fun to use also "my opinion" much more easy to handle than 7.4 and 6.10 and Windows XP.

But unfortunatly I could'nt figure out how to reach the downloads from Synaptic Package Manager.   Where is the downloads?  I only see the "VLC", but I can not reach any other programs which are downloaded from  Synaptic Package Manager.

Could you give me some tips please?
Not sure what you are trying to say. Are you meaning how do you find the programs that Synaptic has downloaded?

---

### Post by vlaklak on 2007-11-14
When I download something from Synaptic Package Manager, I can not find the things I downloaded.  They are not in the "Applications".   

How can I find them?

I think I have to install "Debian Desktop", but I don't know how to do it.  

Could you give me some tips please?:confused:

---

### Post by Inxsible on 2007-11-14
What DM are you using ?
Gnome, KDE or xfce?

If you elaborate on what particular application you want to locate, maybe we can help you better.

---

### Post by paul.matthijsse on 2007-11-14
Once again, not all apps are given a menu entry, but have to be started from the command line. You don't have to install Debian Desktop for this, as the result might quite likely be the same. As root, in a terminal, type "sudo updatedb" and let it run a minute, then type "locate <appname> to find out where it hides, where <appname> is the name of the application you are looking for. Or just type "appname" in a terminal to see if it starts.

---

### Post by Dark Aspect on 2007-11-14
Are we talking menu shortcuts or the actually packages downloaded?The first one varies from application to application.Some applications (example key2joy)  are command line only.The actually packages on the other hand can be found in the /var/cache/apt/archives.

---

### Post by Inxsible on 2007-11-14
If you install the application, they are most likely found in /usr/bin

---

### Post by vlaklak on 2007-11-14
Ohhh thanks very much!

I am so stupid that I missed the usr folder.

Thanks very much!  Ubuntu and the peaple are number one!!!!!:lolflag:

---

### Post by Inxsible on 2007-11-14
> **vlaklak said:**
> Ohhh thanks very much!

I am so stupid that I missed the usr folder.

Thanks very much!  Ubuntu and the peaple are number one!!!!!:lolflag:
Glad to help !!! :D

Mark your thread solved if you questions have been answered. Thread Tools>>Mark Thread as solved. :)

---

### Post by CatKiller on 2007-11-14
Sometimes installed programs do create a menu entry, but the menu needs to be refreshed before they show up. Logging out and logging back in will do it, or if you're using Gnome, you could use **killall gnome-panel**.

---

