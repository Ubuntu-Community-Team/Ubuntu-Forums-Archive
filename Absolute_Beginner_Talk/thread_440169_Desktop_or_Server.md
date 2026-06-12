---
title: "Desktop or Server ?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Impax on 2007-05-11
Ok!  So I've decided to dive into the Linux world and have a few questions. 

Firstly let me say I have ZERO experience with anything other than the Windows with which I am very well adapted to. I know there will be a decent learning curve and that I am actually looking forward to, I love to learn (just wish I would have had that love 20 years ago when I was still in school). 

What I am looking at doing is eventually setting up a LAMP server for our company. Which version (Desktop or Server) would likely be the least amt of trouble for a total Linux newb. From what I can tell through my research is that the Server edition comes out of the box with no GUI but does have AMP already set up and configured however without a GUI of some sort I am not sure how difficult it would be to get one installed. On the other side of the fence if I went with the Desktop version of Ubuntu which has a GUI I'm really not sure how difficult it would be to set up a LAMP server and configure everything to work with eachother.

Any input on this decision I have in front of me weather to go with the Desktop version and setup AMP or go with the Server version and figure out how to get a GUI installed would be greatly appreciated.

Thanks much, I look forward to getting my feet wet.

---

### Post by Ek0nomik on 2007-05-11
You can install the server edition, and than install a GUI if you wish.  This way, upon installation, all your AMP business is installed, and than you can add the GUI.

```
sudo aptitude install ubuntu-desktop
```

Than you restart, and you have a Gnome desktop.  :)

On the other hand, you could install the Desktop and than install the AMP.  That's what I did, but to each his/her own.

---

### Post by mjwhitfield on 2007-05-11
if you're running a server you won't need a GUI I wouldn't have thought.

---

### Post by heimo on 2007-05-11
Install desktop version. It's basically server version without GUI. So you have one step less as you want GUI anyway and server version doesn't come with LAMP installed (as far as I know, haven't used the latest install CDs).

EDIT: Ek0nomic, does that mean that alternate install can install (L)AMP stack for you?

---

### Post by Bachstelze on 2007-05-11
> **Ek0nomik said:**
> You can install the server edition, and than install a GUI if you wish.  This way, upon installation, all your AMP business is installed, and than you can add the GUI.

```
sudo aptitude install ubuntu-desktop
```

Than you restart, and you have a Gnome desktop.  :).

Nope he doesn't, because that does not install X. To install X :

```
sudo apt-get install x-window-system-core
```


@heimo : Since Dapper, the server CD can install a LAMP stack out of the box.

---

### Post by Ek0nomik on 2007-05-11
> **mjwhitfield said:**
> if you're running a server you won't need a GUI I wouldn't have thought.

He *won't* need a GUI, but as he said, he is completely new to Linux.  While it is definitely possible to learn straight from command line and no GUI, he may find it easier to have a GUI as a safe guard.

It really depends on what he/she is going to feel most comfortable with.  :)

---

### Post by Ek0nomik on 2007-05-11
> **HymnToLife said:**
> Nope he doesn't, because that does not install X. To install X :

```
sudo apt-get install x-window-system-core
```


@heimo : Since Dapper, the server CD can install a LAMP stack out of the box.

Wouldn't aptitude install X?  It's kind of a dependency...

---

### Post by heimo on 2007-05-11
> **HymnToLife said:**
> Nope he doesn't, because that does not install X. To install X :

```
sudo apt-get install x-window-system-core
```

Hmm... I'm pretty sure, installing ubuntu-desktop package will install Xorg too.

> **HymnToLife said:**
> 
@heimo : Since Dapper, the server CD can install a LAMP stack out of the box.

Good to know! Thanks!

---

### Post by Bachstelze on 2007-05-11
Oh, yeah, you guys are right, I always though it didn't... Well, that's kind of lame, what if I want to use XF86 or XGL instead of Xorg ?

---

### Post by Ek0nomik on 2007-05-11
> **HymnToLife said:**
> Hmm, seems it is since Feisty, it wasn't in previous releases...

How do you check that all the dependencies of a package are?  I imagine there is a command to list them?

---

### Post by heimo on 2007-05-11
> **Ek0nomik said:**
> How do you check that all the dependencies of a package are?  I imagine there is a command to list them?

For example:
```
aptitude show ubuntu-desktop
```

Or by using package search:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Bachstelze on 2007-05-11
They're listed on the page about that package at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Ek0nomik on 2007-05-11
Thanks.  :)

---

### Post by Impax on 2007-05-11
> **Ek0nomik said:**
> He *won't* need a GUI, but as he said, he is completely new to Linux.  While it is definitely possible to learn straight from command line and no GUI, he may find it easier to have a GUI as a safe guard.

It really depends on what he/she is going to feel most comfortable with.  :)

Percisely, I do know there will be alot of command line stuff and all but being a totally new to Linux I would feel more comfortable with some kind of desktop.

Thanks again for the replies, grabbing the server version and simply installing the GUI is looking like the way to go. I may just grab both and try it both ways just for the learning experience.

Thanks again.

---

### Post by Impax on 2007-05-11
> **Ek0nomik said:**
> You can install the server edition, and than install a GUI if you wish.  This way, upon installation, all your AMP business is installed, and than you can add the GUI.

```
sudo aptitude install ubuntu-desktop
```

Than you restart, and you have a Gnome desktop.  :)

On the other hand, you could install the Desktop and than install the AMP.  That's what I did, but to each his/her own.

By the way, what is "aptitude" ? Is that similar to "apt-get" ? I know "sudo" is for password / root user or something like that and "install ubuntu-desktop" is pretty self explanitory. 

Thanks again

---

### Post by freebeer on 2007-05-11
Welcome to Ubuntu and this community!  Knowing that you're going to have to learn stuff (and embracing that fact!) bodes well for you.  :D

It's really a matter of opinion - ie there really isn't a right and wrong answer for your question.  My suggestion would be to go with the GUI (desktop) version.  You'll be in somewhat more familiar territory.  Installing LAMP afterwards is really easy.  (Fine-tuning it later to your specification might be more involved.)

That's what I did to help on the learning curve.

---

### Post by heimo on 2007-05-11
Yeah - aptitude is just like apt-get, front end for installing/removing/querying packages. Very similar syntax too.

---

