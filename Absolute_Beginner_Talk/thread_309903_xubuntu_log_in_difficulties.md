---
title: "xubuntu log in difficulties"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by electro_man on 2006-11-30
help i've just installed xubuntu oem version and I'm having difficuly logging in I am getting confused when i was  installing Xubuntu it asked for a hostname which i left as ubuntu. however when i get to the log in screen it asks for a username. I tried to put the hostname in and it didn't work. I take it that the host and   usernames are different. I know my password is correct so any help would be appreciated.

:-k

---

### Post by taurus on 2006-11-30
If you pick the oem, then your username is oem, not hostname.  Hostname is the name of your machine...  After you log in with oem as your username and your actual password that you've created during the installing process, you need to run an extra command to create an account for yourself.

```
oem-prepare-config
```

---

### Post by electro_man on 2006-11-30
thanks that seems to have done the trick.

---

### Post by taurus on 2006-11-30
After it created a new account for you, it would remove the oem from your system so no need to worry about the oem thing anymore...  ;)

---

### Post by electro_man on 2006-11-30
i've gone into the terminal and i put in oem-prepare-config and it asks for my password. However the cursor is frozen and i'm unable to enter a password. Apart from that everything else appears to work

---

### Post by taurus on 2006-11-30
The cursor didn't freeze.  It just didn't show you the length of your password when you typed it!!!

---

### Post by electro_man on 2006-11-30
thanks for the help. just trying xubuntu and linux for the first time on an old computer I've asked in another thread for support videos. I rememeber seeing some support videos on an ubuntu website they were embedded youtube videos however i'm unable to find the site through a google search.

---

