---
title: "system administration menus disabled?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by no.t on 2007-06-03
I use Feisty for two weeks, and now most of the icons in System-Administrtaion menus suddenly disappeared (only left:  Keyring Man., Network tools, Printing, System Log,  Sys monitor, Update Man.  All the others disappeared e.g Synaptic).:confused:

I tried to right click-Edit menus-System-Administration, but when I check a checkbox, it turns off after a second.
for me It seems to be a no-rights-problem, altough I use my install-time first user.
I don't even have another user,
I can't remember, maybe chmod'ed something that caused the trouble?

I tried to start manually package manager in terminal:

cd /usr/sbin
synaptic

program started, but got a  warning "started without adm. privileges", and i got an inactive "apply" button.

when i tried 

cd /usr/sbin
sudo synaptic

asked for the password, i entered my user passwd, then nothing happened, got the prompt back.


How to restore my System-Administ menu?

---

### Post by icechen1 on 2007-06-03
You removed your administrative permissions.I think you have to go in recovery mode in GRUB.and 
tape sudo nano /etc/group and add yourself in ```
admin: x :114:
``` line
Exemple,mine is admin: x :114:icechen1

---

