---
title: "New annoyance"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-25
In the upper right hand corner of my taskbar i have a nice little power button icon.  It does not work though.

When I click it it kicks me to the login screen, with no options menu.  I created a new account and the power button in THAT account works.

What file must I edit to get it to work under my super user account?

---

### Post by riven0 on 2007-11-25
Try right-clicking on the power button, choose **Remove from Panel**. Then right-click on the empty spot again and click **Add to Panel**, and under **Desktop & Windows**, click the red Quit icon and add that on. It should work now.

---

### Post by Evil Wayz on 2007-11-25
> **riven0 said:**
> Try right-clicking on the power button, choose **Remove from Panel**. Then right-click on the empty spot again and click **Add to Panel**, and under **Desktop & Windows**, click the red Quit icon and add that on. It should work now.

DId that. still get logged off to login screen.

---

### Post by nickpaton on 2007-11-25
Searching a lot of posts, I found[ this thread]("http://ubuntuforums.org/showthread.php?t=588496") which amongst other things indicates an ACPI problem.

Access grub menu:

```
sudo gedit /boot/grub/menu.lst
```

Find this section (or similar to it):

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd95e4ea-30df-40dc-86f4-f6bd9374b153 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

and add

```
acpi=force
```

to give 

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd95e4ea-30df-40dc-86f4-f6bd9374b153 ro quiet splash vga=791**[SIZE="3"]acpi=force[/SIZE]**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Nick

---

