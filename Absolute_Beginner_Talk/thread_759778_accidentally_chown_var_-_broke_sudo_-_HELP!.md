---
title: "accidentally chown /var - broke sudo - HELP!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by bradlewa on 2008-04-19
You guys are going to laugh/sigh/shake your head at this one.  So I mistakenly did the following:
```
sudo chown -R bill /var
```

which i assume changed the permission of everything in /var to my username from root.  now i can't change anything back.  i tried the following:
```
sudo chown -R root /var
```

but was told: 
```
sudo: /var/run/sudo owned by uid 1000, should be uid 0
```

and then tried,
```
chown -R root /var
```

which returned a lot of text, but each one ended in:
```
chown: changing ownership of `/var': Operation not permitted
```
or something to that effect.

is there anyway for me to fix this?  thanks.

bill

---

### Post by quirks on 2008-04-19
Try this:

1. Reboot your machine.
2. When it says "Press ESC to enter GRUB boot menu ... 3 ... 2 ... 1" press escape.
3. Select the uppermost entry that ends on (recovery mode) and press b.
4. The system boots into command-line mode with root privileges.
5. When it is done, enter this command:
```
chown -R root:root /var
```
6. Reboot the system with this command:
```
reboot
```

If this doesn't work, we can still try it with the live CD (which you hopefully have at your hands).

---

### Post by bradlewa on 2008-04-19
that seems to have worked.  thanks.  i usually prefer to just try things like that and see if they work, but i didn't want to end up causing anymore problems than i already have, which is why i posted.

thanks again - much appreciated.

---

