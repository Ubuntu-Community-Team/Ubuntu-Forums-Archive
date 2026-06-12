---
title: "Wur iz muh Gooie?!"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Skrypt on 2007-07-08
I apologize. That was uncalled for.

Anyhow, I've just installed Ubuntu 7.04 via the LiveDVD for AMD64. Booted via Super Grub disk but booted into the terminal. How do I load up a GUI? 

Thanks!

Edit: 
I've tried "startx" and recieved "-bash: startx: command not found"
I also tried "sudo apt-get ubuntu-desktop" and recieved "-bash: sudo: command not found"
I reckon I'll need to reinstall....

---

### Post by JasonL on 2007-07-08
If you have installed via the live CD you should be able to just boot you PC without the super grub disc and ubuntu should load into a gui by default.

---

### Post by Skrypt on 2007-07-08
> **JasonL said:**
> If you have installed via the live CD you should be able to just boot you PC without the super grub disc and ubuntu should load into a gui by default.

Guess I should have explained that I've had an issue with the dual booting. I've got Ubuntu installed on a Secondary hard drive with Vista (:confused:) installed on my Primary. To access the Ubuntu OS I've been having to use Super Grub. I think I could reconfig my grub.conf but I'm too stupid for that atm.

---

### Post by JasonL on 2007-07-08
In that case read this guide which explains how to recover grub while maintaining your windows loader. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-09167948173503db5923da717a106f0c3aac1cd2")

---

