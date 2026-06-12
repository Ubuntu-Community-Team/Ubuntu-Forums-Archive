---
title: "How to link values in config files"
date: 2012-05-09
forum: Any Other OS
---

### Post by spranks on 2012-05-09
I am using Linux Mint 12 LXDE 32bit.
 
Can you link values from files to other files.  That sounds broad so let me explain.  I have a dhcp server set up on my computer, and in the config file 'dhcpd.conf' I have lines like "option routers 192.168.1.1"  
Can I link that option to look into a file called "router" that contains the value "192.168.1.1"  I have tried: 
```
option routers =/etc/dhcp/router;
```
and
```
option routers "=/etc/dhcp/router";
```but no dice.  Why I am doing this is because I want to make a bash file that asks the user input for the router IP and the user will enter what they want and it will change the value in the "router" file, hence changing the value in the dhcpd.conf file.
 
Any help would be appreciated and let me know if you need clarification on anything.

---

### Post by oldos2er on 2012-05-09
Moved to Other OS/Distro Talk.

---

### Post by spranks on 2012-05-09
I found something that could help me a ways at: [http://www.linuxquestions.org/questions/linux-server-73/set-dhcpd-conf-to-include-other-config-files-935691/](http://www.linuxquestions.org/questions/linux-server-73/set-dhcpd-conf-to-include-other-config-files-935691/)
 
Now I just need to figure out how to make user inputs to change the contents of the files with bash.

---

