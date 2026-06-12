---
title: "Installation problem PCI error"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by MicheleBetti on 2007-03-18
I'm trying to install ubuntu 6.10 on my pentium core 2 PC but I always 
receives the following errors  and the computer hungs:

[17179572.128000] PCI: JMB286x: Enabling dual function on 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 0 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 1 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 2 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 3 of device 0000:04:00.0
[17179572.128000] PCI: Error while updating region 0000.04:00.0/0 (0000b000 != 00000000)
[17179572.128000] PCI: Error while updating region 0000.04:00.0/2 (0000b008 != 00000000)

Please, someone can help me ?

Thanks in advance
](*,)

---

### Post by Kobalt on 2007-03-18
When you boot the computer and arrive at the menu (install/start, etc.) : press F6 to access the boot options then add at the end of the line (with a space before, none after)
> noapic nolapic
Then press enter to boot.
It could make it, but I don't assure you that's the problem, it's just the most common boot problem...

---

### Post by overdrank on 2007-03-18
> **MicheleBetti said:**
> I'm trying to install ubuntu 6.10 on my pentium core 2 PC but I always 
receives the following errors  and the computer hungs:

[17179572.128000] PCI: JMB286x: Enabling dual function on 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 0 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 1 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 2 of device 0000:04:00.0
[17179572.128000] PCI: Cannot allocate resource region 3 of device 0000:04:00.0
[17179572.128000] PCI: Error while updating region 0000.04:00.0/0 (0000b000 != 00000000)
[17179572.128000] PCI: Error while updating region 0000.04:00.0/2 (0000b008 != 00000000)

Please, someone can help me ?

Thanks in advance
](*,)

Hi, I had some problems installing edgy also, you may try the alternate cd at this link
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)
You may look at this link also to burn the cd
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)
Good luck and hope it works for you. :)

---

