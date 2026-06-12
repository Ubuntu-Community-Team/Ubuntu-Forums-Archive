---
title: "Editing .conf file"
date: 2011-09-27
forum: Apple Hardware Users
---

### Post by Alexzasha on 2011-09-27
Hi!

I´m really new to editing .conf files and I really need to edit one. As I don´t have sufficient permissions to do it in TextEdit on my Mac I have to do it i sudo I figured. Unfotunately I do not understand how sudo works.

I need to edit a file called tvmobiliservice.conf.
In terminal I typed "sudo pico /etc/tvmobili/contents/conf/tvmobiliservice.conf", I typed my passwords and sudo opened. I need to edit a line "LaunchSubprocessAsUser=zorwar15" into that file. Unfortunately I have no idea what to do from here. How do I do it?

Thanks in advance!

---

### Post by Blasphemist on 2011-09-27
That command is opening the file in pico for editing and with super user rights via the sudo part of the command. Pico is what you don't know how to use. I don't use it. I use gedit and it will be obvious to you how to use it to. Just substitute gedit for pico in the command. If by some chance you don't have gedit installed, just use the software center or the synaptic package manager to install it.

---

### Post by Alexzasha on 2011-09-29
Thanks a lot for your help. I had to do it a bit differently, but the installation of gedit was crusial. Thanks a lot!

---

