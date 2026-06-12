---
title: "Nvidia Selecting Pci Instead Of Agp"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by mobraver on 2007-10-12
Please help I have no graphic in Ubuntu.  
I have error: No device detected,  no screen found.
Because  it indicates: (Bus ID PCI:1:0:0) found But my card is in an agp slot not pci.

---

### Post by myk.dinis on 2007-10-12
PCI 1:0:0 is your AGP slot...

It's just how it's named...

At the command prompt (don't criticize) type lspci

That'll list all your devices on the PCi bus...You'll see your card there...

Also, if you want more detailed help you'll need to post your xorg.conf and your lspci output here...
in the terminal (also known as command line) type this command:
lspci > ~/lspci.txt
Then type:
nano ~/lspci.txt
copy and paste all the stuff in thee into a message here...and then:
nano /etc/X11/xorg.conf
You won't be able to edit (that's good) copy and paste the info into the same message...
I'll hook you up after that!

Cheers!
Myk

---

