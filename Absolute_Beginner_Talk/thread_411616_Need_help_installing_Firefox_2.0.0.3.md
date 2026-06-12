---
title: "Need help installing Firefox 2.0.0.3"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-17
I've download the latest version of Firefox from Mozilla and am supposed to untar it into the opt directory them run a script to complete the install. Can't place it into opt because it's locked and I don't have root permission. How do I get that? Thanks.

---

### Post by Bachstelze on 2007-04-17
Which Ubuntu are you running ?

---

### Post by joeblow1102 on 2007-04-17
This site should be helpful.  Go to all and choose a mirror to download the debian package from.  Save that to your home folder, double click it, and install it.

[http://packages.debian.org/unstable/web/mozilla-firefox]("http://packages.debian.org/unstable/web/mozilla-firefox")

---

### Post by Bachstelze on 2007-04-17
Please, please, please *don't* do that !

You're running Ubuntu, not Debian.

---

### Post by joeblow1102 on 2007-04-17
I'm kinda confused, the debian packages work.

---

### Post by Bachstelze on 2007-04-17
Most of the time, they don't so it's better not to use them at all.

---

### Post by anujseth on 2007-04-17
thats what happens to everyone "the debian packages work" ... until one fine day ull  come across your dependencies so mangled up that ull regret it. never ever install a debian package unless its absolutely the last thing to do on the planet. 

if u installed ubuntu yourself u already have root permissions. just type in chmod etc. with sudo prefix ... the password it asks for is same as your user password .. since you have the rights and belong to the root group by default.

---

### Post by joeblow1102 on 2007-04-17
they've always worked for me and i've been through the dependency hell.  anyway, let's help this user.

say you unarchive the folder to your home folder.  you want to open the terminal and go sudo mv -r firefox/ (wherever you want to move it)

and it seems that you want to run run-mozilla.sh by double clicking it and going run.

---

