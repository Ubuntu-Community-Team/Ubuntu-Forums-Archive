---
title: "Can't update, error message"
date: 2011-04-06
forum: Any Other OS
---

### Post by myolbug on 2011-04-06
Mint 9 64bit:
When I go to update, I get an error message telling me to fix broken packages and it won't allow me to update.

Besides rebooting, how do I accomplish this?

---

### Post by synapsys on 2011-04-06
Have you tried running 

```
sudo apt-get install -f
```

to fix broken packages? If this command still gives you error messages, please post them.

---

### Post by bodhi.zazen on 2011-04-06
First you should ask on the Mint forums ;)

You can try :

```
sudo apt-get update
sudo apt-get -f
```

---

### Post by Perfect Storm on 2011-04-06
Moved to Other OS/Distro Talk forum.

---

### Post by myolbug on 2011-06-08
> **bodhi.zazen said:**
> First you should ask on the Mint forums ;)

You can try :

```
sudo apt-get update
sudo apt-get -f
```

I get what you are saying.  But, in my experience, that is one SLOW forum!

---

### Post by el_koraco on 2011-06-08
```
sudo dpkg --configure -a
sudo apt-get install -f
```

You may need to repeat this a few times. Then try to update.

---

