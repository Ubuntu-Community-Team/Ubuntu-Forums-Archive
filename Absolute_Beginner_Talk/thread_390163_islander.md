---
title: "islander"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by islander on 2007-03-21
entering password in terminal after su all I get is :
su :Authentication failure , sorry
the su request in the terminal does not accept my password ???
I am using my administrative password . 
Running Ubuntu 6.10
looking for help

---

### Post by sad_iq on 2007-03-21
Ubuntu has no root account...therefore no "su"...just type "sudo"
 However if you want to use "su" then type "sudo -i"

---

### Post by Kobalt on 2007-03-21
In command line enter : 
```
sudo passwd root
```

---

### Post by fakie_flip on 2007-03-21
By default Ubuntu does not have a root user. If you want a root user in Ubuntu, give this command.

sudo passwd root

Otherwise you can do commands with root priveledges by putting sudo before the command for example.

sudo apt-get install epiphany-browser

---

### Post by islander on 2007-03-21
> **sad_iq said:**
> Ubuntu has no root account...therefore no "su"...just type "sudo"
 However if you want to use "su" then type "sudo -i"

thanks !     sudo -i is working ok
islander

---

