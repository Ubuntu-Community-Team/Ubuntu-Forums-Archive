---
title: "All static dns using Archers! And nvidia users also."
date: 2008-10-20
forum: Arch and derivatives
---

### Post by medic2000 on 2008-10-20
This has cost some trouble to us. Maybe lots of us solved but. It is worth mentioning.According to ArchWiki:

```
Configure dhcpcd

Finally, we don't want dhcpcd overwriting our resolv.conf anymore, 
since it is customized. We do, however, want dhcpcd to continue to 
automatically set out IP, default gateway, et cetera. To cause this effect, 
we will edit /etc/conf.d/dhcpcd as root, with our favorite editor. 
The directive we are looking for is DHCPCD_ARGS and by default that directive would 
look as follows:

 DHCPCD_ARGS="-t 30 -h $HOSTNAME"

Add the -C resolv.conf option to prevent the hook script from running and touching your DNS:

 DHCPCD_ARGS="-t 30 -h $HOSTNAME -C resolv.conf"

Previous versions of dhcpcd used the -R flag instead:

 DHCPCD_ARGS="-t 30 -h $HOSTNAME -R"

```



And now some of the nvidia drivers has changed. And that explained why my X 
blowed after the update(using geforcefx 5700 card): 
```

"This NVIDIA Linux graphics driver release supports GeForce 6xxx
 and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through
 the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs
 are supported through the 173.14.xx NVIDIA legacy graphics drivers."

http://www.nvnews.net/vbulletin/showthread.php?t=120679
```

---

### Post by MisfitI38 on 2008-10-20
There is a warning from pacman when upgrading dhcpcd; ```
WARNING /etc/conf.d/dhcpcd saved as /etc/conf.d/dhcpcd.pacnew
```
When you see these warnings, it's good practice to investigate them further, to see if syntax changes may dramatically impact system functionality. 
Don't be lazy, like me, and wait till something breaks.. ;)

---

### Post by medic2000 on 2008-10-20
Thanks for the advice. I usually read the warnings and notifications after installing the program. But this time i have made it very quickly. Everything occured instantly :)

---

### Post by MisfitI38 on 2008-10-20
> **medic2000 said:**
> Thanks for the advice. I usually read the warnings and notifications after installing the program. But this time i have made it very quickly. Everything occured instantly :)

```
cat /var/log/pacman.log
```
;)

---

