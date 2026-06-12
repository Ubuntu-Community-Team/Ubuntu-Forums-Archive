---
title: "archlinux visudo root"
date: 2011-09-30
forum: Any Other OS
---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-30
ok. i am writing on this forum because i cant register on the archlinux forum because the registrating form is bugged or something.

i have installed archlinux now with xfce, but i cant edit the visudo file at the [B]
"ALL=[/B](ALL) ALL)      , part., i know i have to press o to type there, but i cant save the file after typing my username in there by CTRL X

---

### Post by sisco311 on 2011-09-30
To save the file press Esc then :wq

You can use another editor if you don't like vi:
```
EDITOR=/usr/bin/nano visudo
```
```
EDITOR=/usr/bin/vim visudo
```
or
```
VISUAL=/usr/bin/mousepad visudo
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-30
at the first command i can not do the command it says "visudo: /etc/sudoers: Permission denied"

and the 2 other commands dont work it says "Doesent exist"

if i try to do it as root it sais "(gedit:894): EggSMClient-Warning **: Failed to connect to the session manager: A uthentication Rejected, reason : None of the authentication protocols specifield are supported and host-based authentication failed

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOSt 
ream returned 0 bytes on async read (g-io-error-quark, 0) Exiting.

---

### Post by mips on 2011-09-30
Did you install sudo and add your user to the 'wheel' group?

---

### Post by el_koraco on 2011-09-30
> **gyyug78fg87ogguiioioioioi said:**
> 
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOSt 
ream returned 0 bytes on async read (g-io-error-quark, 0) Exiting.

You need to be root. 

```
su - 
```

---

### Post by valytzu01 on 2011-10-01
Become root with su,enter root password.After you became root you need to execute the following command
```
EDITOR=nano visudo
```

and remove the # in front of the line:

```
#%wheel  ALL=(ALL) ALL
```

---

