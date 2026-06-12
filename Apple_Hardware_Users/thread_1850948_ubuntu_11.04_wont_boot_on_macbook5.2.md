---
title: "ubuntu 11.04 wont boot on macbook5.2"
date: 2011-09-27
forum: Apple Hardware Users
---

### Post by epsiphone on 2011-09-27
hi guys
i installed ubuntu 11.04 with this instruction
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
(thanks guys for that):P )
on my macbook 5.2 dual boot with snow lepard 10.6
after installation finished i rebooted and go to partion tools in erefit but it says everything is synced but when want to boot in ubuntu once freeze in tux logo then reboot and then boot on ubuntu and the gurb screen apeard but when want to boot in general(or even in rescue mode) nothing happen sometimes a prurple screen with nothing and sometimes a black screen splashing and reboot automaticaly( i tested many times just this happend)
i dont know why realy
even erase mac and create new partition tabl and install ubuntu and same happend
i searched whole web but i dont understand
please help me i am very confused
is it the compatibilty issue with 1104 and macbook??
if i install 10.4 or 10.10 will have this problem probably or not??
share please

---

### Post by epsiphone on 2011-09-28
please help
no one??

is that vga driver problem??
i have  nvidia graphic

---

### Post by epsiphone on 2011-09-28
i even try reinstalling grub with livecd by this command

grub-install /dev/sda3

but it shows below error
could not find /boot drive(something like this)

then i download and install grub deb file
then in terminal execute this command
sudo grub
grub > root (hd,02)
grub > setup (hd,02)

and terminal could not find the /boot/grub/stage1 and shows 2 error

please help

---

