---
title: "USB mounting problem"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by emnaki on 2007-04-21
I have been unable mount my usbdrive  automatically in Feisty. It gives me this error, "you are not privileged to mount this volume". Does anyone know how to fix this?

---

### Post by Happy_Man on 2007-04-21
Well, did you perhaps mess with its settings the last time you mounted it? It seems like you accidentally changed its permissions so that only root can access it.

---

### Post by mkaylor on 2007-04-25
I'm having the same problem.  How would one fix that if that were the case?  I have it set to 777.

Thanks,
Mike

---

### Post by deadgobby on 2007-04-25
Random disconnection is a kernel bug that is not fixed yet. Some users report randomly disconnecting USB devices, especially external hard drives. One solution is to start the system with the option "irqpoll" in grub, but this doesn't work for everybody, and is believed to make the whole system slower. The other solution is to disable USB 2.0. This will result in way slower read/write, but the connection remains stable.

To disable USB 2.0, type this in the terminal:

sudo modprobe -r ehci_hcd

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`


Gobby

---

