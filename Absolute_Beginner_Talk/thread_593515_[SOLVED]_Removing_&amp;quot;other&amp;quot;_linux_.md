---
title: "[SOLVED] Removing &amp;quot;other&amp;quot; linux to install Ubuntu"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by m005k on 2007-10-27
I want to install Ubuntu on my desktop. I currently have Suse 10 installed. I know there is a command I can use in windows to completely remove Linux and the grub installer so I can start fresh. I think it is something like "make dr". Could someone inform me of the exact comands to put in so I can give Ubuntu 7.10 a try?


Thanks,

Mike

---

### Post by Duck2006 on 2007-10-27
With the ubuntu linux install, over write the suse 10 install. When it comes to the partition part do a manual partition and tell it to fromat the suse partition and tell it that thats where you want the ubuntu install to be. Grub will reinstall it self and over write the MBR.

---

### Post by leg on 2007-10-27
The command your talking about only needs to be used if you want to remove grub completely to re-install Windows.

---

### Post by m005k on 2007-10-27
When I get to that pat of the manual partition, it won't let me format. It says it has no root. It might let me delete it--would that work?

Mike

---

### Post by Duck2006 on 2007-10-27
> **m005k said:**
> When I get to that pat of the manual partition, it won't let me format. It says it has no root. It might let me delete it--would that work?

Mike

Yes delete it and then tell it that it's 

/    

root and then tell it to format it.

---

### Post by m005k on 2007-10-27
thanks--I'm doing this on Ubuntu 7.1. I can't remember how to close a topic. If you tell me how I will.

Mike

---

### Post by Maestro23 on 2007-10-27
> **m005k said:**
> thanks--I'm doing this on Ubuntu 7.1. I can't remember how to close a topic. If you tell me how I will.

Mike

Mark SOLVED with Thread Tools.

---

