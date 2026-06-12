---
title: "login and password"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by darryl fulton on 2006-10-18
i installed xubuntu in the oem install mode,after going through the install and giving my last name as my password. At the boot stage i could not login or write my password.

---

### Post by ReaderRat on 2006-10-18
> **darryl fulton said:**
> i installed xubuntu in the oem install mode,after going through the install and giving my last name as my password. At the boot stage i could not login or write my password.
Did you wait until the login screen was displayed? Or was there no login screen at all?

---

### Post by mcduck on 2006-10-18
First, you really shouldn't use OEM install if you aren't pre-installing Ubuntu for somebody else. It doesn't provide anything you wouldn't get with normal install, it only makes the process more complex.

And then, as you already did OEM install, the default username is 'oem' so use that and the password you set during install.

After that you can install and configure whatever drivers and software you want for the default settings on the machine.

Then open a terminal and run 'sudo oem-config-prepare', this removes the oem install and prepares Ubuntu for the real user. Now reboot the machine. The next time Ubuntu is started it'll ask for all information needed to create the real user.

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview")

---

