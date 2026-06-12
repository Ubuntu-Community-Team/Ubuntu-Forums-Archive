---
title: "What is a Symlink ?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by mistypotato on 2007-01-11
Hi,

What is a symlink, and what is it for?

Thanks

---

### Post by kj1h234lkj1234 on 2007-01-11
A symlink is a file that points to another file.

Example:

You have a file text file in /home/potato/file.txt

If you type the following into your terminal:

```
ln -s /home/potato.file.txt /home/potato/blahblah
```That creates a new symlink called "blahblah" in your home folder.

If you then type:

```
nano -w /home/potato/blahblah (or gedit /home/potato/blahblah)
```It will open blahblah in your text editor, but the file you're REALLY editing is file.txt

You can:

```
rm /home/potato/blahblah
```without affecting file.txt

It's basically a shortcut to a file.

An example of where this is useful is a situation where you sometimes use a different configuration file with a given program. Simply name the files whatever you want (conf1.cfg, conf2.cfg), and just symlink them to where the program expects the configuration file to be. This way you can switch them whenever you'd like without actually moving files around.

Think of them like a shortcut in MS Windows, except the shortcut isn't a seperate file, it's a "link" to the actual file.

---

### Post by obsidion on 2007-01-11
A symbolic Link

man symbolic link from a terminal will tell you a little more about it.

or you could try using google as I did and find a lot more about it like this

[http://www.linux-tutorial.info/modules.php?name=Glossary&term=symbolic%20link](http://www.linux-tutorial.info/modules.php?name=Glossary&term=symbolic%20link)

---

### Post by mistypotato on 2007-01-11
Thanks !

---

