---
title: "Where are my programs in the directory?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by HenvY on 2008-02-15
Hi guys - when I want to open a torrent with Azureus...where is it?!? The Ubuntu directory confuses me, I don't know where anything is. I tried opening it with azureus.desktop but it didn't work.

---

### Post by vikrant82 on 2008-02-15
Are you sure you have azureus installed ?

Try doing Ctrl + F2 and type azureus, see if you get azureus in the choices ...

If you do, click on it to open it and then may be drag torrent on to it.

---

### Post by kpkeerthi on 2008-02-15
> Try doing Ctrl + F2 and type azureus, see if you get azureus in the choices ...

ALT + F2 ?

---

### Post by PeterJS on 2008-02-15
The file structure in Ubuntu is based on the Filesystem Hierarchy Standard.
See the wiki page complete with a description of what goes where, and why:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Borbus on 2008-02-15
Open a terminal and type:

dpkg -L azureus

These are all the files that belong to the Azureus package. (I am assuming you installed it from a package and not from the setup file from the Azureus site).

At the top you will probably see /usr/bin/azureus or some other path with bin in it. This is where the binary (executable) is located.

edit: Yes, the filesystem used by virtually all Linux distributions makes a hell of a lot of sense once you get used to it. Windows is very confusing in comparison. I had to edit this because I thought all distros used it but apparently GoboLinux does not: [http://www.gobolinux.org/](http://www.gobolinux.org/)

---

### Post by mbsullivan on 2008-02-15
Wow... that's a lot of confusing answers! I think (though I'm not sure) that this is the kind of answer you're looking for...

(1) Open a terminal window (how to do this varies with what desktop environment you're running).

(2) Check if/where Azureus is installed:

```
which azureus
```

This will tell you where the azureus binary (executable) file is if it is in one of the directories that are searched when you type a command.

If the above command returned nothing, then Azureus is not installed. In that case...

(3) Install azureus

```
sudo aptitude install azureus
```

Hope this helps!
Mike

P.S. - In addition to the "which" command, which tells you where a binary resides, the "whereis" command will tell you where the location of documentation files (man pages) and libraries for the program.

---

### Post by HenvY on 2008-02-15
how do i open a terminal window in ubuntu 7.10?

---

### Post by p_quarles on 2008-02-15
> **HenvY said:**
> how do i open a terminal window in ubuntu 7.10?
Two ways:
1) The keyboard shortcut alt-F1

2) Click on Applications, then Accessories, then Terminal.

---

### Post by HenvY on 2008-02-15
thanks guys I got it from that...but now Azureus is closing everytime I ok the torrent! It wants me to update as well but if I click yes it closes too.

---

### Post by hyper_ch on 2008-02-15
why not using another torrent client?

Azureus is really heavy on system resources.

For gui clients try ktorrent, deluge or transmission

For CLI clients try:   rtorrent

---

### Post by HenvY on 2008-02-15
I like Azureus, any idea why it keeps closing?

---

