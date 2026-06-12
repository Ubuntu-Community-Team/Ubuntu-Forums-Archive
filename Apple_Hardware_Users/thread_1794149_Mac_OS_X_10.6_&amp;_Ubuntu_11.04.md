---
title: "Mac OS X 10.6 &amp; Ubuntu 11.04"
date: 2011-06-30
forum: Apple Hardware Users
---

### Post by moocan on 2011-06-30
Dear Community,

I have a MacBook5,1 (Alluminium 13" Unibody) and would like to install Ubuntu 11.04 on my Mac.

Is there any way to install "Dual-Boot Mac OSX and Ubuntu" without rEFIt using any other alternative ?

I had so many troubles with rEFIt 0.13 and 0.14 (and sync process) which show me things which does not exist and does not show things which exist. 
I have killed my mac two times with rEFIt and reinstalled each time all.

Is there any other alternative (event if choosing the os is made with opt. key)  ? Is it possible to install with only BootCamp ? ... or other EFI mult-boot ?

I read this guide [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") but it need rEFIt.

Many thanks in advance

Kind Regards
Moo

---

### Post by srs5694 on 2011-06-30
You may want to read my [Web page on booting Ubuntu in EFI mode.](http://www.rodsbooks.com/ubuntu-efi/index.html) Although it describes setting it up with rEFIt, the way it's set up is different enough that it may work better for you. Furthermore, if you prefer, you can configure GRUB to be the computer's primary boot selector. This will require some deviations, and possibly a custom GRUB entry to get it to launch Apple's .efi boot file, but it should work, at least in principle.

---

### Post by pauljwells on 2011-06-30
Virtualbox?

---

### Post by mire on 2011-07-02
Technically refit is not required if you only have two Linux and Mac OS X installed. The OS selection screen you get by holding down option always says windows if it sees another system this option in fact boots whatever legacy system is there. The reason for refit is so Windows can be installed as well and all three systems will show up on one screen.

---

### Post by moocan on 2011-07-09
Hi,

Many thanks for all your replies.

I have already my ubuntu under virtualbox but I would like to free my ubuntu with full memory and processor performance.

rEFIt works well alone but I sync partition table using rEFIt it's the beginning of the end.
It seems that sync process is required and I don't know to do this as it without loosing all.

@srs5694, many thanks for your great guide. I will test this but with another hard disk to not reinstall another time all my MacBook. As mentioned in your great guide .... "As near as I can tell, this is nothing more than the gptsync utility, which is used to create a hybrid MBR. Don't use it!" ... a great advice !


Kind Regards

---

### Post by waynerod on 2011-07-11
> **moocan said:**
> Dear Community,

I have a MacBook5,1 (Alluminium 13" Unibody) and would like to install Ubuntu 11.04 on my Mac.

Is there any way to install "Dual-Boot Mac OSX and Ubuntu" without rEFIt using any other alternative ?

I had so many troubles with rEFIt 0.13 and 0.14 (and sync process) which show me things which does not exist and does not show things which exist. 
I have killed my mac two times with rEFIt and reinstalled each time all.

Is there any other alternative (event if choosing the os is made with opt. key)  ? Is it possible to install with only BootCamp ? ... or other EFI mult-boot ?

I read this guide [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") but it need rEFIt.

Many thanks in advance

Kind Regards
Moo

Doesn't it work via BootCamp? :(
I was considering buying a Macbook pro and setting it up via bootcamp. Any feedback on that?

---

