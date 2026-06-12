---
title: "Now what'd I do?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by TofuTheGreat on 2005-12-10
I noticed that the default install of Ubuntu had Firefox 1.0.7.  I know that 1.5 is out so I downloaded  the tar.gz file.

I don't have permissions to /usr/lib/mozilla-firefox so how can I install the update?

I had problems during my first install attempt.  It allowed me to create a root user and then my normal user but the remainder of the install failed due to a bad CD.  A new CD allowed the install to continue (deleted and recreated the partition) but I only remember being prompted to create a "non-root" user for my normal login.

I tried to use Terminal to su to root but the password I put in the first time around doesn't work.  So how can I su if I don't know the password?  Am I going to have to reinstall yet again?

---

### Post by towsonu2003 on 2005-12-10
you will want to follow the instructions at wiki.ubuntu.com/FirefoxNewVersion

about root, you will wanna read this one: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by TofuTheGreat on 2005-12-10
I followed the wiki's instructions to upgrade and it did't work.  I still get 1.0.7 everytime I start Firefox.  And now 1.0.7 won't allow me to use the back button for some reason.  I get an alert box telling me that the file can't be found.

So I'm thinking only part of the install went correctly?

---

### Post by Rackerz on 2005-12-10
Did you 'sudo apt-get remove firefox' ? Thats what i had to do to get rid of FF 1.0.7. By any chance would you be running KDE? (Kubuntu).

Darren

---

### Post by TofuTheGreat on 2005-12-10
[QUOTE=Rackerz]Did you 'sudo apt-get remove firefox' ? Thats what i had to do to get rid of FF 1.0.7. By any chance would you be running KDE? (Kubuntu).

Darren[/QUOTE]

Nope didn't see that in the wiki and I know next to nothing about the Linux command line so I'd have never thought of it (not to mention I don't know what that does yet, hello man pages).

Oh, also I have no idea if I'm running KDE.  I'm using the default install of Ubuntu so I think it's Gnome?  Should I be running KDE instead?

---

