---
title: "Default Keyring"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by tompickles on 2007-06-12
When i enter any passwords in anything - ie my WPA in wireless networking and my IM in GAIM, i get prompted to enter a default keyring password... what is this all about?!

Thanks for any help!

---

### Post by Bohlio on 2007-06-12
I've been with ubuntu since about the middle of may, and i still dont quite know exactly. I just used the password that i normally use, And the only thing that seems to go in the keyring is the Wireless encryption key.

---

### Post by phr0ze on 2007-06-12
The keyring holds sensitive passwords to other services. To keep your passwords safe, the keyring asks for a password. This is supposed to allow you to only need to remember the one keyring password for all other services. Network passwords are also stored in the keyring.

---

### Post by tompickles on 2007-06-12
so - it's like a desktop version of saving passwords in Firefox when you use a master password?

Also, would you reccomend using it? And what are it's benefits/drawbacks?

---

### Post by Brightbelt on 2007-06-12
This thread shows you how to set it so you don't have to enter the keyring password every time:

[http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring) 

I hope this helps, Frank B.

---

### Post by Brightbelt on 2007-06-12
P.S. It only works if your keyring password is the same as your system password. So the thread tells you how to reset the keyring password if needed.

Thanks, Frank B.

---

