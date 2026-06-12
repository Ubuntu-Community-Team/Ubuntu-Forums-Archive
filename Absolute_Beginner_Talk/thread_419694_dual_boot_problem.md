---
title: "dual boot problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by cmagan on 2007-04-23
i completed installing Ubuntu for the first time!!!
when i restart i get a window that let me chose the o.s. but, the keyboard arrows do not respond and after 10 sec ubunto starts automaticly.
someone knows what can i do?

thanks

---

### Post by LaRoza on 2007-04-23
What other OS do you have, what keyboard do you have and what does the screen say at startup?

Your computer specifications would be useful too.

---

### Post by adrian15 on 2007-04-23
Disable or enable the usb keyboard in your bios.

adrian15

---

### Post by cmagan on 2007-04-23
my other os is widows 
i use logitech cordless desktop ex110 keyboard

---

### Post by LaRoza on 2007-04-23
Did you enable the keyboard in the BIOS setting as written above?

---

### Post by cmagan on 2007-04-23
can you explain me how do i do that?

---

### Post by XTREEM|RAGE on 2007-04-23
> **cmagan said:**
> can you explain me how do i do that?

That really depends on your BIOS version, manufacture etc :x
Just look at the loading screen to know what button to push to get in to the bios

---

### Post by cmagan on 2007-04-23
succeeded!!
now in the only user of this computer who uses ubunto, the others use windows.
how do i make windows the default os?

---

### Post by LaRoza on 2007-04-23
You might want to make people choose explicitly what they want to use, so you are able to use Ubuntu easier, but you can set the BIOS to boot from a certain device or partition. If you set it to boot from a partition first, you wouldn't be able to boot from a disk easily.

---

### Post by adrian15 on 2007-04-23
You can use sudo gedit /boot/grub/menu.lst from a console and then...

default 0

change it for default 1 or default 2 depending on the windows entry number.

adrian15

---

### Post by Cypher on 2007-04-23
> **cmagan said:**
> succeeded!!
now in the only user of this computer who uses ubunto, the others use windows.
how do i make windows the default os?
You can edit the GRUB menu file to decide which OS is the default option.
```

gksudo vi /etc/grub/menu.lst

```
However, read the the top portion of this file and you will see an option called "default" and you can set it to "saved" and what that does is to remember what your last booted OS was and automatically choose that for you the next time around. This is how I have it set up, so I usually boot into Ubuntu, but once in a while into XP and I can choose that. You would do the exact opposite, but you would only have to boot into Windows once for it to remember.

Regards

---

### Post by Sef on 2007-04-23
> how do i make windows the default os?


Read this [thread]("http://ubuntuforums.org/showthread.php?p=2449451").

---

