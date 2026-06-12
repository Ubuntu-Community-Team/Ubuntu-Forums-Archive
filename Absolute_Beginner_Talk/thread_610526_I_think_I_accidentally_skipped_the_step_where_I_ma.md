---
title: "I think I accidentally skipped the step where I make a user on installation"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-11-12
I was using the text based installer and I had to go back a step to fix something. Somehow in the middle of it all  I must have skipped back over the step where I make a user name and password, so when I started the fresh install I couldn't log in. 

What's the easiest way to fix it short of reinstalling.

---

### Post by bapoumba on 2007-11-12
Can you boot at all? Can you boot in recovery mode?
Did you install with the alternate CDs? If so, the user is oem and the password should have  been asked.
To create a user _from the alternate install_ upon next reboot:
```
sudo oem-config-prepare
```

---

### Post by steve.horsley on 2007-11-12
I wonder if you chose an OEM install. If this is the case, try logging in as oem.

---

### Post by Amablue on 2007-11-12
> **bapoumba said:**
> Can you boot at all? Can you boot in recovery mode?
Did you install with the alternate CDs? If so, the user is oem and the password should have  been asked.
To create a user _from the alternate install_ upon next reboot:
```
sudo oem-config-prepare
```

I tried sudo oem-config-prepare but nothing happened. I tried typing o and then tabbing to see the options and there was no command by that name. 

Is there a way to run the install CD and just make run that one step where you choose the user and pass?

I used the CD with the text based installer. I had the option of doing an OEM install, but I didn't choose that option, I just went with the old fashioned text based install. The one with all the blue screens of options and stuff.

---

### Post by bapoumba on 2007-11-12
The oem-config-prepare takes place at next reboot.

But I am confused, how do you login ?

---

### Post by maybeway36 on 2007-11-12
Can you look at /etc/passwd?
```
cat /etc/passwd
```

---

### Post by acegeezer on 2007-11-12
Start again ! 
Best way and pay attention!

---

