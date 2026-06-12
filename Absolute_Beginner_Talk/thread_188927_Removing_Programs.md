---
title: "Removing Programs"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-06-04
I installed LimeWire on Dapper but couldn't get it to work due to not having Java installed correctly.  I want to reinstall it, but would like to delete the current installation from my computer.  How do I do this?  Commands such as 'sudo apt-get remove limewire' don't work.  Is there another way?

---

### Post by tdrusk on 2006-06-04
[QUOTE=amcavoy]I installed LimeWire on Dapper but couldn't get it to work due to not having Java installed correctly.  I want to reinstall it, but would like to delete the current installation from my computer.  How do I do this?  Commands such as 'sudo apt-get remove limewire' don't work.  Is there another way?[/QUOTE]
Applications>add/remove programs. then uncheck the program. See if that works.

---

### Post by cromestant on 2006-06-04
I would recomend that you don't use apt-get too much, dependency wise, it's not quite good, use aptitude instead

You could do a 'sudo aptitude uninstall limewire'
If that does not work it's just that the name is not quite right, so just do an 
'sudo aptitude search limewire' or just launch aptitude with no options and you'll see an ncurses based UI, and there you can look at packages installed and remove them.

If it's just java that's not installed you don't need to uninstall it, just install java and you are good to go.

There is a manual for ubuntu java install ( blackdown and sun) so it's really easy to set up . I don't have the link at hand now, but by doing a search on the forum you'll get it.

Hope this helps

---

