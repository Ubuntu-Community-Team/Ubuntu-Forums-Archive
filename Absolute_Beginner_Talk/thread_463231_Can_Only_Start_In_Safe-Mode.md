---
title: "Can Only Start In Safe-Mode"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by elite-elitist on 2007-06-03
I cannot start Xubuntu. It says some module failed, and that my eeprom might be corrupted. Then it displays a black screen and hangs up, at which point I have to remove my laptop battery to shut off the PC.

However, I can start in safe-mode. What is the difference between starting in regular mode, and safe mode? If I install from safe-mode will that made any difference?

I have 256MB of RAM and a 8MB graphics card.

---

### Post by notquitemichael on 2007-06-03
i was always under the impression the main difference was Xorg (the display), you can try running the command X from your safe prompt and see if you get an error which might lead you to how to solve it.

---

### Post by annda on 2007-06-03
safe mode or recovery mode ignores all the startup services and programs. try notquitemichael's advice and if you still get the error, it means faulty installation.

---

### Post by elite-elitist on 2007-06-03
As to the faulty installation, I don't think there is anything wrong with the CD itself, as on my other computer it boots without problems.

---

### Post by elite-elitist on 2007-06-03
I run a few commands in the terminal, and it is working fine. Is that what you mean by command X? Any command, because there is no command called "x".

---

### Post by annda on 2007-06-03
if 'X' is not working, type 'startx' and see what happens

---

### Post by elite-elitist on 2007-06-03
It says the following

"xauth: creating new authority file /home/ubuntu .serverauth.7807.

x: user not authorized to run the X on the server, aborting.

Couldnt get a file descriptor referring to the console"

---

### Post by annda on 2007-06-03
sorry, this is beyond me. the only advice i have is create another user with admin privileges, log in as the new user and look into the gui user administration to see if something has gone wrong with your original user's privileges.
```

sudo useradd -m -s /bin/bash -G admin username
```

then

```
passwd username
```

---

### Post by elite-elitist on 2007-06-03
When I try to create the admin password it says I do not have the privileges to modify the password. After days of trying to get it to work I think I'm gonna throw in the towel here. There is something about this particular PC ubuntu doesn't like.

Thanks for the help everyone.

---

### Post by annda on 2007-06-03
sorry, my fault - it should be

```
**sudo** passwd username
```

you need admin rights to change this - and this is what sudo is for.

---

