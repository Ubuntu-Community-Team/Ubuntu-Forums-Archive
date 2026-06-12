---
title: "booting problem, must use text mode"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by zora123 on 2007-07-18
since the first time i installed it, my little ubuntu baby cannot boot successfuly on its own.

i will only get a blank black screen unless i give it a hand.

i have to switch to text mode (console?) by pressing alt-F1.
there are some text on the display that looks something like this:

```

starting up
loading, please wait
usplash: setting mode 1152x864 failed
kinit: name_to_dev_t (/dev/sdb5) = sdb5(8,21)
kinit: trying to resume from /dev/sdb5
kinit: no resume image, doing normal boot

```

would anyone tell me whats wrong with my ubuntu?

---

### Post by Cappy on 2007-07-18
Use boot parameter ```
nosplash
```
You will also need to add this onto /boot/grub/menu.lst after you install.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by zora123 on 2007-07-19
thanks, cappy. it works!

in file /boot/grub/menu.lst, i changed the following line:

```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9b57a242-f9e7-49a7-aa31-0907adcab868 ro quiet **splash**

```

to:

```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9b57a242-f9e7-49a7-aa31-0907adcab868 ro quiet **nosplash**

```

and my ubuntu is now able to boot by itself.

but then comes the next question: is it possible to boot in graphic mode instead of in text mode?

---

### Post by Cappy on 2007-07-19
I'm not sure what you are asking. Are you asking if it is possible to have the splash screen when you boot up?
You can try changing /etc/usplash.conf:
```
gksudo gedit /etc/usplash.conf
```

to maybe
```

# Usplash configuration file
xres=1024
yres=768

```
or whatever your monitor's native resolution is. It may or may not work. You'll obviously have to change "nosplash" back to "splash" to test it.

---

### Post by zora123 on 2007-07-19
i had just tried to modify the /etc/usplash.conf as you suggested.

xres=1024
yres=768

and changed back the boot parameter from nosplash to splash.

my ubuntu "hang" again on booting process.
and i had to give it an alt-F1 again to help it.

well, i guess i have to choose "the better of the bads"...
booting in text mode is good enough compared to "cannot boot unless altF1-ing"
:D

---

