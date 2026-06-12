---
title: "Freeze ups"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Billybob115 on 2008-02-11
I have installed Ububtu 7.10 on my laptop and it freezes about every 5 to 10 minutes.  I then downloaded Kubuntu 7.10 and tried it and it goes the same.  This machine is dual booted with vista and it runs fine.  I also ran 7.04 on theis notebook with out trouble .. Any ideas

---

### Post by marshall.robert on 2008-02-11
i hate to suggest this, but have a google around with your laptop make and model and see if there are any similar problems documented in other places.

---

### Post by PmDematagoda on 2008-02-11
Could you please post the specifications of your PC. Without some information about your PC it would be hard to pin-point the exact cause of the problems.

---

### Post by Billybob115 on 2008-02-11
Did the google search but found nothing.  Also did a hardware check and tested ok.

---

### Post by Billybob115 on 2008-02-11
It is a MSI M662 notebook.  It has an Intel 945 Express chip set. Intel Core Duo T2400 dual core processor, 2GB RAM, 120 GB HDD.  Intel Pro Wireless  3945 ABG and a Realtek Giabit LAN.

---

### Post by heldal on 2008-02-12
> **Billybob115 said:**
> It is a MSI M662 notebook.  It has an Intel 945 Express chip set. Intel Core Duo T2400 dual core processor, 2GB RAM, 120 GB HDD.  Intel Pro Wireless  3945 ABG and a Realtek Giabit LAN.

I've seen the same problems on many other notebooks with similar specs. I.e worked without a hitch with 7.04 and freezes up frequently on 7.10. The problem seems to be with the 3945 wireless .. actually most intel wireless chips have the same problem.

Try to disable wifi and use GigE instead to confirm that wireless is the problem.

Ubuntu 7.10 by default uses the discontinued ipw3945 closed-source driver. Intel has since released specs for open-source drivers for several chipsets ([http://intellinuxwireless.org/](http://intellinuxwireless.org/)). These also get installed by default, but are not used. The iwlwifi driver is still under heavy development and ubuntu has problems keeping up. The one supplied with 7.10 unfortunately also has its glitches. To swap to the new-type driver simply blacklist the old driver so that it isn't loaded. Add a line containing "blacklist ipw3945" in /etc/modprobe.d/blacklist and reboot. The system should then pick the iwl3945 driver instead. 

The version of the new iwlwifi-driver in 7.10 also tends to freeze occasionally. I've seen that it also helps a bit to enable hardware-encryption (sw crypt by default). To do this add a line containing "options iwl3945 hwcrypto=1" in /etc/modprobe.d/options.

Finally lets hope the dev-team soon finds the time to release a new collection of kernel-modules for 7.10 that include a more recent version of the iwlwifi drivers. So many people have these kinds of problems that it generates bad publicity for ubuntu. It doesn't make sense to make people wait for 8.04.

---

