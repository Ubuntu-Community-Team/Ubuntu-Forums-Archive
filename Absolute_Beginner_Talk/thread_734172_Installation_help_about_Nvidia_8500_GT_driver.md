---
title: "Installation help about Nvidia 8500 GT driver"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by ZoRRoCanCer on 2008-03-24
Please explain step by step procedure for installation Nvidia GEFORCE 8500 GT graphic card on fresh installation of Ubuntu 7.04

---

### Post by stchman on 2008-03-24
> **ZoRRoCanCer said:**
> Please explain step by step procedure for installation Nvidia GEFORCE 8500 GT graphic card on fresh installation of Ubuntu 7.04

Use Envy.  I have an 8800GT and it works excellent.  The 169.xx drivers are the ones you need to support that card.

You will need to install the Envy 0.9.10, and I have it here.

[http://www.stchman.com/tools/envy_0.9.10-0ubuntu7_all.deb](http://www.stchman.com/tools/envy_0.9.10-0ubuntu7_all.deb)

Once Envy is done installing fire it up by going to Applications--->System Tools--->Envy.

Make sure you have not installed any other nvidia driver.  If you have select the uninstall nvidia driver.  The Restricted driver manager does not have the 8xxx drivers.  If you have not installed any nvidia driver then proceed.

When Envy is up and running specify to install the Nvidia driver manually.  There will appear another menu and you need to select the 169.12 drivers.  Click apply and let it do it's thing.  Let Envy modify your xorg.conf and reboot your PC.

You will be up and running.  The only thing I had to do was modify my xorg.conf with "1920x1200" in the list of resolutions.  After that I rebooted the workspace (CTRL-ALT-Bksp) and viola.

Let me know if you have nay more questions.

---

