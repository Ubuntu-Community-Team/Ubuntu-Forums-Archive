---
title: "Conky problems"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-12-07
I did a forum search, other people had problems, but mine seems to be different.  I seem to be having a lot of problems today.  :lolflag:

Console output of Conky:
chris@chris-laptop:~$ conky
Conky: desktop window (e000ba) is subwindow of root window (1a5)
Conky: drawing to desktop window
Conky: drawing to single buffer

It appears on my desktop on the bottom left corner, but when I drag my (click and drag) border around it, it disipears and then when Conky refreshes, it redraws.  I cannot move the window either..

Screenshot:

---

### Post by jordanmthomas on 2007-12-07
There's a few things you can do / try
In your config, set conky to come up where you want so you don't have to move it.
Also, I believe you can move it if you hold down alt and drag it.

---

### Post by Ek0nomik on 2007-12-07
> **chris062689 said:**
> I did a forum search, other people had problems, but mine seems to be different.  I seem to be having a lot of problems today.  :lolflag:

Console output of Conky:
chris@chris-laptop:~$ conky
Conky: desktop window (e000ba) is subwindow of root window (1a5)
Conky: drawing to desktop window
Conky: drawing to single buffer

It appears on my desktop on the bottom left corner, but when I drag my (click and drag) border around it, it disipears and then when Conky refreshes, it redraws.  I cannot move the window either..

Screenshot:

Can you post your .conkyrc file contents?

---

### Post by Rocket2DMn on 2007-12-07
Have you tried installing from the repos rather than using the source?
Also, did you start the xserver when logged into a command line / tty as root?

---

### Post by jordanmthomas on 2007-12-07
> **Rocket2DMn said:**
> Have you tried installing from the repos rather than using the source?
Also, did you start the xserver when logged into a command line / tty as root?

I think the file on his desktop is just a conkyrc from gnome-look, judging by the random numbers at the start (not the source code).

---

### Post by chris062689 on 2007-12-07
I simply sudo apt-get install conky to install.
I did not use the terminal to login.
Where is the configuration file?

---

### Post by Rocket2DMn on 2007-12-07
> **chris062689 said:**
> I simply sudo apt-get install conky to install.
I did not use the terminal to login.
Where is the configuration file?

the file should be in your home directory "~".  It is a hidden file called .conkyrc so you can open Nautilus and hit ctrl+h to see all the hidden files and folders, or you can open a terminal and run ```
gedit .conkyrc
```

---

### Post by chris062689 on 2007-12-07
Thats what I was thinking, but there is no such file there.

---

### Post by Rocket2DMn on 2007-12-07
> **chris062689 said:**
> Thats what I was thinking, but there is no such file there.

You can run a search for .conkyrc from Places->Search for Files. 
You could search around online for different configurations that you like, then save it (or combinations of different files) as .conkyrc in your home directory and edit it as necessary.  Their homepage has help on setting up the file with the correct variables, it does require you to have good knowledge of your system - [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by jordanmthomas on 2007-12-07
It uses the config at /usr/share/doc/conky/examples/conkyrc.sample.gz
(It's zipped, so you will have to unzip to to view it)

If you have a configuration file in ~/.conkyrc it will use it,

---

### Post by chris062689 on 2007-12-07
Ah ok.  I just found one from another website, copy'd and pasted it, and everything works good now.

Are there any pre-made scripts designed for Ubuntu?  All of the ones I saw were designed for ArchLinux.

---

### Post by jordanmthomas on 2007-12-07
I use Arch, so that's fine for me.  :)
Anyway, you can still use them, just take out the parts that talk about pacman.

---

### Post by Rocket2DMn on 2007-12-07
> **chris062689 said:**
> Ah ok.  I just found one from another website, copy'd and pasted it, and everything works good now.

Are there any pre-made scripts designed for Ubuntu?  All of the ones I saw were designed for ArchLinux.

If by scripts you mean configurations, you can just search these forums or conky's website for dozens of examples.  I'll post mine for your reference

---

