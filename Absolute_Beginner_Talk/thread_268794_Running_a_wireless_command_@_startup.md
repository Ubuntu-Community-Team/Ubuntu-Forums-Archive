---
title: "Running a wireless command @ startup"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by theratster on 2006-09-30
Hey,

I've been trying to setup an Xubuntu system on an old PC with a wireless USB adapter (D-link G122). The ONLY way to have the adapter turn on and activate is by the following commands:

```

sudo iwconfig rausb1 essid <myIDhere>
sudo iwconfig rausb1 key <mykeyhere>
sudo dhclient rausb1

```

Now my problem is, how do I make this automatic, so that it happens during boot so that I don't have to type this in every time I boot up?

Thanks.

---

### Post by davmac on 2006-09-30
There are a couple of ways to do this. Since you're likely to want this to be run for every user, I'd put this in one of the init (boot up) scripts.

I don't know if it is the "proper" way to do it but I'd open up a terminal and type "sudo gedit /etc/init.d/bootmisc.sh".

I'd then put in the commands you want to run in at the bottom, but before the ": exit 0"

Save it and reboot...

Hope this helps,

Dave Mac

---

### Post by jaboua on 2006-09-30
Unless you need network during boot, you can add it before "exit 0" in /etc/rc.local

---

### Post by theratster on 2006-09-30
> **davmac said:**
> There are a couple of ways to do this. Since you're likely to want this to be run for every user, I'd put this in one of the init (boot up) scripts.

I don't know if it is the "proper" way to do it but I'd open up a terminal and type "sudo gedit /etc/init.d/bootmisc.sh".

I'd then put in the commands you want to run in at the bottom, but before the ": exit 0"

Save it and reboot...

Hope this helps,

Dave Mac

Thanks Dave, it worked like a charm!

I just added the codes above (without the sudo), and although it takes a few seconds longer to boot, everything works absolutely perfectly!!!

Thanks again!

---

