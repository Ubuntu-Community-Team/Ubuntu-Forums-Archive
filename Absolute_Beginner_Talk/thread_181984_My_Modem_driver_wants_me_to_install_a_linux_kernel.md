---
title: "My Modem driver wants me to install a linux kernel header."
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-25
my modem ask me that. what should i do?

---

### Post by Ben Sprinkle on 2006-05-25
you should get broadband :D screw modems and dial up ur livin in the 70's lol

---

### Post by AndyCooll on 2006-05-25
[QUOTE=Solidad]my modem ask me that. what should i do?[/QUOTE]

Either from the command line:
```
sudo apt-get install build-essential
```

Part of that process will include installing the appropriate kernel headers.

Or install them via Synaptic. Do a search "kernel-headers", and choose the ones appropriate for the kernel you are using. If you're not sure, again using the command line, type

```
uname -r
```

:cool:

---

### Post by Solidad on 2006-05-26
it took long but ok thanks.

---

### Post by az on 2006-05-26
[QUOTE=AndyCooll]Either from the command line:
```
sudo apt-get install build-essential
```

Part of that process will include installing the appropriate kernel headers.

Or install them via Synaptic. Do a search "kernel-headers", and choose the ones appropriate for the kernel you are using. If you're not sure, again using the command line, type

```
uname -r
```

:cool:[/QUOTE]
Actually, they are called "linux-headers"  If you are running the kernel you got when you installed, just install "linux-headers-386"

---

