---
title: "networking issues as of vmware install and getting worse!"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by c4l3b on 2007-08-19
Hello all,
  This forum is, by far, the leading resource for linux help. It's quite frankly amazing.


I have 2 problems.  one is critical, one is only annoying. here they are in order of when they appeared.  For reference I'm using the latest stable ubuntu with ndiswrapper on a hp pavilion dv8000 laptop.

#1. After installing vmware server and setting up a windows install I was no longer able to browse my windows network. I can browse to the virtual machine, but not my other network.  It was fine before the install.  I'm pretty sure this is just a setting, but I haven't found it.


#2 (the critical one)  I was browsing the internet. I had made NO changes to the system in days. I pressed ctrl+t to open a new tab in firefox. It opened about 1000 new tabs, a problem I've been assuming was a glitchy keyboard(it happens with other things like switching desktops).  I closed Firefox and was notified that my connection was lost.  It will no longer connect as it was before.  When I reboot, I get a moment of connection, then it loses it again.  Wired connection seems to be working fine.

Thanks in advance for all your help,
Caleb

---

### Post by mikeyphi on 2007-08-19
> **c4l3b said:**
> Hello all,
  This forum is, by far, the leading resource for linux help. It's quite frankly amazing.


I have 2 problems.  one is critical, one is only annoying. here they are in order of when they appeared.  For reference I'm using the latest stable ubuntu with ndiswrapper on a hp pavilion dv8000 laptop.

#1. After installing vmware server and setting up a windows install I was no longer able to browse my windows network. I can browse to the virtual machine, but not my other network.  It was fine before the install.  I'm pretty sure this is just a setting, but I haven't found it.


#2 (the critical one)  I was browsing the internet. I had made NO changes to the system in days. I pressed ctrl+t to open a new tab in firefox. It opened about 1000 new tabs, a problem I've been assuming was a glitchy keyboard(it happens with other things like switching desktops).  I closed Firefox and was notified that my connection was lost.  It will no longer connect as it was before.  When I reboot, I get a moment of connection, then it loses it again.  Wired connection seems to be working fine.

Thanks in advance for all your help,
Caleb

#1. I once installed vmware server - as I recall it sets up internet access for the guest OS, so, as you say, your settings have probably been altered. Open network and check.

#2. Strange!!! Try opening preferences in Firefox (without going online) and clearing Private data....get rid of all that history, the overflowing cache, etc.!! It's worth a try.

---

### Post by c4l3b on 2007-08-19
clearing out stuff didn't help.

internet connection works fine when wired.

what network settings specifically?

---

