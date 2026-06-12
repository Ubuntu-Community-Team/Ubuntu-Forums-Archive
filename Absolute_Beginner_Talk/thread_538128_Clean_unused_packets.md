---
title: "Clean unused packets"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-29
Sometimes, when you remove a program, traces of the program remain. How can I get rid of those?

---

### Post by Mornedhel on 2007-08-29
I usually remove packages with the --purge switch, as in :
apt-get --purge remove thispackage
But that may leave configuration files in hidden folder. For instance, to completely get rid of Kazehakase (web browser based on the Gecko engine) :
rm -R .kazehakase

---

### Post by bogolisk on 2007-08-29
> **amitroy5 said:**
> Sometimes, when you remove a program, traces of the program remain. How can I get rid of those?

Huh, please give an example. In a Debian based distro such as Ubuntu, the *purge* operation would get rid of everything from the package while the *remove* operation would leave the configuration files of the package behind. Example
```

sudo aptitude remove...
sudo aptitude purge...
sudo dpkg --remove...
sudo dpkg --purge...

```

---

### Post by amitroy5 on 2007-08-31
The reason I want to do this is because I want to reinstall packages. Is it possible to reinstall packages and have Ubuntu replace my configurations with the default ones?

---

### Post by amitroy5 on 2007-09-02
bump

---

### Post by justleen on 2007-09-02
you could do a find for any left files..
find / -name "*mozilla*"
to find any leftovers...

if youre **really** sure that the found files can be removed, you can do a
find / -name "*mozilla*" -exec rm -r {} \;


Normally the --purge option should remove all files though!!
on some occasion apt will give an error saying that /dir/ was not empty, and not deleted. you can remove those dirs by hand.
Any setting for files are usually stored in /etc/ (which is purged) or in your /home dir, (view hidden files)

---

### Post by amitroy5 on 2007-09-02
I was wondering how you can do this though the Add/Remove programs and the Packet Manager?

---

