---
title: "Troublesome install + freezing, imac 24&quot; C2D/kubuntu 10.4"
date: 2010-06-01
forum: Apple Hardware Users
---

### Post by Karunamon on 2010-06-01
First, the backstory.

This mac was set up with Boot Camp a long time ago, and I've been running windows 7 with no problems.

After a very slick install on my netbook, I thought i'd try it out on my main machine at home, an early 2008 model Core 2 Duo iMac.

The first thing I did was install rEFIt, on advice of the imac install guide on the wiki. Then, after an extra reboot to get that working, I boot the ubuntu CD directly.

Which fails. It seems my video card is not well liked by the system. I ended up having to add "nomodeset" to the boot options in order to get a working GUI.

After this, the system installs as expected.

Now, i'm stuck again. After getting to GRUB, I still have to do the nomodeset thing in order to avoid a "PRAMIN flush timeout" error. This works, but now I'm frozen at a "ehci_hcd" message on the screen right after my keyboard and mouse are detected.

I am able to boot recovery mode (again, putting nomodeset in the options).

Any ideas what I need to do in order to clear this error and get a fully functioning system?

---

### Post by linuxopjemac on 2010-06-02
I am not extremely familiar with GRUB, but I guess you need to adapt the /etc/default/grub file. In the GRUB_CMDLINE_LINUX_DEFAULT line you can add kernel options. So I guess you could add something like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```
sudo nano /etc/default/grub

```
edit
CTRL-X and "y" to save

Then you need to update grub
```
sudo update-grub
```

---

### Post by linuxopjemac on 2010-06-02
You might also want to try this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi=off noapic vga=792"
```

---

