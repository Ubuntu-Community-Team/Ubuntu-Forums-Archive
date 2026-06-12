---
title: "upgrade kernal"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-09-12
Ok, I uninstalled some stuff I had added a few days ago that messed up my 2.6.20-16-generic kernal to where it would not boot, showed a kernal panic message, so I took it out of the menu and am wondering if all I have to do is a reinstall through synaptic. I am currently booting to 2.6.20-15-generic, It shows the 2.6.20-16-generic kernal to be installed already.:confused:

---

### Post by jw5801 on 2007-09-12
Removing it from the menu isn't uninstalling it, it's just telling grub to ignore it. Try running "sudo dpkg-reconfigure" on the package you're trying to install that you're being told is already installed.

---

### Post by atria on 2007-09-12
To uninstall the kernel you will have to do it through synaptic by removing the relevant kernel packages.

---

### Post by J11Gyro on 2007-09-12
it says after i run that it is not installed

---

### Post by J11Gyro on 2007-09-12
Is there a easy way to just reinstall it?

---

### Post by por100pre1 on 2007-09-12
If it is NOT installed try this:

```
sudo aptitude install linux-image-2.6.20-16-generic
```

If it is installed try this:

```
sudo dpkg-reconfigure linux-image-2.6.20-16-generic
```

---

### Post by jw5801 on 2007-09-12
sudo apt-get install linux-image-2.6.20-16-generic

---

### Post by J11Gyro on 2007-09-12
Ok here is what I did , 1st I tried the reconfig but still was hosed on boot so I booted into previous kernal and did a search in synaptic for the 16 kernal and did reinstall and it is now running just fine so far. thanks for the help it worked

---

