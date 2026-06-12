---
title: "Wrong Ubuntu?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by FireFreek on 2007-10-30
Well, first, i accidentally installed the server version of Ubuntu on my desktop. Then, i swear i installed the download version, yet it still acts EXACTLY the same as the server version(No GUI, just command lines. Scary for a newcomer like me)! Is it just a stupid mistake i've made? Do i have to initiate some command? Oh well, i'm installing Kubuntu now, which has no server version, right?

---

### Post by mikewhatever on 2007-10-30
You may find the following useful: [http://psychocats.net/ubuntu/whichbuntu](http://psychocats.net/ubuntu/whichbuntu).

The only difference between Ubuntu and Kubuntu is Gnome vs. KDE desktop environments.

---

### Post by taurus on 2007-10-30
You don't have to reinstall again.  If you want KDE, just run

```
sudo apt-get update
sudo apt-get install kubuntu-desktop kdm
sudo /etc/init.d/kdm start
```

---

### Post by aysiu on 2007-10-30
Try this:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by PPAAUULL on 2007-10-30
you could see if you can start GDM and even on the desktop version (atleast I know the alt. disk) you can install a command line based system.

---

### Post by Incense on 2007-10-30
The server install is great! One disk for all my machines which run Ubunutu, Kubuntu, and Xubuntu. Just install the server, and your DE is an apt-get away.

---

### Post by FireFreek on 2007-10-30
> **taurus said:**
> You don't have to reinstall again.  If you want KDE, just run

```
sudo apt-get update
sudo apt-get install kubuntu-desktop kdm
sudo /etc/init.d/kdm start
```

Ok, i'll try typing that. And no, i don't want the KDE (well, i dont care), I want any GUI. It's just a black screen with letters. And I dont know all the commands for Linux. Just "cd", "ln" and "pwd"

---

### Post by rudeboyskunk on 2007-10-30
for gnome it should be (IIRC):

```
sudo apt-get update
sudo apt-get install gnome gdm
```

then when it's done just type "gdm" (or maybe "sudo gdm").

good luck!

---

### Post by FireFreek on 2007-10-30
Did i mention the computer doesn't have internet? That's probably why it didn't work. :(

Oh, and it turns out the computer also doesn't graphically support Kubuntu. It's pretty old. I can say... maybe 7 years old..

---

### Post by rudeboyskunk on 2007-10-30
What's the model number?  Can you post the specifications (or a link to them)?

---

### Post by FireFreek on 2007-10-30
I dont think i'd find a model number, since i bought it at a garage sale or it was a hand-me-down. What I do know at this point is that it has 128MB memory, and the rest is really old.

---

### Post by taurus on 2007-10-30
If it has only 128MB of RAM, then you definitely don't want to go with Gnome or KDE.  Should try either Xubuntu (XFce4) or Fluxbuntu (fluxbox).

---

### Post by FireFreek on 2007-10-30
But I do have another computer slightly older, I'd say about 4 years old. I tried Live CD on that one, and it worked fine. I cant install it yet though, since that comp has some important files I need to transfer to my main one.

---

### Post by FireFreek on 2007-10-30
Argh, as it turns out, i've run out of CD's to burn. This day is getting worse by the minute.

---

