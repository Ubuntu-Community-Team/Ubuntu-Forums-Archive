---
title: "[Triple Boot] Annoying Grub Screen"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by xelapond on 2007-11-09
So, awhile ago I successfully triple booted my Macbook Pro.  Worked Flawlessly.  I was using rEFIt, so when I selected Linux it would load Linux, windows would load windows, and Mac OS would load Mac OS.  When Gutsy came out, i figured it was best to reinstall because i had messed up my graphics driver.  When I reinstalled, something annoying happened.  Now, when I select Linux or Windows, it takes my to the grub bootloader.  It did not do this before.  So every time I want windows or Linux I have to select it twice.

As I know nothing about grub, naturally i don't know how to fix it.

Do any of you know how to make it so it does not show the grub screen, and instead lust loads the operating system?

Thanks, 

Alex

---

### Post by cyberdork33 on 2007-11-09
> **xelapond said:**
> So, awhile ago I successfully triple booted my Macbook Pro.  Worked Flawlessly.  I was using rEFIt, so when I selected Linux it would load Linux, windows would load windows, and Mac OS would load Mac OS.  When Gutsy came out, i figured it was best to reinstall because i had messed up my graphics driver.  When I reinstalled, something annoying happened.  Now, when I select Linux or Windows, it takes my to the grub bootloader.  It did not do this before.  So every time I want windows or Linux I have to select it twice.

As I know nothing about grub, naturally i don't know how to fix it.

Do any of you know how to make it so it does not show the grub screen, and instead lust loads the operating system?

Thanks, 

Alex
you need to install grub to the Ubuntu partition and restore the windows bootloader to the MBR.

[http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/](http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/)

---

