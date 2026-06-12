---
title: "Gnome + Kde Desktop"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-22
If I want to run both Ubuntu and Kubuntu, I have two options -

1) Install both (with the old XP).
2) Install one, say GNOME, then add just the KDE desktop.

Obviously the second option sounds better - less hard disk space, but reports say that the desktops become cluttered with the other desktop's programs.

Is there a way to manage neatly using the second option ? Or is it better to use more hard disk space and install separately ?

---

### Post by taurus on 2007-04-22
Install KDE with

Applications -> Accessories -> Terminal
```
sudo aptitde update
sudo aptitude install kubuntu-desktop
```

---

### Post by mkjarema on 2007-04-22
> **taurus said:**
> Install KDE with

Applications -> Accessories -> Terminal
```
sudo aptitde update
sudo aptitude install kubuntu-desktop
```

great information, but is there a way to uninstall it if you decide you don't like it?
THX

---

### Post by taurus on 2007-04-22
Yeah.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by MoxJet on 2007-04-22
That is rather interesting. I've always wondered why I couldn't remove xubuntu-desktop and kubuntu-desktop properly with »apt-get remove». 

When should one use aptitude to install instead? Always? When installing big applications like these?

---

### Post by taurus on 2007-04-22
Here's another link.  ;) 

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by dptxp on 2007-04-22
Thanks Taurus for the info.
My basic question is still unanswered.
Will I be able to manage both desktops neatly ? 
I am asking this because some go for separate installations. Intentionally, knowing that they can use
both with same one OS.

---

### Post by MoxJet on 2007-04-22
I used to have a number of WMs installed; Gnome, KDE; Enlightenment, Xfce and so on, for testing purposes. You just select session at your login (gdm/kdm) I see no reason to have them in separate installations. 
Just do the aptitude, I doubt there will be any problems ^_^

---

### Post by dptxp on 2007-04-22
How much download for adding KDE desktop and for XFCE desktop ?
OR  How much time needed at 16- 20 KBytes/sec (128 - 160 kbps) ?

---

### Post by mkjarema on 2007-04-22
when trying to remove via the instructions given above I am getting

```
mjar@mjar:~$ sudo aptitude remove kubuntu-desktop
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mjar@mjar:~$ 

```
as output...can you please advise?

---

