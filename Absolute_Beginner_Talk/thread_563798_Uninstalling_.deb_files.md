---
title: "Uninstalling .deb files"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-09-30
My little brother, trying to be cool, downloaded the .deb file of limewire onto my computer. Now I can't get it off.

I've run
```
sudo dpkg -r LimeWireLinux
```
Into the terminal but that doesn't work.

Please help.

---

### Post by Steveway on 2007-09-30
Did you try to use Synaptic to remove it?

---

### Post by capitalistpiglet on 2007-09-30
try 
```

sudo dpkg -r -P packagename

```
If that doesnt work post the error message you get.

---

### Post by Taters on 2007-09-30
I thought synaptic only uninstalled programs on synaptic..
I'll try it.

and its said  that -p -r are conflicting messages.

Synaptic didn't work..

---

### Post by crjackson on 2007-09-30
> **Taters said:**
> I thought synaptic only uninstalled programs on synaptic..
I'll try it.

and its said  that -p -r are conflicting messages.

Synaptic didn't work..

Well it's a lower case -r and an upper case -P

Are you trying to delete the *.deb file itself or uninstall the package?

---

