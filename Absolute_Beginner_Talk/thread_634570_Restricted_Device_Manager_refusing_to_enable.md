---
title: "Restricted Device Manager refusing to enable"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by dbryan on 2007-12-07
First day with UBUNTU. Mostly a pleasant experience but I am having a problem with the restricted device driver. It shows my NVIDIA, the modem and wireless LAN but refuses to let me enable them. It takes me through the steps but ends up with a "not enabled" message.

This running Gutsy on a HP laptop zv5410us laptop

---

### Post by erfahren on 2007-12-07
> **dbryan said:**
> First day with UBUNTU. Mostly a pleasant experience but I am having a problem with the restricted device driver. It shows my NVIDIA, the modem and wireless LAN but refuses to let me enable them. It takes me through the steps but ends up with a "not enabled" message.

This running Gutsy on a HP laptop zv5410us laptop
are you connected to the internet with Ubuntu?

---

### Post by awthomp on 2007-12-07
Also, are you prompted with a screen to enter your administrator password?

---

### Post by dbryan on 2007-12-08
Yes and Yes

---

### Post by erfahren on 2007-12-08
I bet I know:
using the terminal (Applications > Accessories > Terminal) - post the output of 
```

cat /etc/apt/sources.list

```
 Actually, what you can try first is go to System > Administration > Software Sources and make sure everything is checked (except "source code", you don't really need that right now). 

close Software Sources before going to next step (only use one package manager application at a time)

If they were unchecked, do this in the terminal:
```

sudo apt-get update

```
then
```

sudo apt-get upgrade

```
if they were unchecked you should get some updates with that (reboot if it says to). 

Then try enabling the drivers

---

### Post by dbryan on 2007-12-08
Software Sources did the trick. Thank you

---

