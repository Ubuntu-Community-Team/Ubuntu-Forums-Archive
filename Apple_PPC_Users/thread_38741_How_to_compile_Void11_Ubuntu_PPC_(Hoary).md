---
title: "How to compile Void11 Ubuntu PPC (Hoary)"
date: 2005-06-01
forum: Apple PPC Users
---

### Post by usr3301 on 2005-06-01
I am trying to compile a wireless tool called "void11" on my PowerBook running Ubuntu Linux Hoary (2.6.10-5).  I am still relatively new to Linux.  Has anyone done this before?  If so, can you please post how I go about this?  Thanks!

Void11:  [http://www.wlsec.net/void11/](http://www.wlsec.net/void11/)

Requires:  HostAP and Host APD (which I have installed)

Their directions:
> compile and install Linux HostAP driver from hostap.epitest.fi
> compile void11
  > # make HOSTAPD_PATH=[PATH_TO_HOSTAPD] <FLAGS> (find flags in :: subdirs ::)
  (note: newer versions of HostAP are splitted into several packets,
         use the userspace daemon in hostapd-0.1.0.tar.gz or newer!)
  > exp. # make USEGTK=1 USECONSOLE=1 all install
(monitor void11 on device wlan0ap)

---

