---
title: "xbox"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-11-04
ok im guessing there is no way to connect the xbox 360 to my ubuntu box and stream video's, pictures etc.. like i can from windows. i just want to know if there is a program that will do it? not that i need it or will use it much.

---

### Post by Kimmik on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=295433]("http://ubuntuforums.org/showthread.php?t=295433")

---

### Post by Kimmik on 2007-11-04
Here's a short howto for gutsy:

-open synaptic and search for "libupnp", install the two found packages.

-Download [http://bobshowtos.googlepages.com/ushare_1.0-1_i386.deb]("http://bobshowtos.googlepages.com/ushare_1.0-1_i386.deb") and install it.

-If you use wireless: Enter "sudo gedit /etc/ushare.conf" in the terminal and where it says &#8220;USHARE_IFACE=&#8221; after the equal sign put eth1.
USHARE_IFACE=eth1

-Run "ushare -p 49153 -x -c /path/to/my/music/files/"

Your Xbox360 should find your computer now. :)

---

### Post by DiamondX on 2007-11-07
Thanks kimmik, but I keep getting an error:
> ushare: error while loading shared libraries: libupnp.so.2: cannot open shared object file: No such file or directory

---

### Post by Kimmik on 2007-11-07
> **DiamondX said:**
> Thanks kimmik, but I keep getting an error:

Don't forget  to open synaptic and search for "libupnp". Install the two packages that you find.

---

### Post by Znort_Ubern00b on 2007-11-21
> **Kimmik said:**
> Here's a short howto for gutsy:

-open synaptic and search for "libupnp", install the two found packages.

-Download [http://bobshowtos.googlepages.com/ushare_1.0-1_i386.deb]("http://bobshowtos.googlepages.com/ushare_1.0-1_i386.deb") and install it.

-If you use wireless: Enter "sudo gedit /etc/ushare.conf" in the terminal and where it says “USHARE_IFACE=” after the equal sign put eth1.
USHARE_IFACE=eth1

-Run "ushare -p 49153 -x -c /path/to/my/music/files/"

Your Xbox360 should find your computer now. :)

Can you tell me if this works for feisty too???

---

