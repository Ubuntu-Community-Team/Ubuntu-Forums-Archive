---
title: "Some network-related questions"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Drewski on 2007-04-26
Alright so, my Ubuntu system is up and running on my network. I just have a few generic questions.

1) In my /etc/hosts file, the first two entries are 127.0.0.1 and 127.0.1.1, the former of which is localhost, and the latter is my hostname. What is this 127.0.1.1? I'm familiar with loopback, but not 127.0.1.1.

2) Where can I specify what domain to put the computer on? I found how to do it in the GUI, but that's no fun. ;) I want to learn how to do it the "real" way, sans GUI. Do I put the line "domain mydomainhere" into my /etc/resolv.conf, or is the domain stored elsewhere?

3) How is a network domain related to a Windows workgroup (if at all?) I have 2 other computers on this network, both of which run Windows, and are on the same workgroup. Would a network domain be considered the same thing?

4) How come my Linux boss name doesn't show up in my router's status? In the status box it lists the IPs and MAC addresses of all 3 computers on my network (2 Windows + 1 Linux) but the Linux machine's entry doesn't have a name, whereas the two Windows' computers do. This is not critical of course, I'm just curious why it wouldn't show up.

---

### Post by Austin_KW on 2007-04-26
If you want your linux box name to show in your router edit /etc/dhcp3/dhclient.conf  and uncomment the send host-name line. Just put yourPCname in quotes.
If you look a couple of lines futher down you will see that the dhcp client is requesting the domain from the dhcp server. So if dhcp returns the domain it will be auto configured and added to resolv.conf along with the dns server

---

### Post by Drewski on 2007-04-28
Great, thanks!

But what about #1? What is 127.0.1.1? I mean I know it resolves to my hostname, but why? What's so unique about this IP address?

Also, I tried manually adding my domain to my resolv.conf file, by adding the line
domain mydomainname

But that didn't seem to work, because running hostname -d returns nothing.

---

### Post by Austin_KW on 2007-04-28
I skipped that because it has been a while since I read the rfc, but from memory;

127.0.0.0/8 is defined as the loopback address. 
i.e Any 127.x.y.z will be loopedback

It is often implemented as localhost = 127.0.0.1 but the rfc says that the entire range is loopdack
Try ping any 127 address, and they will all ping your local loopback. It is all the same thing

---

