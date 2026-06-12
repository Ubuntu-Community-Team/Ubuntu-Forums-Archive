---
title: "installing other OS messed up existing boot list!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-05-26
Hi all! having installed another linux OS (PClinuxOS) on a second hard drive the grub loader has somehow messed up the boot list for Ubuntu. I had  Ubuntu Dapper on (1) partition Ubuntu 7.04 on another partition.I do not have 'Feisty'any longer on the boot menu list. I did reinstall grub in the process so this may have been my error which has caused this problem.
I have included some attachments which show the present situation. Any help appreciated!

---

### Post by tchoklat on 2007-05-26
what do you get when u boot

---

### Post by Sbarton on 2007-05-26
> **tchoklat said:**
> what do you get when u boot

Have a look at the attached menu list and that is what I get at boot up, the only selection is 'dapper'
thanks

---

### Post by Sbarton on 2007-05-26
> **Sbarton said:**
> Have a look at the attached menu list and that is what I get at boot up, the only selection is 'dapper'
thanks
I have added another attachment showing exact bootup option.

---

### Post by confused57 on 2007-05-26
You can probably use configfile to boot PCLinuxOS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Maybe an entry similar to this, depending on which is your root partition:
```
title        PCLinux on /dev/hdb1
savedefault
configfile   (hd1,0)/boot/grub/menu.lst
```

---

### Post by Sbarton on 2007-05-28
> **confused57 said:**
> You can probably use configfile to boot PCLinuxOS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Maybe an entry similar to this, depending on which is your root partition:
```
title        PCLinux on /dev/hdb1
savedefault
configfile   (hd1,0)/boot/grub/menu.lst
```

Apologies for long delay for reply. Before looking at reply I had deleted the PCLinux partition which led to other problems (all human). Since then I have reinstalled 'Feisty' and all seems OK at present. Let me thank you for your reply anyway.
Regards to you.

---

