---
title: "MacBookPro6,1 error when using nvidia blob on boot"
date: 2013-10-31
forum: Apple Hardware Users
---

### Post by gtaylor2 on 2013-10-31
[COLOR=#333333][FONT=UbuntuRegular]I've got a MacBookPro6,1 running Ubuntu 13.10 with the proprietary blob. I'm booting in EFI mode, and basically all of the installer defaults. Booting with noveau works fine, but as soon as I install nvidia-current and restart, I briefly see the boot splash, but the screen goes black and I can't switch to a tty. I was able to SSH in and get the dmesg output, though.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://pastebin.com/3C5gWXVm](http://pastebin.com/3C5gWXVm)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It looks like something is going wrong when the nvidia module is being loaded. Something ACPI related.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any ideas? I sure would like to be able to use the binary driver.[/FONT][/COLOR]

---

