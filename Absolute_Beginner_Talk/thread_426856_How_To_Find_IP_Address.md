---
title: "How To Find IP Address"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by pbhill on 2007-04-28
After many hours trying to get a wireless PCMCIA card to work (Linksys WPC54G) and reading about 35 different posts, I'm more confused than ever. But it seems I'll need a *static IP address*.
My question is: How do I find this IP address and associated information? Thanks for any help you could give a new Ubuntu user.:confused: [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by seshomaru samma on 2007-04-28
I don't know anything about wireless so this may not be what you need
but
system>admin>networking
under the 'connections' tab highlight your connection and choose 'properties'
in the poroperties tab change 'configuration' from DHCP to Static IP

---

### Post by diskotek on 2007-04-28
having a static ip address is about with your service provider. for example my service provider gives dynamic ip address everytime i switched on.

you can see your current ip address by typing in terminal:
```
ifconfig
```

---

### Post by briansvgs on 2007-04-28
Do you have any other computers on this network? If you do, then find the ip address of these computers and the ip of their gateway. To find this information, you would use the ipconfig command on a windows computer from the command line, or the ifconfig command from the command line of a linux computer. Then go to the system>admin>networking mentioned above, and type in your gateway for the gateway address, and an unused ip address on your network for the ip address.

---

### Post by zetsumei on 2007-04-28
```
/sbin/ifconfig
```

use that to get your IP address and other usefull information...

that is for linux terminal...

---

