---
title: "PowerBook G4  &amp; IBook G4 Yaboot.conf issue when installing"
date: 2019-04-09
forum: Apple Hardware Users
---

### Post by minicm94123 on 2019-04-09
Hi.

Well its hard to explain but i have a problem when install any ppc distro for this 2 "macs".

Let me explain.

I havent a blank disk so i used a USB drive for that; the case is... i've download a "ubuntuPPC.iso" by example, and i used the Disk Utility for put it in the usb, well that was easy,  i go to openfirmware Opt+Apple+F+O  and make a devalias for usb bla bla bla etc. When  using the command boot ud:/install/yaboot it goes to a black screen, then it shows me a error like this 

/pci@f2000000/usb@1b/disk@1 yaboot.conf unknow or corrupt filesystem.

I tried with other distro, it gives me the same screen, recently i've installed succesfully a "Ubuntu 12.04 installation" on my Ibook G4, but when i try to make a new installation it gives me the same yaboot error, i tried with replacing the usb yaboot file with another yaboot files on other distros, it gives me the same error ¡Again!

¿What should I do in this scenario?

My PowerBook G4 has a recently 10.5 leopard installation and anyway it gives me that yaboot error. My Ibook G4 haved 10.4 Tiger installed, deleted by Ubuntu when install.

I really apreciate you help guys.

-Minicm

---

### Post by gsahli on 2019-04-13
I don't think you've used the correct method to make a bootable USB. Can you use the command (In terminal) diskutil list and tell us all info about disk partitions?

---

