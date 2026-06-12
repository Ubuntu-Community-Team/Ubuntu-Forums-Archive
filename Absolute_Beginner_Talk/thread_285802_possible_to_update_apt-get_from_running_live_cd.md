---
title: "possible to update apt-get from running live cd?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by jamaas on 2006-10-27
I have a broken partially installed edgy system and can not update the files using apt-get, network probs and behind a firewall.  I can however get everything running using the live cd.  Is there a way to start with the live cd, and then do the apt-get update and upgrade on the main system using the proper sources.list?

Thanks

Jim

---

### Post by nereid on 2006-10-27
You must chroot into your main system.

Boot with your live system and mount your root partition. Then 

```

chroot /folder/where/your/root/partion/is/mounted

```

After chrooting your partition simply call sudo apt-get update && sudo apt-get upgrade. This should do the trick.

---

### Post by g3k0 on 2006-10-27
how do you mount the root partition?  
My network wont let me download one of the files on the  internet so i downloaded the iso.  I want to upgrade to edgy from the cd but when I do it tries to download that file on the internet again and fails.  This seems similar to my problem so I was going to try it but am pretty new to linux.  Can anyone translate for me how to mount my root partition?

---

