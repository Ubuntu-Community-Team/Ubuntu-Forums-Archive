---
title: "new apple bluetooth keyboard/mouse"
date: 2007-12-22
forum: Apple Intel Users
---

### Post by brandon333 on 2007-12-22
will not work with ubuntu, i see the bluetooth preference and has "add devices" but when you open that it dont give an option to type anything, so how do you add devces.

---

### Post by z0mbie on 2007-12-23
I'm not sure how the apple keyboard mouse synchronizes, but usually most devices have a red button to activate the process. Find that button.

**1**. Search for the button in terminal by typing:
```
sudo hidd --search
```

You will see  msg that says:

> Searching...
[B]
2[/B]. Press the synchronize buttons on the devices.

If the sychronize is successful you should get a msg similar to bellow in terminal saying:

>         Connecting to device 00:07:61:32:64:93

Now you should have both devices connected.

---

### Post by brandon333 on 2007-12-23
**This post could be related to an Ubuntu bug filed at**: r [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ok thanks..worked perfect, however audio buttons not working.

---

### Post by brandon333 on 2007-12-23
huh?

---

### Post by brandon333 on 2007-12-23
anyoneknow how to fix the volume, when i touch them it does nothing , i set the shortcuts up so it works that part just doesnt effect sound.

---

