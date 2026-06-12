---
title: "Simple Q"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by OldManRiver on 2007-08-10
All,

noob on Ubuntu.  Need to see status of services.  On Gentoo command was "rc-status".  Link to describe this are:

[http://gentoo-wiki.com/MAN_rc-status]("http://gentoo-wiki.com/MAN_rc-status")
[http://gentoo-wiki.com/Rc-status]("http://gentoo-wiki.com/Rc-status")

Can anyone give me the Ubuntu command to see same results here?

Thanks!

OMR

---

### Post by Hospadar on 2007-08-10
i think you are looking for "ps"
this is the generic unix command to show all running processes
"ps -e" shows all processes running on the machine.  there are a lot of other options as well.  try a "man ps"

depending on what you are looking for, you might also want to try:
lsmod (kernel modules)
lsusb (usb devices)
lspci (pci devices)

---

### Post by SOULRiDER on 2007-08-10
A program i likle to use to see processes, RAM and CPU usage is Htop, its like top, but just better!
```
sudo aptitude install htop
```

You can also use:
```
sudo netstat -lnp | less
```

---

### Post by bodhi.zazen on 2007-08-10
You can do via a gui , open servies ...

This is a nice review as well : [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Via the command line, see these links :

[http://www.debianadmin.com/manage-linux-init-or-startup-scripts.html](http://www.debianadmin.com/manage-linux-init-or-startup-scripts.html)

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by OldManRiver on 2007-08-10
All,

Thanks 4 the help but not even close.  When I get a chance and can get tech off it, I'll run cmd to redirect file and pastebin, so you know what I'm looking for.

OMR

---

### Post by OldManRiver on 2007-08-11
All,

Pastebin at: [http://paste.stgraber.org/2456](http://paste.stgraber.org/2456)

shows what I need as output from the command which I seek.

Please let me know Ubuntu cmd that yields these results.

Thanks! :)  :)  :)

OMR

---

