---
title: "How do I connect to a VPN?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by dloudy on 2007-08-29
Can someone tell me where to start in order to connect to my Company's VPN?

I am running Feisty and am having no luck.....and yes.....I'm new to Ubuntu...:)

Thanks,
Derek

---

### Post by benhall on 2007-08-29
Go to add/remove programs in the applications menu, and search for "VPN". There should be 3 packages in feisty, each compatible with different types of network. Install the appropriate one, and then go to the network manager icon in your task bar and click "VPN connections->Configure VPN" and you should be able to configure with the information given by your company.

The "PPP Generic" plugin works for microsoft VPN connections

---

### Post by dwhitney67 on 2007-08-29
And when you are done with that, make sure that if you are using a router (such as the Linksys WRT54G) that you enable VPN traffic.  Some routers may come set with this feature already enabled... mine did not.

---

### Post by cmnorton on 2007-08-29
If your company supports pptp, then this link should give you the instructions you need to set up pptpconfig 

[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

It will cover how to download -- modifying your repositories to include [http://quozi.netrek.org/pptp/pptpconfig./](http://quozi.netrek.org/pptp/pptpconfig./) -- setting up, and troubleshooting, including trying to connect and stuff that can happen with a large file transfer.

I configured this on Ubuntu 6.06 LTS, so I do not have experience with Feisty.

There are still some issues I have. Sometimes I cannot connect after using a browser over my regular network, but a reboot makes everything okay. (Perhaps something less than a reboot would work; I am still working on that.)

---

