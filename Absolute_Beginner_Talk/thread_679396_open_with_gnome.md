---
title: "open with gnome"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-26
okay i am running openbox by its self is there anyway that i can get my gnome network settings to load with openbox because i half to boot into gnome desktop to get wireless connected and then log out and switch sessions to openbox.

---

### Post by Tenken on 2008-01-26
You could try running 

```
gksu network-admin
```

or you could try another wifi manager and add it to your autostart.sh

```
sudo apt-get install wifi-radar
```

---

### Post by fedex1993 on 2008-01-27
well problem with wifi radar every time i connect to my wireless settings it says it has found my ip and connected well actually it isnt connected at all

---

### Post by Tenken on 2008-01-27
Are you running the command with sudo? In your autostart.sh add

```
sudo wifi-radar &
```

Then edit your visudo file to not ask for a password for wifi-radar on your user account

```
visudo
```

then add this line

```
yourusername     ALL=(ALL) NOPASSWD: /usr/bin/wifi-radar

```

Once you connect to your network and create a profile, it should auto login to that network when it is available.

---

### Post by Seisen on 2008-01-27
If you can install it the package is network-manager-gnome and to run it the command is ```
nm-applet
``` or you can try WiCD 

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

