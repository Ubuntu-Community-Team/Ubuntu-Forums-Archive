---
title: "problem, login in to a windows domain server"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by kwacka on 2008-03-28
Its been about 10 years since I used RedHat so I'm not sure what 'network manager' front ends they used - look under Administration for whatever they have.

Alternatively,  open a terminal/console/konsole and type 'ifcong'. You will get a list of connections available.

Now type ```
ifup eth0
```

Here I'm making an assumption that you are using a wired connection on the first network card.

You may need to find out whether it is a DHCP server (if people are adding removing computers regularly there's a good chance it will be) or you need to be assigned a static IP address - you'll need to contact network administrator if it is this.

Although Ubuntu & RedHat are both linux they are different 'flavours' - e.g. in Ubuntu instead of the above the command would be 'sudo ifup eth0', so it may be better to check out a RedHat/Fedora forum.

---

