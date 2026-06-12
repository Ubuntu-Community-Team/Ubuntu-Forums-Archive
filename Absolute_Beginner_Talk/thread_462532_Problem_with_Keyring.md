---
title: "Problem with Keyring"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Cerealbh on 2007-06-02
well i put in the wep key for my work and it asked me to setup a master password for nm-applet and i thought it wanted the wep key again so i put it in there so now to connect i have to put that freaking 128 bit key in there anyway i can reset it, ive deleted the keys and tried to renter them thinking that would work but no go, any ideas??

---

### Post by Cerealbh on 2007-06-02
anybody?

---

### Post by Inxsible on 2007-06-02
Go to System -- > Administration -- > Keyring Manager
Select the key and then Keyring -- >Delete Key

Then switch off your network connection...or simply try to log into another wireless, and it would ask you to enter a keyring password. Create a new password for the keyring here.

I think that should work !

---

### Post by Cerealbh on 2007-06-03
didn't work, still asking for the old key password for nm/applet

---

### Post by vanadium on 2007-06-03
Unfortunately, there is no build-in way to change the pasword other than start all over. Stop the keyring daemon typing in a command prompt:
```

killall gnome-keyring-daemon

```
then delete ~/.gnome2/keyrings (while you have a command prompt anyway:
```

rm ~/.gnome2/keyrings

```

Next time you log in, keyring manager will prompt you and then provide the correct password.

---

### Post by Cerealbh on 2007-06-03
ty your my hero

---

