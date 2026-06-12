---
title: "vmware vista"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by silicon_chipper on 2007-12-17
Hi I am trying to get wireless working in a vmware vista image on gutsy gibbon. I just created a new vmware image and used a vista home premium cd to install vista. I know this isn't a vista forum but vista is saying it can't find any network devices. Gibbon found my card by it's self and everything is up and running but the vista image can't find the hardware or something.
Apollo

---

### Post by lswest on 2007-12-17
virtual machines use virtual bridges to wireless cards, so that there should be no problems.  Make sure that vmware has the bridge for the right wireless set up, and that that bridge is active.  as long as the wireless is connected in gutsy it should be no problem to run it (may not say it is connected, but you'll have internet)

---

### Post by 720iD on 2007-12-17
> **silicon_chipper said:**
> Hi I am trying to get wireless working in a vmware vista image on gutsy gibbon. I just created a new vmware image and used a vista home premium cd to install vista. I know this isn't a vista forum but vista is saying it can't find any network devices. Gibbon found my card by it's self and everything is up and running but the vista image can't find the hardware or something.
Apollo
set your network preferences for the vista VM to NAT your vista vm will use the hosts connection

---

### Post by iammeagain on 2007-12-22
I was wondering if i could install Vista to VMware off a recovery partition that came with my Gateway computer.  It seems unlikely cuz it probably searches for hardware preinstalled to my computer from the factory.

---

### Post by Squizz on 2007-12-22
NAT should solve most internet finding problems in Windows with VMWare.

iammeagain - I'm not aware of a way to boot vmware from an existing recovery partition, but if you find a way, please post details as it'll be very useful.  Try the [vmware forums]("http://communities.vmware.com/index.jspa") - they require registration but the developers usually respond within a few hours and they're very helpful.

---

### Post by 720iD on 2007-12-22
there is a way to use an existing drive or partition on a host machine as a drive in the VMware virtual machine. not sure how this is done but there are "how to's" about this.

---

### Post by iammeagain on 2007-12-23
Thanks for the replies, I won't have much time to try until after Christmas. But now I know there is a possiblilty.

---

