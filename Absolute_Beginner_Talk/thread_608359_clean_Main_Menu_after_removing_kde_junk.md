---
title: "clean Main Menu after removing kde junk"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by positroniks on 2007-11-09
I installed kde-core in Synaptic after reading somewhere in a post on these forums that it would make Konqueror run more stable. Turns out, I don't like Konqueror and I've uninstalled it. I also uninstalled kde-core and all the junk that came with it using the "pure ubuntu" method I found [here]("http://www.psychocats.net/ubuntu/puregnome").

Now I'm left with a bunch of trash entries in my Main Menu that use something called kcmshell which obviously was part of the KDE junk I removed. I know I can just hide the entries that don't work but I want them gone, completely. How would I go about doing it? Do I need any of this stuff? If so, how do I run it without kcmshell?

---

### Post by Nano Geek on 2007-11-10
Go **System=>Preferences=>Main Menu** and right-click the ones you don't want and click **Delete**.

---

### Post by positroniks on 2007-11-10
Doh! :oops: 
An 'add' button but no 'remove' button confused me. Didn't think to right click them. 
Had to check the command property of each, one at a time, but it did the trick.
Thanks! =D>

---

### Post by Nano Geek on 2007-11-10
Any time. :KS

---

### Post by freddybob on 2007-11-21
In the same situation after installing Konqueror in Ubuntu Gutsy then removing it again.

*sudo apt-get autoremove* got rid of most of the extra menu items.

The four items that remain (CGI Scripts, Input Actions, Keyboard, Keyboard Layout) all seem to be related to kcmshell.  Is it safe to remove kcmshell?

I still want to use some KDE applications (Amarok, KTorrent).

---

