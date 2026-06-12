---
title: "Installing Ubuntu 7.04: ATI X**** Cards"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Technoviking on 2007-04-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853") that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

[LIST=1]
[*]Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
[*]Start text mode installer and install Ubuntu/Kubuntu.
[*]Finish Install and reboot.
[*]Update package list and upgrade any packages needed.
```
sudo apt-get update
sudo apt-get dist-upgrade
```
[*]Install fglrx closed source driver for ATI video cards.
```
sudo apt-get install xorg-driver-fglrx
```
[*]Update loaded modules.
```
sudo depmod -a
```
[*]Configure /etc/X11/xorg.conf
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
[*]Reboot
[/LIST]

Ubuntu 7.04 should now boot into GDM/KDM.

---

