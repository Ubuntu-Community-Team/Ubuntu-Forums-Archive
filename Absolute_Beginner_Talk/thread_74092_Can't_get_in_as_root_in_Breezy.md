---
title: "Can't get in as root in Breezy"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by H_Roark on 2005-10-10
The title pretty much says it: I can't log in as root through the su command or through the login screen.  Sudo works just fine, but I get an error saying I have the wrong password when I try to login as root.  Am I looking at a total re-install here?

---

### Post by Leif on 2005-10-10
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

### Post by codejunkie on 2005-10-10
[quote=H_Roark]The title pretty much says it: I can't log in as root through the su command or through the login screen. Sudo works just fine, but I get an error saying I have the wrong password when I try to login as root. Am I looking at a total re-install here?[/quote] the root account is disabled in ubuntu/kubuntu by default if you want you can enable the root account with ```
sudo passwd root
``` and to login through gdm you have to go into System/Administration/Login Screen Setup and check the box that says allow root to login with gdm hope this helps.

---

### Post by aysiu on 2005-10-10
There's no root unless you set it up:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by H_Roark on 2005-10-10
Running the program from the "run as different user" command did the trick.  The whole thing threw me because in Hoary, a root terminal was always available to me.  I guess that was not supposed to be the case.  At any rate, thanks for the help.

---

### Post by Wolki on 2005-10-10
[QUOTE=H_Roark]Running the program from the "run as different user" command did the trick.  The whole thing threw me because in Hoary, a root terminal was always available to me.  I guess that was not supposed to be the case.  At any rate, thanks for the help.[/QUOTE]

To get a root terminal, just do "sudo su" in a normal terminal :)

---

### Post by codejunkie on 2005-10-10
[quote=H_Roark]Running the program from the "run as different user" command did the trick. The whole thing threw me because in Hoary, a root terminal was always available to me. I guess that was not supposed to be the case. At any rate, thanks for the help.[/quote]
if your missing the root terminal in breezy you can right click on the applications menu choose edit menu's go to System Tools and check the box for Root Terminal and you root terminal will be back again.

---

