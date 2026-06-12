---
title: "Problem with UbuntuStudio DVD and Ubuntu Package manager"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-12
I downloaded the UbuntuStudio DVD, and am tryine to add it to a package manager, but all I get is an error.

It installed to the system fine, like a clean UbuntuStudio install, but just won't add to the package manager.

Help?  I don't want to have to download these packages again :(

---

### Post by Acksys on 2007-05-12
I just installed Ubuntustudio today, and I had to insert a regular 7.04 CD for Synaptic to install NFS.

I haven't looked into it, but I assume the Feisty repositories aren't in /etc/apt/sources.list by default.

---

### Post by deadgobby on 2007-05-12
The sever is down!

---

### Post by jiminycricket on 2007-05-12
This is how to install Ubuntustudio in a normal Feisty Fawn: [http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/](http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/) (for just theme)

(for everything)

```
Open a terminal and cut/paste the following two commands:

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

Now, open synaptic and refresh the package list. Next search for ubuntustudio and you should have a ton of packages for it. Grab the desktop ones and the others you might want. It does overwrite the old orange ubuntu theme with the new slick black one, so just be aware.
```

---

### Post by deadgobby on 2007-05-12
The sever is DOWN!!

---

### Post by gohanssjn on 2007-05-12
Ok, I dl'ed all of those last night while I slept (except ubuntustudio-desktop).  Just a shame I can't pull them off a perfectly good DVD.

I tried installing UbuntuStudio, but I am kind of weary about the low latency drivers...anyone know what they are, exactly?  Was also turned off a bit that is didn't have OpenOffice by default, just the Word Processor.

No matter what I do, I am keeping my old theme though, the US one just doesn't suit me!

---

