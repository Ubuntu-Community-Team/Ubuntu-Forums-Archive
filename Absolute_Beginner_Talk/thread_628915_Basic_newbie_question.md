---
title: "Basic newbie question"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by TarB on 2007-12-01
What I need to do is to:
"wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor"

However, I do not have wlanconfig. I than do the following..

"apt-get install madwifi-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package madwifi-tools"

I am running Kubuntu and I need to know how to perform that wlanconfig command that I mentioned in the beginning of my post. In other words, what is the proper way to get and install those tools? Thank you!

---

### Post by jamvegan on 2007-12-01
madwifi-tools is in the universe repository (at least in Feisty it is).  The easiest way to enable this repository is to open Synaptic (System->Administration->Synaptic Package Manager), then select Repositories from the Settings menu in Synaptic, and check the universe repository.  Then click Reload after closing the Settings window, and you should be able to install it either with Synaptic or with the apt-get command you were using.

---

### Post by dondad on 2007-12-01
> **jamvegan said:**
> madwifi-tools is in the universe repository (at least in Feisty it is).  The easiest way to enable this repository is to open Synaptic (System->Administration->Synaptic Package Manager), then select Repositories from the Settings menu in Synaptic, and check the universe repository.  Then click Reload after closing the Settings window, and you should be able to install it either with Synaptic or with the apt-get command you were using.

Also, when using apt-get, you will need to use sudo.

---

### Post by TarB on 2007-12-01
Thank you!

---

