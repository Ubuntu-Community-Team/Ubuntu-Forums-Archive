---
title: "rEFIt Problem with External! - HELP!"
date: 2009-01-25
forum: Apple Hardware Users
---

### Post by Shady899 on 2009-01-25
I am trying to run rEFIt on my MacBook 5,1 to duel boot using my external with Ubuntu but it does not work!
It keeps giving me an error when I start up my macbook and click on the other Drive.

Help me!!!
I dont know what to do!
Send me a step by step instructions either someone else made or you made please!
I need exactly what will happen and how to install it!
I dont understand this: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

It says something like "Error opening grub.(something)"

Thanks, Luc (shady899)

---

### Post by cyberdork33 on 2009-01-25
> **Shady899 said:**
> I am trying to run rEFIt on my MacBook 5,1 to duel boot using my external with Ubuntu but it does not work!
It keeps giving me an error when I start up my macbook and click on the other Drive.

Help me!!!
I dont know what to do!
Send me a step by step instructions either someone else made or you made please!
I need exactly what will happen and how to install it!
I dont understand this: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

It says something like "Error opening grub.(something)"

Thanks, Luc (shady899)
Because you cannot just install to an external drive and have it work. You can either 
a) Use a Boot CD
b) try to bot via EFI

Please see the FAQ stickied in the forum for more information.

You have already been asked to go to the EFI thread to ask your question about the process. 

[http://ubuntuforums.org/showpost.php?p=6597404&postcount=4](http://ubuntuforums.org/showpost.php?p=6597404&postcount=4)
[http://ubuntuforums.org/showpost.php?p=6601763&postcount=4](http://ubuntuforums.org/showpost.php?p=6601763&postcount=4)

Please keep to one thread. There is no need to open numerous threads on the same problem. It makes it very difficult to help you when you information is scattered through the forum.

---

### Post by Shady899 on 2009-01-26
Yes Well you told me to re-post it somewhere else.

But I do boot from a CD...what do you mean?

I am confused on what to do here.

---

### Post by cyberdork33 on 2009-01-26
> **Shady899 said:**
> Yes Well you told me to re-post it somewhere else.

But I do boot from a CD...what do you mean?

I am confused on what to do here.

The basic bottom line is that you CANNOT install and boot using an external drive. There is a bug in the Apple firmware that does not allow you to boot what Apple calls a "legacy OS" from an external hard drive. It just doesn't work.

You can boot Ubuntu in a non "legacy OS" manner with grub-efi. This method is not yet very well supported, but there is information in the Link which I keep giving you. If you would like to attempt this, and do not understand the proceedure then please post a REPLY in that thread with details about what you have done, and what you do not understand. Again, here is the link to that thread:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

The other option is to download a special BootCD that is made to boot Ubuntu from an external drive on computers with firmware that do not support booting directly from USB (or firewire). Here is the link for the CD:
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

All of this information is found in the FAQ at the top of the forum. Please check there for information in the future.

---

