---
title: "Restor default driver for ATI?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by sccrstvn93 on 2007-09-16
is there a way to go back to the default ati driver? I have a radeon 9250.

---

### Post by w4ett on 2007-09-16
Boot into recovery mode From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "ati" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

---

### Post by sccrstvn93 on 2007-09-16
thx

---

### Post by sccrstvn93 on 2007-09-18
how do i boot in recovery mode?

---

### Post by w4ett on 2007-09-18
Select recovery from the grub menu:

---

### Post by sccrstvn93 on 2007-09-18
thx, but when i try to do the command i get an error: "overwrite possible custom configuration"

---

### Post by w4ett on 2007-09-18
That is not an error...when you reconfigure your xorg.cong, you want to modify the file...it is correct to do so.

---

### Post by sccrstvn93 on 2007-09-18
after i type the command in nothing happens. It just gives me that message.

---

