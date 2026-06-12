---
title: "Configuring Fixed network parameters with GNOME Network Manager"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-19
Hello,

I'm running Ubuntu 6.10 on my machine and today at my work  office I got permission to connect with it to the fixed network. However, they gave me several parameters like Ip address, gateway, subnet mask, dns1 & dns2 
I don't know where to enter these data, and without that the internet doesn't work.

Any advice wold be appreciated.

Thanks in advance :)

---

### Post by Seisen on 2007-04-19
Click on System>Adminstration>Network and select your ethernet card and select properties. Change it from DHCP to Static and enter the rest of your information in the provided areas. Once your done with that hit OK and then click on the DNS tab and select Add. This is where you put the DNS server they provided.

---

### Post by O-pos on 2007-04-19
that works if you don't have GNOME network manager. If you have GNOME network manager, then it takes care of all network connections and to be able to do that, everythin in System>Adminstration>Network should be deselected - nothing should be allowed.

so I mean that I want to configure that with GNOME network manager and not with defaut network manager.

---

### Post by O-pos on 2007-04-20
I think the best solution is to uninstall this gnome network manager, then connect to my wired network normally, then upgrade my 6.10 to 7.04 and then 7.04 will have it's own improved networking tools..

can anyone tell me the command how to uninstall gnome network manager? ( I installed it with sudo apt-get install network-manager-gnome)

thanks in advance

---

