---
title: "What do you use to store you passwords"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-23
Since we have so many passwords to remember are there any programs to keep them in?

---

### Post by byenary on 2007-05-23
truecript is a nice app, i have used it in windows, but im sure there is a linux version

---

### Post by byenary on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

---

### Post by ironmonkeygf on 2007-05-23
I use KeePassX ([http://keepass.info/download.html]("http://keepass.info/download.html")).  I prefered the windows version (KeePass), but hopefully they'll get auto-type working in the cross-platform version soon.

---

### Post by shinythings on 2007-05-23
I have an encfs-encrypted folder in my home directory for sensitive stuff like passwords. I use two little scripts to access it:

You'll need to install encfs (and maybe some dependencies, I forget):

```
sudo aptitude install encfs
```

and add your user to the relevant group (this takes affect only after loging out and back in):

```
usermod -a -G fuse username

```

Then put the following in a set of files (in my case .hide and .unhide)

.unhide:
```
mkdir -p ~/vault/
encfs ~/.vault/ ~/vault/
nautilus ~/vault/
```

.hide:
```

fusermount -u ~/vault/
rm -r ~/vault/
```

Make them executable:

```

chmod 700 .unhide
chmod 700 .hide
```

Now just run .unhide from the terminal (or add it to the gnome panel for one-click access). The first time you do it, it should set everything up. Put the file with your passwords in the folder and run .hide.

---

### Post by ushills on 2007-05-23
Another vote for xKeepass, I used Keepass (Win) on my USB drive first as it works as a portable app and is fully compatible with xKeepass (linux).

---

### Post by LaRoza on 2007-05-23
I also use Kpass Portable. (Windows)

---

### Post by clipper74 on 2007-05-23
I like Jafe - a Java based keper with decent crypt levels

---

### Post by toasterofirony on 2007-05-23
A piece of paper. Seriously.

That and have Firefox save the ones for non-vital, but still useful sites.

---

### Post by matthew on 2007-05-23
Look in the repos for Revelation Password Manager. It fully encrypts the file it makes, is flexible and easy to use.

sudo apt-get install revelation

---

### Post by captgadget on 2007-05-23
Downloaded Keepass & it's exactly wanted.

Thanks to all

---

### Post by silent1643 on 2007-05-23
> **captgadget said:**
> Since we have so many passwords to remember are there any programs to keep them in?

use firefox if your the only one using the computer,

use opera wand (pompts for general password to access auto login function)

thats what i use neways

---

### Post by matthew on 2007-05-23
> **captgadget said:**
> Downloaded Keepass & it's exactly wanted.

Thanks to allGlad you found something that works for you.

---

