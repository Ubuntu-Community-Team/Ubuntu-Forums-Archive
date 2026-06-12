---
title: "can't fdisk now"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by shania98 on 2006-01-19
I installed ubuntu on my primary drive & found out that win98 would be better installed on primary. So in the task of trying to install win back on hd 
i can't fdisk now, it says error on disk. Do you believe ubuntu currupted my hard drive where I can't run win fdisk? and if so how can i correct this, thanks

---

### Post by matthewv on 2006-01-19
easiest thing to do:
Boot the ubuntu live cd...
Run gparted ( Application --> System Tools --> Gparted ) 
Delete the ubuntu partition. Reboot and run win98 install again. Hope that works...

---

### Post by shania98 on 2006-01-19
okay i have a knoppix cd, will that work?

---

### Post by shania98 on 2006-01-19
[QUOTE=matthewv]easiest thing to do:
Boot the ubuntu live cd...
Run gparted ( Application --> System Tools --> Gparted ) 
Delete the ubuntu partition. Reboot and run win98 install again. Hope that works...[/QUOTE]
how about that linux-swap on the right there? do i need to delete that also?

---

### Post by shania98 on 2006-01-19
[QUOTE=shania98]how about that linux-swap on the right there? do i need to delete that also?[/QUOTE]
 
Wow i like this live cd, my internet works on it too! I hope i can set up 5.10
when i'm finish loading win

---

### Post by shania98 on 2006-01-19
[QUOTE=matthewv]easiest thing to do:
Boot the ubuntu live cd...
Run gparted ( Application --> System Tools --> Gparted ) 
Delete the ubuntu partition. Reboot and run win98 install again. Hope that works...[/QUOTE]
hey my Aussie friend, got it! formatting as I type
maybe you can help me load 5.1 on my 2nd HD
i'm doing a dual boot, is this what that grub is for?
thanks again

---

### Post by jimrz on 2006-01-19
Yes, that is what Grub is for. [**[COLOR="Sienna"]Here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/") is an excellent guide to ubuntu/win dual boot install.

---

