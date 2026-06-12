---
title: "Deskjet 672C alignment"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-10-15
I was wondering under Ubuntu how I would go about aligning my printers cartridges after installing new ones. I have a old HP Deskjet 672C that came with software for Windows to align the cartridges with. Since I do not have windows or wine running how could I align the cartridges.

---

### Post by PereUbu on 2006-10-22
Hi there!

Try

/usr/bin/hp-toolbox

in a console.

You might need to install an additional package, to get it to work.I don't remember the name of the package, but it's name is in the error message.


Frankly, I didnt't have any luck with the aligning tool for my HP DJ5440. Hopefully it works for you! ;) 

Good luck! 
PereUbu

---

### Post by Bartender on 2006-10-22
I typed in usr/bin/hp-toolbox   Got this: 
"You must install python-qt3 for this program to work"

---

### Post by Chaos5lw on 2006-10-22
> **Bartender said:**
> I typed in usr/bin/hp-toolbox   Got this: 
"You must install python-qt3 for this program to work"
I think you mean /usr/bin/hp-toolbox

Try "sudo apt-get install python-qt3", let it install and try again.

---

