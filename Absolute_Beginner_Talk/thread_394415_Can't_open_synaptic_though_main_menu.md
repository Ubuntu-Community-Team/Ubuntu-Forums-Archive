---
title: "Can't open synaptic though main menu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by BusSys on 2007-03-26
I can access synaptic through the command prompt but am unable to access it through system->admin->synaptic.

It flashes in the toolbar at the bottom and then dis-appears.

Any ideas?

Thanks.

---

### Post by doobit on 2007-03-26
> **BusSys said:**
> I can access synaptic through the command prompt but am unable to access it through system->admin->synaptic.

It flashes in the toolbar at the bottom and then dis-appears.

Any ideas?

Thanks.

You might have a conflict or broken link somewhere. I think you can do ```
sudo apt-get reinstall synaptic
``` and that might fix the broke links.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by BusSys on 2007-03-26
Tried sudo apt-get reinstall synaptic

comes back

E: invalid operation reinstall

any ideas?

Thanks.

---

### Post by cactaur on 2007-03-27
I think the command he meant was 

```
sudo apt-get install --reinstall synaptic
```

Try that.

---

### Post by doobit on 2007-04-04
> **cactaur said:**
> I think the command he meant was 

```
sudo apt-get install --reinstall synaptic
```

Try that.

That's it...sorry!

---

