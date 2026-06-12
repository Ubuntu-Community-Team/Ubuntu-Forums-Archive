---
title: "terminal commands for gui ?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-14
Please correct me if I'm wrong.
if I understand Ubuntu right then its GUI is just a front end for terminal commands & there's nothing done from the GUI that you can't do from the terminal.
I was wondering if there was some way to view some of the toolbar  commands they actually run. I know the desktop items you can just check the properties & find the launcher.
One in particular is the connection eth & wireless.  I'd like to know how to get connected from the yerminal when I lose connection.

---

### Post by wieman01 on 2008-02-14
Then start from here:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

Basically you can restart your network by issuing:
> sudo /etc/init.d/networking restart

---

### Post by erginemr on 2008-02-14
System-wise you are correct, there is almost always a CLI alternative to a GUI program. Some GUI's are even just front-ends to CLI back-ends, such as grsync to rsync , winff to ffmpeg, etc. However, this is not the case within a single graphical application. That is, if it is not deliberately designed that way, you cannot emulate pressing a button in a GTK/QT program from the terminal.

That being said, I am using an ADSL modem, and can start my connection from the terminal with
```
sudo pon adslusb
```
and stop it with
```
sudo poff
```
I think you should also focus on the command "pon/poff".

---

### Post by sigge on 2008-02-14
Hi Gary.

Don't mind the pon/poff stuff... Thats for adsl-connections, and not for your setup... :) Even if you _do_ use adsl, you stated that you connect to a wireless router, and thus this is not a PPOE network.

What you need to learn is:
iwconfig : (type this in a termial) ```
man iwconfig
```
ifup : (type this in a termial) ```
man ifup
```
I'm suggesting here that you take the time to read the fairly extensive explanation in the man-pages... This is definately "the way" to learn CLI.

These commands do most (re)connection work in CLI Linux... :)

Hope this helps.

---

### Post by Trail on 2008-02-14
> **erginemr said:**
> you cannot emulate pressing a button in a GTK/QT program from the terminal.

Check out DCOP, though :)

---

### Post by garyed on 2008-02-15
Thanks for all the replies.
I had some problems today & couldn't get much computer time in but I'm checking out the man files.

---

