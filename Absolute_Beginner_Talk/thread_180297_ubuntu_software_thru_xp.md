---
title: "ubuntu software thru xp?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by lordharsha on 2006-05-22
is there any way to download the software for ubuntu through windows? my main pc has xp, and my laptop will have ubuntu installed. the problem is that xp is connected to the internet, but ubuntu isn't

---

### Post by aysiu on 2006-05-22
Is there *any* way? Yes.

Will it be easy? Hell, no... especially if you can't even get internet on your XP computer using a Ubuntu live CD. Can you use a Ubuntu live CD on your XP computer?

---

### Post by lordharsha on 2006-05-22
yeah, i can

---

### Post by aysiu on 2006-05-22
It's still not going to be easy, but you can try this:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

If you don't want to create an entire local repository, you can do this:

Boot up the live CD.
Press Alt-F2 and type ```
gksudo nautilus
``` in Ubuntu or ```
kdesu konqueror
``` in Kubuntu.
This will launch a file browser with root privileges.
Go to the /var/cache/apt/archives folder.
Delete everything in there.

Then, go to System > Administration > Synaptic Package Manager in Ubuntu or KMenu > System > Adept in Kubuntu and install whatever programs you want to install.

Once they're installed, copy over the .deb files from /var/cache/apt/archives to some other place (external hard drive, CD-ROM, whatever) and then copy them to your Ubuntu desktop (the actual Ubuntu, not the live CD).

In the actual Ubuntu, paste this into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

If you don't know how to install stuff with Synaptic Package Manager, go here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by lordharsha on 2006-05-22
Isn't there a ftp site where I could maybe download them from, and install them later in ubuntu?

---

### Post by aysiu on 2006-05-22
[QUOTE=lordharsha]Isn't there a ftp site where I could maybe download them from, and install them later in ubuntu?[/QUOTE] Well, that's essentially what I just outlined in the last post. You kind of need a package manager like Synaptic or Adept, though, as you wouldn't know what dependencies you needed otherwise.

---

### Post by lordharsha on 2006-05-22
Oh, ok. Thanks

---

