---
title: "nvidia drivers problem!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by 1normalguy on 2007-08-23
Hi , I'm completely new to linux operating system. I recently installed ubuntu 7.04 ( feisty fawn) in my system. Then I tried installing beryl for which I took help of forums. A procedure to install beryl is given in this link URL="http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html"]http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html[/URL]
. Here in the thirp step when I installed nVidia drivers and restarted my system, I couldn't get my desktop back.

---

### Post by Hobo Joe on 2007-08-23
To install you drivers, follow these instructions. This can be done from text mode.

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

dpkg -i /home/<username>/envy_0.9.7-0ubuntu8_all.deb

envy -t

```

Press the option that says 'install nVidia driver'. Then just answer the questions and it will install for you. Make sure to let it configure X for you.

---

### Post by 1normalguy on 2007-08-23
Your solution requires internet connection. I could only work on command prompt on a black screen and cannot connect to internet without desktop.

---

### Post by tseliot on 2007-08-23
> **1normalguy said:**
> Your solution requires internet connection. I could only work on command prompt on a black screen and cannot connect to internet without desktop.
Ok, get back to the desktop in this way:
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by sailor2001 on 2007-08-23
and remember to system/administration/restricted drivers manager

---

### Post by 1normalguy on 2007-08-23
I selected vesa and I have my desktop back, but I cannot enable desktop effects now and the desktop is not as before.

---

