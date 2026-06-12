---
title: "&quot;X&quot;? and Command Lookup"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-22
I'm glad to see that other people have made a lot of the mistakes that I've made; that's really reassuring.  

Reading along I have two more questions: 

1) What is "x" for?  Such as I had to reboot "X".  For the life of me I can't figure out what that is referring to.  It can't be the entire computer.  I recently saw it in a thread" Xfree86....must be something for a 386???

2) On my other thread ([http://ubuntuforums.org/showthread.php?t=107092](http://ubuntuforums.org/showthread.php?t=107092)) I saw some commands not to type.  The one I saw as this: sudo rm -R /.  Is there a way to look this up somewhere?  I tried to google it, but that didn't turn up too much.

---

### Post by xtacocorex on 2005-12-22
> 1) What is "x" for? 

X is the graphics server on your machine that allows you to use a GUI to interface with programs. XFree86 is an older version of the X server, the newer one is Xorg.

To reboot X, type ctrl alt + backspace.

```
sudo rm -R /
```

Definately not a command that you want to run. rm deletes files, and -R means delete files recursively. / is the system file location. Running as sudo gives you full root privilages and you can delete every file on the machine.

---

### Post by kabus on 2005-12-22
[QUOTE=Nameless]
2) On my other thread ([http://ubuntuforums.org/showthread.php?t=107092](http://ubuntuforums.org/showthread.php?t=107092)) I saw some commands not to type.  The one I saw as this: sudo rm -R /.  Is there a way to look this up somewhere?  I tried to google it, but that didn't turn up too much.[/QUOTE]

If you are unsure what a command does just type 

```
man *command*
```
or
```
*command* --help
```

for some brief (or sometimes not so brief) usage info.

For example :

```
rm --help
```

would tell you that the -R switch stands for "remove the contents of directories recursively"; something you wouldn't want to do in your / directory. :)

---

### Post by Nameless on 2005-12-22
Excellent !  Yet another thing to keep in mind.  Thanks, kabus

---

