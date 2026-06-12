---
title: "Hardware identifier, eg what mainboard do I have."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-15
Hi,

What hardware identifier do you recommend for ubuntu? Device Manager doesn't give clear enough information. I am looking for a program to identify a box's mainboard, and other hardware devices.

I know I can check this visually, but I would prefer software for ease of use.

Thank you.

---

### Post by vigleik on 2006-06-15
[QUOTE=u.b.u.n.t.u]Hi,

What hardware identifier do you recommend for ubuntu? Device Manager doesn't give clear enough information. I am looking for a program to identify a box's mainboard, and other hardware devices.[/QUOTE]

"sudo lspci -v" should give you a detailed list of your hardware. For a slightly different list you can use hwinfo (available through apt-get).

Vigleik

---

### Post by u.b.u.n.t.u on 2006-06-15
vigleik thanks.

"sudo lspci -v" = pci ?

I was about to install hwinfo when I saw an entry for lshw.

Remembering my ultra basic linux command line ability I saw "ls" and "hw". (list hardware). All pleased I raced for the terminal and opened it. Sudo, remember Sudo I said to myself as I began to type,

```
sudo lshw 
```

There it was, the details of the mainboard in the box and other useful goodies of hardware knowledge.

Now to find the manual and check the allowable FSB settings for the new CPU I got today - this is my custom ultra quiet box, the only fan is part of the the PSU.

---

