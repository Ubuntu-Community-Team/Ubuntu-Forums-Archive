---
title: "Installing a Game.. Directory?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-20
Well im installing ET
```

sh et-linux-2.60.x86.run

```

When I do all of this, I've already Chmodded... But I get to this point where it wants me to pick a path, so I decided, my home folder? 


/home/nic/games/enemy-territory or something like that.
Then it asks for something else like that.

What should I set these to?

/home/nic/?
or something else?

---

### Post by Bachstelze on 2007-05-20
What does it ask for, precisely ?

---

### Post by LollYouSuckZor on 2007-05-20
> **HymnToLife said:**
> What does it ask for, precisely ?


it says,

/usr/local/games/enemy territory
above this it says, Please enter the installation path.

When I leave it at the usr thing, and click okay, it says, that there is no write permission to /usr/local/games

I was wondering what should be the directory.

---

### Post by Bachstelze on 2007-05-20
You must run the installer with sudo.

---

### Post by LollYouSuckZor on 2007-05-20
> **HymnToLife said:**
> You must run the installer with sudo.

```
nic@nic-desktop:~$ sudo et-linux-2.60.x86.run
sudo: et-linux-2.60.x86.run: command not found
nic@nic-desktop:~$

```

---

### Post by Bachstelze on 2007-05-20
That's because it searches for it in your PATH. To search for it in the cwd, do :

```
sudo ./et-linux-2.60.x86.run
```

---

