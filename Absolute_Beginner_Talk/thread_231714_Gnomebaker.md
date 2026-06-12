---
title: "Gnomebaker?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-07
i just read a thread containing some talk about gnomebaker...i read a little about this...and i want to know if it is already installed on my computer...or if i have to download it..if so where?

thanks!

---

### Post by darrenm on 2006-08-07
Not as standard, 

```
sudo apt-get install gnomebaker
```

and then you will find it in Sound and Video.

I really like it. Prefer it to K3b.

---

### Post by Jagot on 2006-08-07
It is in the universe repository which you need to enable first.  See either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then, from the terminal:

```
sudo aptitude update && sudo aptitude install gnomebaker
```

---

### Post by zxee on 2006-08-07
> **Sniper99 said:**
> i just read a thread containing some talk about gnomebaker...i read a little about this...and i want to know if it is already installed on my computer...or if i have to download it..if so where?

thanks!

Look at Applications>Sound & Video that where it would be. If it's not there use synaptic or from a terminal > sudo apt-get install gnomebaker

---

### Post by starscalling on 2006-08-07
all the gnome cd / dvd burning applications suck b/c they do not support write verification
i highly recommend you install k3b
sudo apt-get install k3b

---

### Post by flamarro on 2006-08-08
but if you do really only want gnome applications give a shot at bonfire. I think it's excellent.

---

