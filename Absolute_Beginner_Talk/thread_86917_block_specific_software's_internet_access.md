---
title: "block specific software's internet access"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-11-06
you can do this in Win XP using ZoneLabs' firewall. It will ask you whether you allow Program X's connection to internet and if you say no, that program cannot send or receive anything from the internet. I used to use that with most updating and configuration tools of my programs (for example, stopping Media Player's configuration tool from accessing internet) to deny them to send my comp's info.

Can you do that in ubuntu? For example, can you stop apt-get from connecting to internet to get updates, or firefox but not epiphany&lynx from loading anything? I checked Firestarter but it seems it doesn't have that feature. 

Thanks.

---

### Post by John.Michael.Kane on 2005-11-06
You can try to edit the iptables manualy. theres also guarddog which may open up some fetures that firestarter does not.

---

### Post by towsonu2003 on 2005-12-10
just installed guarddog (seems nice), but no option for firewalling applications... still very open to suggestions... 

i also have this thread (bc I forgot about this one), which didn't go too far till now :)  [http://ubuntuforums.org/showthread.php?t=99332](http://ubuntuforums.org/showthread.php?t=99332)

again, open to any suggestions - thanks

---

### Post by prizrak on 2005-12-10
AFAIK the Linux firewall uses ports rather than executables to allow or deny connections. So if you allow Epiphany Firefox will be able to go as well since they both run on the same port. Also you might want to change your policy to whitelist outgoing traffic (default is blacklist meaning that all traffic is allowed unless otherwise specified)

---

