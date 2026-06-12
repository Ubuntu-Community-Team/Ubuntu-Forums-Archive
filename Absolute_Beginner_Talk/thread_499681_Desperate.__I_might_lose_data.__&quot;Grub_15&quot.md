---
title: "Desperate.  I might lose data.  &quot;Grub 15&quot; error"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by querent on 2007-07-12
Hi.  So my pc was running extremely slowly and got confused when I told it rm -r instead of rm -rf to move a directory.  I killed it with ctrl c and it bugged hard.  now when I try to boot, I get a Grub 15 error.  There's a small spreadsheat on the harddisk that I'd really not like to lose.  I booted from the installation (7.04) disk, and got the harddisk to register on the desktop the way cd's and such do.  But I have no permission to do anything.  I tried sudo at the command line (not knowing what password it would expect), but it claims directories that are obviously there, aren't.  what the hell can I do?

---

### Post by drowner on 2007-07-12
Wait..... first things first.

What did you type in after 'rm -r' and why did you want to use rm -r?

For instance if it was rm -r /home/user/photos that wouldnt be an issue, but if it was rm -r / thats more concerning

---

### Post by Raineer on 2007-07-12
If you typed rm -r from the root directory, don't assume that the directories are there anymore.  Don't mean to scare you but that's why people tell everyone to be so careful with sudo (and one GREAT reason why ubuntu is awesome for not letting you login as root)

If you boot from the live CD, the password for sudo is just [enter], there is no password

---

### Post by querent on 2007-07-19
thanks

---

