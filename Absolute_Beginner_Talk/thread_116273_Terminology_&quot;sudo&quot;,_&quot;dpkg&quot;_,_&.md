---
title: "Terminology &quot;sudo&quot;, &quot;dpkg&quot; , &quot;rm&quot;, etc...."
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-01-12
Hello guys, does someone knows where i can find guide to learning all this terms and learn what they are and what they mean?..

---

### Post by Thirsteh on 2006-01-12
Not really, but I can tell you.

sudo = superuserdo, do something as the super user (root)
Example:> sudo gedit /etc/X11/xorg.conf edit your X.org configuration file as the superuser -- allows for you to actually save your changes.

dpkg = debian package, do something with a debian package (.deb)
Example:> sudo dpkg -i funnygame.deb installs a funny game.
> sudo dpkg remove funnygame removes that funny game again.

rm = remove, removes a file or folder (supports recursive deletion)
> rm horse.avi gets rid of that horse movie.
> rm -r Music/ gets rid of your music folder and all its contents.
> rm -rf Music/ gets rid of your music folder and all its contents without asking you to confirm deletes (same can be done with files).

---

### Post by Estariel on 2006-01-12
this is a nice guide: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

scroll down a little for the commands...

---

### Post by carlosqueso on 2006-01-12
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)  That's the best tutorial I've found for the terminal.

---

### Post by DoorGunner on 2006-01-12
another thing availible if you are not sure of a command is to do this
when you are done type q for quit or just x out of terminal
$ man rm
$ man dpkg
$ man sudo

In this example man will give you the intructions for the rm command. 

[http://www.mediacollege.com/linux/command/linux-command.html](http://www.mediacollege.com/linux/command/linux-command.html)
this may help as well..... just another resourse

---

### Post by az on 2006-01-12
*EDIT* I have been beaten to the punch!

RTFM means "read the ... manual"

You can open a terminal and type

man sudo

to read the sudo manual page (man page)
(scroll up and down, press "q" to quit)

If someone answers a post with RTFM, it is usually rude.  I hope I am not being rude.

---

### Post by DoorGunner on 2006-01-12
Lol :d

---

### Post by tim15856 on 2006-01-12
Here's a reference for Debian which Ubuntu is based on [http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf](http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf)

---

