---
title: "Software sources problem :S"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2008-01-26
Whenever I try to install anything an error keeps coming up saying 

'W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5'

What can I do to stop it saying that?

---

### Post by Paul820 on 2008-01-26
Enter this in the terminal
> wget [http://us.ubuntu.cafuego.net/AF425CB5.gpg](http://us.ubuntu.cafuego.net/AF425CB5.gpg) -O- | sudo apt-key add -
then run
> sudo apt-get update

---

### Post by Kilz on 2008-01-26
> **Ionamay said:**
> Whenever I try to install anything an error keeps coming up saying 

'W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5'

What can I do to stop it saying that?

By following the instructions [on the repository page ]("http://ubuntu.cafuego.net/")for the repository you added.

```
wget http://au.ubuntu.cafuego.net/AF425CB5.gpg -O- | sudo apt-key add -
```

---

### Post by Ionamay on 2008-01-26
I did that and it said
Get: 5 [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release.gpg [189B]
Ign [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego/bcm43xx Translation-en_GB
Hit [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release
Err [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release
  
Get: 6 [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release [50.8kB]
Ign [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release
Hit [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego/bcm43xx Packages
Fetched 51.0kB in 3s (14.8kB/s)
Reading package lists... Done
W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5
W: You may want to run apt-get update to correct these problems

So i did apt-get update and it said the exact same thing all over again

---

### Post by aysiu on 2008-01-26
Maybe something's wrong with the cafuego server right now.

---

