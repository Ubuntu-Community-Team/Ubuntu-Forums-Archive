---
title: "how to be able to change protected files?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by stefaan.dutry on 2007-05-16
Hello,

before i begin i'll start by saying i know very little about ubuntu (or linux at all).

I have a dual boot system with ubuntu 7.04 and windows vista.
ubuntu is set as the standard selected operating system in the selection.
I would like it to be windows (at least for the time being).

I know you can do this by changing a value in **/boot/grub/menu.lst**.
The problem is i can't safe the file after making changes.

How can i change this file?

Do i need to login as root? if so: how?

I hope someone is willing to help me with this ;)

---

### Post by Nythain on 2007-05-16
sudo is your friend... super user do... temp root privelages...
in terminal type
gksudo gedit /boot/grub/menu.lst
it should then ask for your password, and voila

---

### Post by stefaan.dutry on 2007-05-16
> **Nythain said:**
> sudo is your friend... super user do... temp root privelages...
in terminal type
gksudo gedit /boot/grub/menu.lst
it should then ask for your password, and voila

I'll try it as soon as i get home :) 

Thx for the fast respons. :D

I'll let you know if i was smart enough ;) l

---

### Post by stefaan.dutry on 2007-05-17
It worked.

I've now set windows as standard startup OS ( at least till i don't need any programs anymore that only run on windows).

Thank you for the fast response.  And i appolagise for the late posting of this succes.

what i did:

Opened terminal
[LIST=1]
[*]typed: **gksudo gedit /boot/grub/menu.lst**
[*]changed the value after **default** to the wanted one (4 in my case) (having 3 linux startup modes and a line other operating system before i get to the line with vista longhorn)
[*]saved the file.
[*]restarted.
[/LIST]

---

