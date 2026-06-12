---
title: "Sssd.service Ubuntu 20.04 Desktop Problem"
date: 2021-02-12
forum: Apple Hardware Users
---

### Post by erselbey on 2021-02-12
&#350;ub 12 17:16:35 User systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
    &#350;ub 12 17:16:37 User systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
    -- Subject: A start job for unit sssd-sudo.socket has failed
    -- A start job for unit sssd-sudo.socket has finished with a failure.


    systemctl restart sssd* --all
    Failed to restart sssd-pac.service: Operation refused, unit sssd-pac.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-pac.service' for details.
    Failed to restart sssd-sudo.service: Operation refused, unit sssd-sudo.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-sudo.service' for details.
    Failed to restart sssd-nss.service: Operation refused, unit sssd-nss.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-nss.service' for details.
    Failed to restart sssd-ssh.service: Operation refused, unit sssd-ssh.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-ssh.service' for details.
    Failed to restart sssd-autofs.service: Operation refused, unit sssd-autofs.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-autofs.service' for details.
    Failed to restart sssd-pam.service: Operation refused, unit sssd-pam.service may be requested by dependency only (it is configured to refuse manual start/stop).
    See system logs and 'systemctl status sssd-pam.service' for details.
    A dependency job for sssd-nss.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-ssh.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-pam.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-pac.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-pam-priv.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-sudo.socket failed. See 'journalctl -xe' for details.
    A dependency job for sssd-autofs.socket failed. See 'journalctl -xe' for details.


I tried the installs on Ubuntu 18 and 16 Desktop and Server versions and it worked. I think the only problem is with ubuntu 20.04 Desktop. Device MacBook Pro 2015 13 inches.

---

### Post by howefield on 2021-02-12
SUpport thread, moved to the "*Apple Hardware Users*" forum.

---

### Post by erselbey on 2021-02-13
???

---

### Post by 2blue on 2021-02-13
All apple users installing Ubuntu derivatives are delegated to this section. I installed Lubuntu 20.10 and didn`t get the problem you have, My macbook is probably a year old than yours, with a new SSD. Lubuntu has the same installer and boot ware as Ubuntu. There should not be that much trouble installing on the macbooks, Take a look at installer issues on various brands of hardware, and there are similar issues. I don`t know about any reason why a 2015 macbook stands out, with the same UEFI/Bios as others.  I`m not and expert in any way, I just work with the hard ware until it runs, with the notion that macbooks these days aren`t "not-PCs".

---

### Post by howefield on 2021-02-13
> **erselbey said:**
> ???

I assume, in the absence of actual words, that this refers to the moving of your thread.

You posted in the Resolution Centre, a non (technical) support area of the forum with the strapline..
> 
This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse. 

Your thread has been moved the "*Apple Hardware Users*" forum, a technical support area of the forum with the strapline..
> 
Support for users who are using Apple Intel or PPC based systems with Ubuntu

Trust that you can follow that.

---

### Post by Doug S on 2021-02-13
see [here]("https://askubuntu.com/questions/1315875/sssd-service-ubuntu-20-04-desktop-problem"), which will also point you to [here]("https://askubuntu.com/questions/1288626/ubuntu-20-10-sssd-system-security-services-daemon-failure"), which will also point you to [here]("https://ubuntuforums.org/showthread.php?t=2452209&p=13994052").

Although, I had understood the issue to only have been introduced in 20.10, but maybe it has been back ported.

---

