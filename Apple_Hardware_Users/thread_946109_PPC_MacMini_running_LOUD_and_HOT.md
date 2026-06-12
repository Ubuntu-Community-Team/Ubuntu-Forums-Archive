---
title: "PPC MacMini running LOUD and HOT"
date: 2008-10-13
forum: Apple Hardware Users
---

### Post by jakedahn on 2008-10-13
Ever since I got my macbook I haven't used my mac mini. I got the mac mini a few weeks after its release in 2005 so its PPC and I've upgraded it to 1gb ram.

I installed ubuntu without incident, and I'm a fairly experienced linux user. My issue is that the mac mini is running very hot and very loud when it is doing nothing but running gnome. So I'm thinking that there are some driver issues.

Does anybody know of a fix that will keep the fan a little more quiet while the machine isnt doing anything?

---

### Post by EnGorDiaz on 2008-10-13
i dnt exactly know you problem?

explain it more i might be able to help

---

### Post by jakedahn on 2008-10-13
> **EnGorDiaz said:**
> i dnt exactly know you problem?

explain it more i might be able to help

The fan in the MacMini is going at what sounds like max rpm. While I'm in Mac OS the fan is relatively quiet but in ubuntu the fan is always going at max speed. It is loud and fairly annoying.

I'm wondering if there is a way to fix it so the fan isn't always at max speed.

---

### Post by kosumi68 on 2008-10-13
Are you running Intrepid or Hardy, what kernel version, and what is the DMI identifier for your machine? Are you running gnome? What is the output of sensors?

---

### Post by jakedahn on 2008-10-14
> **kosumi68 said:**
> Are you running Intrepid or Hardy, what kernel version, and what is the DMI identifier for your machine? Are you running gnome? What is the output of sensors?

Running Hardy with kernel version 2.6.24.19.21. Running gnome.

What is a DMI identifier and how do I find it, and what do you mean by output of sensors?

---

### Post by kosumi68 on 2008-10-14
This will output the exact version of your mac model
```

sudo dmidecode | grep 'Product Name:'

```

This program shows you sensor data, in particular fan speed and temperatures
```

sensors

```

In addition to this,
```

dmesg | grep applesmc

```
is of interest, and whether you run powernowd or anything similar like cpufreq/powersaved, etc.

EDIT: ppc... sorry about that, the applesmc stuff does not apply.

---

