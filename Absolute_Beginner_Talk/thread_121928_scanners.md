---
title: "scanners"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by newbee on 2006-01-26
Can sombody point me in the right direction on how to get a scanner to work?

The setup is as follows: Parallel from computer to scanner, and out to printer from scanner.(printer works, but not sure if that is relevant in this case)

Unfortunately, I don't remember the model of the scanner offhand...I think hp scanjet 3200 *edited ...but will check.

Thanks

---

### Post by Ted D. on 2006-01-26
Do you have xane installed?

---

### Post by plexi50 on 2006-01-26
Run Synaptic, make sure sane is installed and the one under it, not at system now but I believe it is sane dev. It has support for some other scanners (my Microtek included) The is a lot of good info on this @ [www.sane-project.org]("http://www.sane-project.org") as to what is supported, etc. My scanner would not work till I installed the update to sane, the it worked right away.

---

### Post by newbee on 2006-01-26
[QUOTE=Ted D.]Do you have xane installed?[/QUOTE]
Do you mean xsane?  Yes, and "kooka"(I think the name is right)...
They pick out my video capture card as a scan device....lol

---

### Post by newbee on 2006-01-26
[QUOTE=plexi50]Run Synaptic, make sure sane is installed and the one under it, not at system now but I believe it is sane dev. It has support for some other scanners (my Microtek included) The is a lot of good info on this @ [www.sane-project.org]("http://www.sane-project.org") as to what is supported, etc. My scanner would not work till I installed the update to sane, the it worked right away.[/QUOTE]
This machine does not have access to the internet, so I guess I'll try to get it some other way...

---

### Post by plexi50 on 2006-01-26
You will absolutely have to have those installed. They hold the "driver" info that allows Ubuntu to recognize the scanner. The other programs you mentioned are only the scanning software, which both work nicely IMHO

---

### Post by Thulemanden on 2006-01-26
My scanner was not found using the user entry in the menu.

Entering as root however gave me access to choose between my 2 scanner devices.

Try entering xsane as root in a terminal.

later you can give the user membreship in the scanner group.

---

