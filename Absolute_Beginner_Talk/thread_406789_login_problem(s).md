---
title: "login problem(s)"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by richmi on 2007-04-11
my screen when i start says::
My GNU grub v 0.97
ubuntu kernel 2.6.15-26-386
ubuntu kernel 2.6.15-26-386 (recovery mode)
ubuntu mem test 86+
other operating systems
windows 95/98/me
ubuntu kernel 2.6.15-26-386 (on dev/hda3 )
ubuntu kernel 2.6.15-26-386 (recovery mode)(on dev/hda3 )
ubuntu mem test 86+ (on /dev/hda3)

when I allow ubuntu to auto boot up (1st entry is highlighted) when it asks for my user name and password-they are not accepted and it keeps recycling asking again, and again.
BUT when I select the item :ubuntu kernel 2.6.15-26-386 (on dev/hda3 ) it boots up normally.
How or what do I need to do to get it back to normal automatic boot  and accept my user name and pw?

---

### Post by happy-and-lost on 2007-04-11
What are your system specs? You might want to use Xubuntu if your machine's old enough to be running 95/98/me.

---

### Post by richmi on 2007-04-11
hp pavilion n5440 notebook P3 cpu 384 meg mem. It was running fine untill I got tangled up in upgrading. it will boot and run fine in the (on/dev/hda3) choice. on auto load cant get by the un/pw screen.

---

### Post by happy-and-lost on 2007-04-11
If it boots fine on /dev/hda3, boot into that and edit /boot/grub/menu.lst so that is the default choice.

---

### Post by richmi on 2007-04-11
Thanks I will try that. will be  a few hours-days to figure it out.

---

