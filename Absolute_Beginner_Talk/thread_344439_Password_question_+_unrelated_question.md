---
title: "Password question + unrelated question"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by SolaceAvatar on 2007-01-22
When I hit su in the terminal, it doesn't accept my password. But when I try to install something another way and it asks for the administrative password, it works just fine. Any idea what's up with that?

Also, I have my computer on a dual boot between Windows and Ubuntu. Since I'm rather new at Linux, I still use windows more often, but it's been set to automatically load Ubuntu in ten seconds if I don't choose windows quick enough. Is there any way to switch that around, at least until I get better at Linux?

---

### Post by Shatrat on 2007-01-22
su doesnt work because there is no root account in Ubuntu.  You could use su to switch to being another user, but using it without any argument (and therefore trying to switch to root) wont work because there is no root.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
For your second question, you just need to change the default selection in your /boot/grub/menu.lst file.
I just checked and in the menu.lst it isnt that obvious how to change teh default choice, but there should be a line that says 'default 0' early in the menu.lst, just change it to 'default 4' or whatever is the number of your windows entry

---

### Post by jimrz on 2007-01-22
> **SolaceAvatar said:**
> When I hit su in the terminal, it doesn't accept my password. But when I try to install something another way and it asks for the administrative password, it works just fine. Any idea what's up with that?

Also, I have my computer on a dual boot between Windows and Ubuntu. Since I'm rather new at Linux, I still use windows more often, but it's been set to automatically load Ubuntu in ten seconds if I don't choose windows quick enough. Is there any way to switch that around, at least until I get better at Linux?

use "sudo" not "su" for ubuntu

---

### Post by Bachstelze on 2007-01-22
As for the default OS setting in GRUB, see [here](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS).

---

### Post by SolaceAvatar on 2007-01-22
Thanks. ^^
> **Shatrat said:**
> For your second question, you just need to change the default selection in your /boot/grub/menu.lst file.
Err... is that in Ubuntu, Windows, or somewhere in my Bios?

EDIT: Wasn't fast enough. XD Thanks again.

---

### Post by Atomic Dog on 2007-01-22
If you really want to be root you can type "sudo su" and then just enter your password.  You will be root at the prompt.

---

### Post by Bachstelze on 2007-01-22
*sudo -i* is recommended to get a root shell, rather than *sudo su*.

---

### Post by Atomic Dog on 2007-01-22
> **HymnToLife said:**
> *sudo -i* is recommended to get a root shell, rather than *sudo su*.

I did not know that!  What's the difference?  Same # of keystrokes :)

---

### Post by Bachstelze on 2007-01-22
*man sudo* could have told you that the -i switch simulates an initial login, instead of just running the shell executable as root, thus setting the user env correctly. I guess *sudo su* will do that too, so it's indeed more or less the same but *sudo -s* or *sudo bash*, which we see quite often, are definitely bad ideas.

---

### Post by Atomic Dog on 2007-01-22
Danm!  I feel like I just got beat up! :D

---

