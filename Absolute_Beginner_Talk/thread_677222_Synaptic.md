---
title: "Synaptic"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by BackBack on 2008-01-24
Evidently there's a system update, but when I click on it to install the updates, I get a message saying "Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."  When I open Synaptic it says, "You have 1 broken package on your system! Use the "Broken" filter to locate it." I know I could just do sudo apt-get update, but I'd rather solve this problem, so please help.

Oh, on another note, when I try to install a font by clicking and dragging the font into /usr/share/fonts I get an error saying I don't have permission to do that, what would be the command to throw the file from the desktop to that directory?

Thanks in advance.

---

### Post by LaRoza on 2008-01-24
Run:
```

sudo apt-get install -f

```

---

### Post by taurus on 2008-01-24
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

If you want to move the new fonts to /usr/share/fonts, you need root privilege so run this command from a terminal then.

```
gksudo nautilus
```
Now, you should be able to move those new fonts to /usr/share/fonts.

---

### Post by BackBack on 2008-01-24
Ah, well many thanks. It works quite well, though it does tell me to use dpkg --configure -a constantly to fix an error, but after using it the errors are gone. Thanks a bunch ;)

---

