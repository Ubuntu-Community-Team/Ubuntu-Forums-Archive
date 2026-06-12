---
title: "No sound after fixing screen brightness, 11.10"
date: 2011-11-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Kirstine on 2011-11-02
Hi!
I had a problem with increasing and decreasing the screen brightness on both 11.04 and 11.10, and I fixed it with the following. Now my the sound don't work at all, neither if I plug in headphones.
Do you know what the problem may be?

This solved the screen brightness:


1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot[/QUOTE]

---

