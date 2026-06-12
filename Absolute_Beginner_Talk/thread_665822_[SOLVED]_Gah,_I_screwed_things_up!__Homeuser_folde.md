---
title: "[SOLVED] Gah, I screwed things up!  Home/user folder problem..."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by VortexSpin on 2008-01-12
My user folder used to be File System -> Home/nick.  I renamed it, stupidly, to Nick's Files through root Nautilus and everything's gone to heck.  My desktop is gone, none of the applications work (as in NOTHING) and I don't know how to get back into root Nautilus to change the name back.  Please help me - I spent 7 and a half hours customizing and installing stuff...did I screw all of that up?

---

### Post by Rocket2DMn on 2008-01-12
You can either boot into recovery mode or just get to a TTY by doing CTRL+ALT+F1 at the login screen.  Login with root if you can, then change navigate to the /home directory and change the name.
```
(after having logged in with root)
cd /home
mv Nick\'s\ Files/ nick
```
This is assuming your login name is "nick", all lowercase.

---

### Post by VortexSpin on 2008-01-12
Thanks, I'll try it.

---

### Post by geirha on 2008-01-12
The easiest way to fix if you prefer to do it graphically, is to boot the ubuntu CD, open nautilus, double-click all the harddrives in the left margin of nautilus (this will mount them). Find out which one is the one containing your homes, then run ```
sudo nautilus
``` and rename it back. Reboot and things should be back to normal :)

---

### Post by Rocket2DMn on 2008-01-12
username is "root" rather than "nick" (or whatever your login normally is).  The password will be your regular password.
Is it letting you login with your regular username at all?  If you can't login with root, and you can still login with your username, you can login at the TTY (a terminal, text based session)
```
cd /home
sudo mv Nick\'s\ Files/ nick
```

---

### Post by bodhi.zazen on 2008-01-12
Well, you can also boot to recoverry mode and enter :

```
usermod -d <user_name> "/home/Nick's Files"
```

---

### Post by VortexSpin on 2008-01-12
Rocket's initial solution worked.  I was dazzled by the speed of response on this forum.  Good lord, you guys make it easy on noobs.

---

