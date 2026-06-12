---
title: "desktop effects"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by zrx1200 on 2007-07-29
finally got fiesty fawn 7.04 to run but when i enabled desktop efects and restarted its broke dont even get to the login screen.help please.

---

### Post by misfitpierce on 2007-07-29
Maybe xorg file got messed up... When this happens to me I just erase current messed xorg with

sudo rm -r /etc/X11/xorg.conf

Use at own risk it will erase graphics setup etc in xorg which is essentially harmless to OS just need to reinput the correct settings layout.... but after that just CTRL+ALT+BCKSPC

---

### Post by zrx1200 on 2007-07-29
how exactly would i get to terminal to do that?

---

### Post by zrx1200 on 2007-07-29
the only way i can get it to work is to reistall i do n0t want to do this for a third time..thried the above commands in safe startup no good.help please.

---

### Post by Jimmyfj on 2007-07-29
Have you tried:

sudo dpkg-configure xserver-xorg

---

### Post by zrx1200 on 2007-07-30
comes up command not found.

---

### Post by zrx1200 on 2007-08-02
ok i have now reinstalled got all updates tried again same prob cant get to login screen.graphics card is g force 6200 agp slot .any one have any ideas?

---

### Post by ghanu on 2007-08-02
Boot from live cd and copy /etc/X11/xorg.conf specific to the  live cd  to the already installed partition (U need root access). Now try booting as normal. Dont forget to backup the old file.(wud require if even this fails). 
Hope this helps. 
Enlighten me if I am wrong.

---

### Post by zrx1200 on 2007-08-02
going to do another install and read up a heap more before installing the fancy stuff thanks for your help..

---

