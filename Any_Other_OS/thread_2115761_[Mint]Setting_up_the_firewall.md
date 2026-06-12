---
title: "[Mint]Setting up the firewall?"
date: 2013-02-13
forum: Any Other OS
---

### Post by ChaosSeeder on 2013-02-13
Hello:

How can I set up the firewall that comes with Linux mint Nadia? Do you recommend any other firewalls? In case you do: How do I uninstall the firewall that comes with Linux Mint Nadia?

Thanks :)

---

### Post by QIII on 2013-02-13
*Moved to **Other OS/Distro Talk.***

Mint is based on Ubuntu, but is a separate distro.

---

### Post by chadk5utc on 2013-02-13
To my knowledge iptables is the only real firewall anything added to linux to run the firewall is just a "GUI" also known as a user interface. My suggestion is to learn iptables as it will be more useful later as well as universal with any Linux distro you choose.

---

### Post by BBQdave on 2013-02-13
> **ChaosSeeder said:**
> How can I set up the firewall that comes with Linux mint Nadia?

It is **GUFW**, **G**UI for **U**ncomplicated **F**ire**W**all. Though in Linux Mint, I believe it is simply labelled *Firewall*, and is under system applications in your Linux Mint Menu.

To open *Firewall* application, you will be asked for your admin password. Then simply turn it on and close the application :)

---

### Post by haqking on 2013-02-13
> **ChaosSeeder said:**
> Hello:

How can I set up the firewall that comes with Linux mint Nadia? Do you recommend any other firewalls? In case you do: How do I uninstall the firewall that comes with Linux Mint Nadia?

Thanks :)

```
sudo ufw enable
```

See here [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

There is nothing different to it in Mint.

However it is merely a interface to IPTables/Netfilter.

GUFW is a GUI to UFW.

Peace

---

### Post by xenopeek on 2013-02-14
On Linux Mint Nadia, the Firewall Configuration application (gufw) is not shown in the menu by default. That's because it comes from the Ubuntu repositories, and it is configured from there to only show on the Unity desktop. Run the following command from the terminal to show this application in your menu again:
```
sudo sed -i '/^OnlyShowIn=Unity;$/d' /usr/share/applications/gufw.desktop
```But as haqking shared, there is nothing different between Ubuntu and Linux Mint as to how you configure your firewall with gufw or ufw, so you can indeed refer to the documentation on the Wiki (or just "man ufw" to do stuff from the command line).

In gufw, enable the firewall and it should already be set to deny incoming by default. With ufw from the command line, do the same with:
```
sudo ufw enable
sudo ufw default deny
```Basically, gufw and ufw are just easier front-ends to iptables. I don't think you need to delve into that, but if you want I think have a look at [http://www.netfilter.org/](http://www.netfilter.org/).

---

### Post by mips on 2013-02-14
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

