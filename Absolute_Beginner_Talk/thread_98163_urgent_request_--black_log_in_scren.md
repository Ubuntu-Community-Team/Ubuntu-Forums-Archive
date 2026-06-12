---
title: "urgent request --black log in scren"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-02
Hello
breezy badger 5.10

I have just installed a wireless driver  with dpkg -i all went well.

logged out and back in again now I get a black and white screen tty1 I think
its called anthing I can type at command prompt to see what has happened?

andy:???:

---

### Post by etc on 2005-12-02
Try ctrl + alt + F7, if that doesn't work
```
startx
```
See what happens

---

### Post by aysiu on 2005-12-02
So it's a totally black screen with some white letters that look like a command prompt?

Try Control-Alt-F7

If not, try ```
startx
```

If not, try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xstation on 2005-12-02
thanks for your posts

cnrl alt F7 nothing happened

startx after a second a sort off gray scren appeared with a white arrow head
could move the arrow head but thats all.


andy:???:

---

### Post by xstation on 2005-12-02
there are many options under reconfigure xserver -xorg.

its pretty difficult.

andy::???:

---

### Post by AndyCooll on 2005-12-02
sudo dpkg-reconfigure xserver-xorg

This is taking you through your gui screen setup again (since if you've tried ctrl+alt+F7 and startx without success it probably needs re-setting). There might be quite a lot of options as you state, however the guide does do alot of explaining what each one means. And for most of them anyway you can accept the defaults. You may only need to take careful note of the options relating to your monitor and screen settings.

:cool:

---

### Post by xstation on 2005-12-03
Yes there are many otions to choose from I worked hrough the list and
after the last one the flahing coursor returnrd at the the foot of the last message

xserver-xorg postinst warning
overwriting possibly customised config etc/x11/xorg.conf.back-up
in 200512031024

the promt appears  I then exit but on restart the same black screen appers as mentioned in my first post of this thread.

Is there something I should then type at command prompt?


andy:???:

---

### Post by xstation on 2005-12-04
can some kind person take a look at this tread for me above

thanks

andy:???:

---

