---
title: "Has anyone installed vpnc-0.4.0, and be willing to help?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by dthompto on 2007-03-20
I was able to download the .tar.gz, expand it into /opt/vpn, and now I'm not sure how to proceed. I found an application called KVpnc, listed as a wrapper for most vpn clients but I'm not sure how to configure these two items to work together.

Thanks in advance to anyone who would be willing to help.

---

### Post by KenSentMe on 2007-03-20
Is there a specific reason why you don't use the vpnc version that is in the Ubuntu Repositories? 

You can install the package through synaptic (search for vpnc) or from terminal with:

sudo apt-get install vpnc

---

### Post by dthompto on 2007-03-20
oh, I didn't realize, I'll try your command line suggestion. Thanks

---

### Post by dthompto on 2007-03-20
that seemed to work. pardon my ignorance, can you tell me where it installed it?

---

### Post by KenSentMe on 2007-03-20
Most applications put an 'executable' in /usr/bin. This mean most of the time you can run it from terminal just by typing 'vpnc'.

---

### Post by dthompto on 2007-03-20
Thanks. I have it working. Now I need to get with my network admins for specific profile settings.

---

