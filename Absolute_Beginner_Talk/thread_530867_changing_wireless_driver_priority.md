---
title: "changing wireless driver priority"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2007-08-20
Frustrated with trying to make the driver for my built-in ra2500 work I plugged in an Atheros based wireless card and got success.  However, network manager still tries to use the ra2500 driver first and I have to override it. Everytime.  Is there a way to make it use the Atheros driver only?

Thanks.

---

### Post by overdrank on 2007-08-21
> **BeardedOne said:**
> Frustrated with trying to make the driver for my built-in ra2500 work I plugged in an Atheros based wireless card and got success.  However, network manager still tries to use the ra2500 driver first and I have to override it. Everytime.  Is there a way to make it use the Atheros driver only?

Thanks.

Hi if you installed the driver with ndiswrapper then just uninstall the driver or disable the onboard nic card in the bios of the motherboard. :)

---

### Post by BeardedOne on 2007-08-22
Thanks.  I didn't use a wrapper, just network manager (which configured itself for the built-in wireless).  There is no place to disable the wireless in the bios of my laptop, though I do keep the built-in wireless turned off.  Is there a way to disable the driver?

---

### Post by johnl on 2007-08-22
If you know the name of the driver, you can blacklist it:

pop open a terminal and type:
```

sudo gedit /etc/modprobe.d/blacklist

```

add the driver name to the file to prevent it from loading.  If you're not sure what the driver is called, try searching for it in the module list:
```

lsmod

```
(or)
```

lsmod | grep ra25

```

Once you've blacklisted the module, either restart your computer or remove the module with the rmmod command:

```

sudo rmmod modulename

```


Hope this helps!

---

### Post by BeardedOne on 2007-08-25
Great.  Thanks.  I'll give it a try.

---

### Post by BeardedOne on 2007-08-25
Terrific!  That works exactly right.  The bad driver doesn't get in the way now.  Thanks,

---

