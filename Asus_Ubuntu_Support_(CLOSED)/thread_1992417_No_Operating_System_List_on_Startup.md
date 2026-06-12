---
title: "No Operating System List on Startup?"
date: 2012-05-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by namone on 2012-05-31
Hey, so I am new to everything. Here is my problem:

I downloaded the Windows Ubuntu Installer (Wubi). I have an ASUS (2.0 GHz Dual Core, 3.0 GB RAM, Intel(HD) Grapchis card, Windows 7.) Well, after running through the installer in Windows 7, it told me to reboot. At the time, I was busy, so I clicked "Manual Reboot Later." Of course, once I was done, I rebooted my ASUS laptop. However, here is the problem. There was NO operating system selection screen, it just went straight to Ubuntu. I'm not gonna lie, I like Ubuntu so far, but I have important stuff on my Windows operating system; and it just keeps booting to Ubuntu automatically.

Thanks,
Namone

---

### Post by drs305 on 2012-05-31
namone,

Welcome to the Ubuntu forums.  :-)

I am not a Wubi user but try these two things and let us know what happens:

1. Open a terminal in Ubuntu (gnome-terminal) and run:
```
sudo update-grub
```
It will ask for your password. Type it in but you won't see it. Press ENTER after you have entered it.

2. Reboot and see if the menu appears. If not, reboot again and hold down the SHIFT key and see if the menu shows up. Does Windows now appear?

Let us know what happens after doing the above.

---

### Post by namone on 2012-05-31
> **drs305 said:**
> namone,

Welcome to the Ubuntu forums.  :-)

I am not a Wubi user but try these two things and let us know what happens:

1. Open a terminal in Ubuntu (gnome-terminal) and run:
```
sudo update-grub
```It will ask for your password. Type it in but you won't see it. Press ENTER after you have entered it.

2. Reboot and see if the menu appears. If not, reboot again and hold down the SHIFT key and see if the menu shows up. Does Windows now appear?

You should really be seeing the Windows bootloader rather than the Ubuntu bootloader if your Wubi installation went as planned, but let us know what happens after doing the above.

Okay, I'll try that and get back to you.

---

### Post by namone on 2012-05-31
> **drs305 said:**
> namone,

Welcome to the Ubuntu forums.  :-)

I am not a Wubi user but try these two things and let us know what happens:

1. Open a terminal in Ubuntu (gnome-terminal) and run:
```
sudo update-grub
```It will ask for your password. Type it in but you won't see it. Press ENTER after you have entered it.

2. Reboot and see if the menu appears. If not, reboot again and hold down the SHIFT key and see if the menu shows up. Does Windows now appear?

You should really be seeing the Windows bootloader rather than the Ubuntu bootloader if your Wubi installation went as planned, but let us know what happens after doing the above.

Thanks! It worked like a charm! I was worried for a bit there, haha.

---

### Post by bcbc on 2012-05-31
> **namone said:**
> Hey, so I am new to everything. Here is my problem:

I downloaded the Windows Ubuntu Installer (Wubi). I have an ASUS (2.0 GHz Dual Core, 3.0 GB RAM, Intel(HD) Grapchis card, Windows 7.) Well, after running through the installer in Windows 7, it told me to reboot. At the time, I was busy, so I clicked "Manual Reboot Later." Of course, once I was done, I rebooted my ASUS laptop. However, here is the problem. There was NO operating system selection screen, it just went straight to Ubuntu. I'm not gonna lie, I like Ubuntu so far, but I have important stuff on my Windows operating system; and it just keeps booting to Ubuntu automatically.

Thanks,
Namone

Please confirm... you rebooted into Ubuntu (no prompt). Then you rebooted again and it still went straight into Ubuntu?
How many times did you reboot?

This was fixed after running 'sudo update-grub'?

With a Wubi install, it does boot immediately into Ubuntu the first time you reboot. But only the first time. Thereafter it should prompt you with a choice.

It's important to confirm the details so a bug report can be filed as this is a serious issue you are reporting. The problem is, that the boot menu screen you are referring to (Windows Boot Manager) has nothing to do with grub, and so running 'sudo update-grub' *should* have no impact on that.

Please can you also post the result of the following command:
```
df -h
```

---

