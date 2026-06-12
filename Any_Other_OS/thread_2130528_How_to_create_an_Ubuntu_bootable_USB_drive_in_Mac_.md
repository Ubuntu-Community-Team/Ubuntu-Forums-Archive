---
title: "How to create an Ubuntu bootable USB drive in Mac OS X?"
date: 2013-03-29
forum: Any Other OS
---

### Post by BenginM on 2013-03-29
[COLOR=#333333][FONT=Ubuntu Beta]Salutations![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]So, i got a Macbook pro8,1 and i would very much like to have a dual boot system on it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I prefer the USB Media installation method, and as it's the only option i have at the moments.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]So, i've Follow the Instructions in :[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)[/FONT][/COLOR]

[LIST]
[*]Terminal commands used :
[/LIST]
**hdiutil convert -format UDRW -o ~/Desktop/ubuntu-12.10-desktop-amd64+mac.img ~/Desktop/ubuntu-12.10-desktop-amd64+mac.iso**

**sudo dd if=/Users/sary/Desktop/ubuntu-12.10-desktop-amd64+mac.img of=/dev/rdisk2 bs=1m**

**This is my setup :**


[LIST]
[*]installed Refind
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta][http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)[/FONT][/COLOR]

[LIST]
[*]Formatted the usb in " Disk Utility " :
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]Selected '1 Partition' and 'MacOS Extended (Journaled)' .[/FONT][/COLOR]

[LIST]
[*]Partitioned the usb as :
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]GUID Partition Table (GPT)[/FONT][/COLOR]

[LIST]
[*]The ISO img used :
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]the Ubuntu 12.10 amd64+mac version " ubuntu-12.10-desktop-amd64+mac.img " .[/FONT][/COLOR]
**after a shutdown, Refind shows up and it's working properly, But when i select the USB Media drive it leads to a black screen that reads " Non-system disk " .**

**I would like to know What exactly am i doing wrong, or missing here ?**


[LIST]
[*]Should the usb format be in " Mac OS Extended (Jounrnaled) " , " MS-DOS (FAT) or " ExFat " ?
[*]Should it have 1,2 Partition Layout ?
[*]IF it must be formated as Mac OS Extended (Jounrnaled) , does it mean the partition scheme should be set to " GPT " or " MBR " to have an ubuntu bootable usb drive ?
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]Thanks.[/FONT][/COLOR]

---

