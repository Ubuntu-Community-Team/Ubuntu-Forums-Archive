---
title: "difference between modprobe.conf and modprobe.d"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-03-24
I know one is a folder and the other is a file but are both used to run modules at startup. So why have 2 separate?

---

### Post by Whiffle on 2008-03-24
Its two different ways to do the same thing.  Both provide a means of specifying options for modules, among other things.  Modprobe.d allows it to be broken up into several files, instead of having to dig through a single file.

---

### Post by KOTAPAKA on 2008-03-24
So say I want to add ndiswrapper to modprobe.d how do I do it? I know that ndiswrapper can be added to modules.conf but just as an example to show how it works.

---

### Post by Whiffle on 2008-03-24
Well, if you want it to to load a module, you would add that module to /etc/modules.  /etc/modprobe.d/anything is just options for modules.  For example, on my thinkpad:

/etc/modules
```

thinkpad_acpi

``` 

tells it to load thinkpad_acpi on boot.

/etc/modprobe.d/options
```

options thinkpad_acpi experimental=1 fan_control=1 hotkey=enable

```
tells it to use those options any time it loads the thinkpad_acpi module.

---

### Post by KOTAPAKA on 2008-03-25
OK i got it.

---

