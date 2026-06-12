---
title: "adding a network computer"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-09-22
ok i have 3 xp computers on my homer network and 1 ubuntu(mine) i can see one of these computers in my network places. i just want to know how i can add the other computers? they all have file sharing enabled.

---

### Post by Sunforge on 2007-09-22
If it's a simple peer to peer network, make sure that all your machines have the workgroupname set identically and, after a while, one of your machines will become the "master browser" which means that it will gather and distribute a list of network resources to all the other PCs on your network. All the other machines will refer to this one to obtain a list of resources.

In order for the master browser to obtain a list of network resources it's best to switch all your machines on and leave them on for a while as they advertise their services to each other.

If you don't have everything in the same workgroup you'll get the same effect but you can find that authentication (with XP) gets a little less convenient because of the way Microsoft prepends the workgroup or domain name to your username.

Linux boxes should be able to browse a Microsoft peer to peer or domain network out of the box.

If you want chapter and verse on peer to peer networking here is a Microsoft technet article. Strange posting a Microsoft article in the Ubuntu forum but there you go, we live in a mixed vendor world:

[http://www.microsoft.com/technet/network/p2p/p2pintro.mspx](http://www.microsoft.com/technet/network/p2p/p2pintro.mspx)

---

