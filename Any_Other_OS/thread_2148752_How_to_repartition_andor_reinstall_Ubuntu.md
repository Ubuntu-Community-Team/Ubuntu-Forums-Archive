---
title: "How to repartition and/or reinstall Ubuntu"
date: 2013-05-26
forum: Any Other OS
---

### Post by ruwan2 on 2013-05-26
Hi,
I want to creat a dual boot system on my desktop computer with Dell XPS. The hard drive is 1.5TB. I have installed OPENSUSE successfully. When I install Ubuntu, I incorrectly select "install along side i586 OPENSUSE". In this mode, I cannot control the hard disk partion. The total 163 GB was given to all Ubuntu. I would like to have the Ubuntu having separate partitioin for the root folder, home folder, usr local folder. Could you tell me the procedures to do this? Especially what to do with GRUB2, which is now correct to select OPENSUSE and Ubuntu.

Thanks,

---

### Post by oldos2er on 2013-05-26
You need to choose manual installation (I think it's called "Something else"). See #4 [here]("http://www.ubuntu.com/download/desktop/install-desktop-latest").

---

### Post by Bucky Ball on 2013-05-26
Yep, choose 'Something Else' at the partitioning section of the install.

---

### Post by ruwan2 on 2013-05-26
Thanks. I now know that I have to use manual install. My question is I concern the reinstall Ubuntu may ruin the present OPENSUSE in the dual boot GRUB2. Are there something I should be care about? I can simply reinstall Ubuntu by delete the present Ubuntu partition and install manually?

---

### Post by Bucky Ball on 2013-05-26
> **ruwan2 said:**
> I can simply reinstall Ubuntu by delete the present Ubuntu partition and install manually?

Yes. As for not deleting the OpeSuse install, it will be clearly visible when you get to the partitioning section. Those partitions will be shown as used and have a mount point name and other details. Just don't touch them; make sure they *_are_* set to 'Don't use' and ***not*** ticked to format. Then all good.

---

