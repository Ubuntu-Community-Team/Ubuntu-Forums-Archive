---
title: "firefox??"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-28
i have some dependencies.
some apts need firefox. 
but to instaall firefox i must remove 15 other apts.
which are v. important.

how do i install firefox without apt-get?

thanks

---

### Post by scxtt on 2007-06-28
i think you can just get the *.tar.gz file from mozilla.com and extract it ... but if your system is missing some necessary dependencies you're SOL ...

---

### Post by skymera on 2007-06-28
the dependencie IS forefox

---

### Post by TitanKing on 2007-06-28
I would say;

Install this : [http://www.getautomatix.com](http://www.getautomatix.com)

And install applications like these from there...

---

### Post by scxtt on 2007-06-28
> **skymera said:**
> the dependencie IS forefoxi meant that as "if you don't have the necessary deps for firefox installed, it's not going to run from the folder you extract it to" ...

what is it telling you it will remove when you do **apt-get install firefox**?

---

### Post by pyros on 2007-06-28
> **skymera said:**
> i have some dependencies.
some apts need firefox. 
but to instaall firefox i must remove 15 other apts.
which are v. important.

how do i install firefox without apt-get?

thanks


Is there any chance that you could copy and paste the messages that you are getting?

---

### Post by alienexplorers on 2007-06-28
Just go to mozilla .com and download Firefox 2.0.0.4's tar file.  Un tar it in your home directory.  Setup a shortcut to it and away you go.

---

### Post by skymera on 2007-06-28
well.. it didnt say what it was removeing in terminal so i went to Synaptics.
and it says it going to remove..

```

Ekiga
Evolution
Evolution-mail-server
gnome applets
gnome control centre
gnome panel
gnome session 
gnome terminal
libcamel1.2-10
libdatabook1.2-2
libdataserverui1.2-8
libnss3
nautilus
nautilus-sendto

```

---

### Post by pyros on 2007-06-28
ok, what if you try to install the package 
```

firefox-gnome-support

```

---

### Post by skymera on 2007-06-28
that needs firefox...

---

### Post by skymera on 2007-06-28
i just 
```
 sudo apt-get install ubuntu-desktop 
```
im guessign that has all that  i need.
i checked and removes nothing...installs most of what was removed.

so hopefully problem solved.

thanks for the help, appreciate it

---

### Post by pyros on 2007-06-28
---

sweet.

---

