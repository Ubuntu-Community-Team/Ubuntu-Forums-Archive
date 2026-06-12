---
title: "virtualization of xp using feisty wireless"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2007-09-20
Hi there,

I am trying to run xp in vmware server with feisty. 

it doesnt appear that there is support for wireless in vmware. Does anyone know of a workaround, or a virtualization tool that works with a host wireless connection.

thanks in advance

---

### Post by steveneddy on 2007-09-20
I have the same issue.

I actually don't have any internet connection in vmware using XP.

Frustrating.

---

### Post by pompeyjohn on 2007-09-22
polite bump

---

### Post by Jose Catre-Vandis on 2007-09-22
I have it working fine using VirtualBox and both NAT and Host Interface on a Dell laptop (although with NAT you are isolated from the local netowrk, and with HI you can see the network, but the network can't see you, because I use masquerading IPs as the std Vbox way just doesn't work)

VirtualBox is in the repositories and will co-exist with VMware Server. it is supposed to be able to read VMware images, but not many folks have reported success, so suggest you do a fresh install of an XP guest on VirtualBox

---

