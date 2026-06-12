---
title: "Is Ubuntu Server for me?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2008-01-21
Hi there! Since I noticed Ubuntu comes preinstalled with lots of useless application I don't want, I was advised to give Ubuntu Server a try.
Can I select what to install with it?
Thanks in advance!

---

### Post by tgm4883 on 2008-01-21
You probably want the alternate install cd and to install a command line system.  Then just apt-get what you need

---

### Post by Zdravko on 2008-01-21
I wonder if it is easy enough to get a DE working and able to login, hardware recognition etc.?

---

### Post by bodhi.zazen on 2008-01-21
Try the minimal CD : [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And see if this page helps as well : [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Zdravko on 2008-01-21
Does it ask me what to install? Or it downloads 700 MB silently?
One more question - I already have a linux installed on my 3rd partition. The 1st one being Vista. Currently I dual-boot. Is it possible, with this minimal CD to place GRUB in MBR so that I can again dual-boot with Vista?

---

### Post by Dr Small on 2008-01-21
> **Zdravko said:**
> I wonder if it is easy enough to get a DE working and able to login, hardware recognition etc.?
Yes, all of my hardware was recognized with the minimal installation, and then I just apted it into a server. Also, if you want a Window Manager, you'll have to install xorg first, and then you can install any window manager you want.

Dr Small

---

### Post by stchman on 2008-01-21
> **Zdravko said:**
> Hi there! Since I noticed Ubuntu comes preinstalled with lots of useless application I don't want, I was advised to give Ubuntu Server a try.
Can I select what to install with it?
Thanks in advance!

I believe that the server installation does not have a GUI, it is command line only.

A full install on Ubuntu is approx 2.5GB so it has a small footprint compared to Windows.

What apps are you saying you don't want?

You can always apt-get sutoremove the apps you don't want.

---

### Post by maybeway36 on 2008-01-21
Do command-line install, not server install. This can be done with any of the alternate CDs or the mini.iso.

---

### Post by Zdravko on 2008-01-21
You are right. I'd better stick to the normal edition. Now I have to download it :(

---

### Post by Zdravko on 2008-01-21
> **maybeway36 said:**
> Do command-line install, not server install. This can be done with any of the alternate CDs or the mini.iso.
Can you explain in details how could this be achieved?

---

### Post by tgm4883 on 2008-01-21
> **Zdravko said:**
> Can you explain in details how could this be achieved?

When you boot the alternate CD, the boot menu will have a selection called "install command-line system"

Select that

---

### Post by Zdravko on 2008-01-22
I didn't select that. Instead I chose the default installation and selected the Ubuntu Desktop (~600 MB of download, though).
Now I will boot in Ubuntu.
If only I could safely remove certain applications...

---

### Post by LaRoza on 2008-01-22
> **Zdravko said:**
> Can you explain in details how could this be achieved?

Use the Alternative CD of Ubuntu Desktop. Then, boot from it. Select "Install a Command Line System".

You can the apt-get what you want.

---

### Post by ugm6hr on 2008-01-22
> **Zdravko said:**
> If only I could safely remove certain applications...

There is no danger in removing applications, as long as you don't remove anything critical.  Just make sure you don't upgrade directly to 8.04 (Hardy) if you have removed ubuntu-desktop package though.

---

### Post by LaRoza on 2008-01-22
> **ugm6hr said:**
> There is no danger in removing applications, as long as you don't remove anything critical.  Just make sure you don't upgrade directly to 8.04 (Hardy) if you have removed ubuntu-desktop package though.

@OP When you remove a package that is part of the meta package called "ubuntu-desktop" you will be told the "ubuntu-desktop" will be removed. Don't worry, nothing other than what you specified is being removed. Without the elements of the meta package, the meta package is "uninstalled", even if it is only a few apps that you remove.

---

