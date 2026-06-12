---
title: "windows network"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Gildp67 on 2007-11-10
is it possible to network my recently now Ubuntu machine with my windows machines, for the purpose of sending files and saving emails. Caution extreme noob to linux.

---

### Post by snick_hill on 2007-11-10
depends on how you want to network.....hardwired or wirelesslessly? :-\"

---

### Post by SomethinSnappy on 2007-11-10
> **Gildp67 said:**
> is it possible to network my recently now Ubuntu machine with my windows machines, for the purpose of sending files and saving emails. Caution extreme noob to linux.

[http://ubuntuforums.org/showthread.php?t=528592](http://ubuntuforums.org/showthread.php?t=528592)

---

### Post by jimrz on 2007-11-10
> **Gildp67 said:**
> is it possible to network my recently now Ubuntu machine with my windows machines, for the purpose of sending files and saving emails. Caution extreme noob to linux.

Yes ... you will need to install samba (available via Synaptic). Depending on what all you want to do there are many useful threads here that can help you get it set up the way you need. When you modify your smb.conf file make SURE that you change the name of your WORKGROUP to match exactly your workgroup/domain name on your win boxes. Check out these threads [[COLOR="Sienna"]**_#1 _**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") + [[COLOR="Sienna"]**_#2_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") + [[COLOR="Sienna"]**_#3_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=103328") for starters. You will need to do some work in the terminal, but it is pretty much cut and paste (with a little modification to get your specifics, like workgroup name etc, correct) from the "how to" and easy to follow. May look a bit daunting but the actual process is not difficult. As ALWAYS, be sure to back up ANY current conf file before making changes.

---

