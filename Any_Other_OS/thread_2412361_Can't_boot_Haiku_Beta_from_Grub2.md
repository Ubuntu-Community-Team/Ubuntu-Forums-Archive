---
title: "Can't boot Haiku Beta from Grub2"
date: 2019-02-11
forum: Any Other OS
---

### Post by bikeguychicago on 2019-02-11
[COLOR=#1D2129][FONT=system-ui]I have a Thinkpad R60 with both Ubuntu 18.10 and Haiku Beta 1 installed on it. [/FONT][/COLOR]
[COLOR=#1D2129][FONT=system-ui]I added Haiku to the Grub 2 menu via the instructions found here: [Adding Haiku to GRUB2 in Ubuntu 9.10]("http://old.besly.de/menu/search/archiv/sys/haiku_grub2_eng.html")[/FONT][/COLOR]
[COLOR=#1D2129][FONT=system-ui]Haiku appears in the menu but when I try to select it from the boot menu, the following messages appear: [/FONT][/COLOR]
[COLOR=#1D2129][FONT=system-ui][FONT=inherit]error: can't find command 'title'
error: can't find command 'rootnoverify'
error: invalid signature

The Haiku partition is on hd0,2

[/FONT]
[FONT=inherit]Does anyone know the source of these errors above and how to resolve the problem?[/FONT]
[FONT=inherit]Thanks![/FONT]
[/FONT][/COLOR]

---

### Post by oldfred on 2019-02-11
Do not know Haiku.
Moved to other OS.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2019-02-12
> [COLOR=#1D2129][FONT=system-ui][FONT=inherit]error: can't find command 'title'[/FONT][/FONT][/COLOR]

That would mean that you used an incorrect entry for Grub as "title" is only used in Grub Legacy not Grub2.   I don't know why you used 'title'  because the site you posted with the instructions does not use it in their examples nor does it use 'rootnoverify'?  The menuentry posted below worked fine for me several years ago when I put Haiku Alpha on a usb and booted it from Grub Legacy on the hard drive.  

> title Haiku
rootnoverify (hd1,0)
chainloader +1 
 

I'm not sure why you got the error on the chainloader command as that is also used in Grub2.   Take a look at the Haiku site below which gives examples of correct Grub2 entries for both a Legacy and EFI boot menu and note they both use the chainloader command.  Best instructions for using Haiku are at their site which has been available for years.  Good luck.

[https://www.haiku-os.org/guides/booting/](https://www.haiku-os.org/guides/booting/)

---

