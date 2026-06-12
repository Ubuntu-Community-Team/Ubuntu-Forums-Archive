---
title: "no apic?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by perrybergmann on 2007-06-04
I get hit with this message everytime I try to boot up.

[10.3345301]..MP-BIOS Bug:8254 Timer not connected to IO-APIC.

I have done some research and people say to go to Grubb and append it to say no apic. I have no idea what this means. I get into the Grubb menu by pressing esc at start up and it gives me these four options.

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic(recovery mode)

I have no idea which one to pick to make the changes. I have tried entering all of them but when I type no apic it says: Error 11: Unrecognized device string. I do not know what to do. I really want to remedy this situation because it seems to be making my system crash at random times. 

Does anyone have any suggestions or advice.

---

### Post by information_entropy on 2007-06-04
The one you want to changes is kernel 2.6.20-16-generic, unless you have edited grub to boot one of the others.

You can also edit grub by entering  the following at the gnome terminal. 

```
sudo gedit /boot/grub/menu.lst
```

Be very careful.  If you mess it up you may find yourself booting from a recovery CD


Add the following after the command, do not delete anything.

```
noapic  acpi=off

```
This worked for me.

Others have suggested:

```
noapic nolapic acpi=off
```

I  have not had the time to test this on an old computer.

---

