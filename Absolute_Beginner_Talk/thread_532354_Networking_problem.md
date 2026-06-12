---
title: "Networking problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by charliehorse on 2007-08-22
Hi i have installed feisty on 2 pc's networked via a router connected to the net at home.
I followed this tutorial to set up samba [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) to network to my other windows machine. Everything works fine i can send files across the network to  the windows pc, i can ping the router fine. What i cant do know is network between the 2 feisty pc;s. 
The machine setup up with samba cant ping the other machine yet the machine not setup with samba can ping the machine setup with samba.
Do i need to setup samba on the other pc for networking to work?

Thanks

---

### Post by phr0ze on 2007-08-22
Are you pinging with computer names or using IP's? I'd try it with IP's as it simply might be a name service issue.

---

### Post by charliehorse on 2007-08-22
Hi yes im pinging with ip's. If i ping my router it works as expected but if i ping the second pc this is what i get.
mark@mark:~$ ping 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable
From 192.168.1.5 icmp_seq=4 Destination Host Unreachable

i have now installed samba on the second pc and can now see the shared folders on it but still cant ping the pc. Im trying to setup a remote desktop but when i run vncviewer -fullscreen 192.168.1.6:0
it cant reach the other pc.

I have just noticed that on the first pc the only option i have for sharing folders is samba on the other pc it gives me 2 options samba and i think it says something like linux sharing.

---

### Post by charliehorse on 2007-08-22
Ok i went back to the second pc and its nfs thats missing from the first pc.
If i install the nfs services will this cure the problem.
I dont want to mess around to much as apart from not being able to ping the second pc and not being able to remote take over the second pc everything is working as it should including the internet.

---

