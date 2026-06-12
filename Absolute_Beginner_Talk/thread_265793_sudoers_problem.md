---
title: "sudoers problem"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by wittyguysuku on 2006-09-26
Using sudoedit under root terminal, I added my user login as below:
> # User privilege specification
root    ALL=(ALL) ALL
rsukumar        ALL=(ALL) ALL


But under user terminal, when I give **sudo make install**, it asks for password. That's fine. But when I give correct root password, it's still not allowing me to execute the command. It's giving

> $ sudo gvim
Password:
Sorry, try again.
Password:


But I could achieve the same thing log-in as root user. Could you please throw me the light?

thanks,
Wg

---

### Post by fstab on 2006-09-26
You need to enter rsukumar's password, not root's.

---

### Post by wittyguysuku on 2006-09-26
Thanks fstab!!
Thank you for educating me.

:)

---

### Post by Yosho121 on 2006-10-01
Hi...Sorry rsukumar's password?!!!:-k :-? ](*,) Never heard of it?!!:eek:  could someone please elucidate me?!!:-? 
Thanks in advance8)

---

### Post by kerry_s on 2006-10-01
If you edited the sudoers list, you had to make it writeable, if you don't change it back to not writable it gets screwed up.

Why did you need to add yourself in the first place? If your the first user your under admin. If your trying to set it up so you don't have to enter a passwd->
%admin ALL=NOPASSWD: ALL

So since it sounds like you activated the root account, login as root and right click the sudoers file> properties> and make sure its not set to write, then it should work again.

---

### Post by fstab on 2006-10-02
Hi Yosho121,

"rsukumar" is a user on wittyguysuku's computer.  It probably doesn't apply to your computer since I doubt you also have a user called that.

---

