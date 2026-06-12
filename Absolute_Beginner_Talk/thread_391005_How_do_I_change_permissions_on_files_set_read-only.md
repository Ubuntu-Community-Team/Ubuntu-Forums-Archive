---
title: "How do I change permissions on files set read-only by root? [Resolved]"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Davidknight24 on 2007-03-22
Hi, I'm trying to edit the sources.list file in /etc/apt in edubuntu edgy

Problem is, it won't let me. Permission is set to read only by root and I can't change it even with admin rights.

How do I change permissions if I'm not root?

---

### Post by Catsworth on 2007-03-22
> **Davidknight24 said:**
> Hi, I'm trying to edit the sources.list file in /etc/apt in edubuntu edgy

Problem is, it won't let me. Permission is set to read only by root and I can't change it even with admin rights.

How do I change permissions if I'm not root?

Why do you need to change the permissions?  

Did you try:

```
 gksudo gedit /etc/apt/sources.list
```

---

### Post by raul_ on 2007-03-22
just for the record

```


man chmod


```

the previous reply should work, or you have a broken system

PS: you're assuming his using Ubuntu...just replace gedit for whatever text editor you use, if necessary

---

### Post by Catsworth on 2007-03-22
> **raul_ said:**
> just for the record

[code]PS: you're assuming his using Ubuntu...just replace gedit for whatever text editor you use, if necessary

He's using *edubuntu*[1] I assumed that gedit would work in edubuntu, hadn't even considered that it wouldn't - good spot, thanks.




[1] from the OP: "*I'm trying to edit the sources.list file in /etc/apt in edubuntu edgy*"

---

### Post by Bachstelze on 2007-03-22
Please, please, *please* **don't** tell people to use *sudo* for GUI apps. Use *gksudo* (Gnome) or *kdesu* (KDE).

---

### Post by Davidknight24 on 2007-03-22
DOH! Thanks, I'm still getting to grips with the terminal. And yes, I DID just break my system and am in the process of reinstalling everything again!:oops:

---

### Post by Catsworth on 2007-03-22
> **HymnToLife said:**
> Please, please, *please* **don't** tell people to use *sudo* for GUI apps. Use *gksudo* (Gnome) or *kdesu* (KDE).

Ok, why?  What's the difference?

---

### Post by Arken on 2007-03-22
> **Catsworth said:**
> 

```
 sudo gedit /etc/apt/sources.list
```

I'm complete noobster, so, where do I type this?

---

### Post by Bachstelze on 2007-03-22
*gksudo* is specificaly designed as a way to run GUI apps as root, ant it will set trhe environment better for that purpose. Using *sudo* for a GUI app might possibly mess up a system quite badly. Rare, but not unheard of, I helped a guy who completely wrecked his file permissions like that just yesterday.

@Arken : 

```
gksudo gedit /etc/apt/sources.list
```

You type that in the "Run command" dialog (Alt-F2) or in a terminal.

---

### Post by Catsworth on 2007-03-22
> **HymnToLife said:**
> *gksudo* is specificaly designed as a way to run GUI apps as root, ant it will set trhe environment better for that purpose. Using *sudo* for a GUI app might possibly mess up a system quite badly. Rare, but not unheard of, I helped a guy who completely wrecked his file permissions like that just yesterday.[...]

Ok, thanks.  I'll keep that in mind (and edit my original post in case someone else decides to follow that advice).

Cheers.

---

### Post by aysiu on 2007-03-22
> **Catsworth said:**
> Ok, why?  What's the difference?
Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Catsworth on 2007-03-22
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Found that just after the last response (decided to do some more reading), thanks for the link though.

---

### Post by Arken on 2007-03-22
> **HymnToLife said:**
> *gksudo* is specificaly designed as a way to run GUI apps as root, ant it will set trhe environment better for that purpose. Using *sudo* for a GUI app might possibly mess up a system quite badly. Rare, but not unheard of, I helped a guy who completely wrecked his file permissions like that just yesterday.

@Arken : 

```
gksudo gedit /etc/apt/sources.list
```

You type that in the "Run command" dialog (Alt-F2) or in a terminal.

That sources thingy... it's empty... what do I insert in there?

---

### Post by aysiu on 2007-03-22
Wine support moved to [its own thread](http://ubuntuforums.org/showthread.php?t=391030).

---

