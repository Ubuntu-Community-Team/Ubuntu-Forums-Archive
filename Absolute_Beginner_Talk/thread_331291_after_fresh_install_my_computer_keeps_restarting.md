---
title: "after fresh install my computer keeps restarting"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Lord_Garfield on 2007-01-04
Hi all,

I'm verry new to linux and it seems that it is is not made for me.

First I downloaded gentoo. Tried it but it failed. Seems that it was not compatible with my PIII and needed another version of it. Wich worked but for me as a beginner was a bit to hard.

So I bought myself an via epia computer. Wich I will use for testing. I downloaded ubuntu 6.06 server version. Becouse I'm a php developer and want to install the LAMP server.

So I boot my epia with it and I check the cd if it is ok. And yes it is. Then I click on install LAMP server. I go through the whole install process and at a certian moment the install is finished. I pops out my cd and asks to remove it and to reboot. I do this and what happens. My system keeps rebooting. The last thing I see before it restarts booting is the folowing:

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro quiet splash
[linux-bzImage, setup=0x1c00, size=0x16c98f]
initrd /boot/initrd.img-2.6.15-26-server
[linux-initrd @ 0xd93e000, 0x6a1333 bytes]
savedefault
boot

after this I started all over again and well.. I thought lets try the install to hard disk instead of the lamp.

But it has the same problem. Install work until it asks for removing the cd and to reboot.

Same error here.

What could cause this problem..

Funny is that a friend of me gave me a cd with ubuntu 5.10 and this one worked. (I could start installing apache etc.. on it.) But I want to start with 6.06 now instead of updating the 5.10 for the simple reason that I would not like to install 5.10 and then upgrade all the way to ubuntu 8.5 (if this one ever comes :D ) I want to find the cause?
What can I try?

tanks in advance

---

### Post by raul_ on 2007-01-04
I don't know but i tell you there is no problem (nor difference) in installing a fresh Dapped or upgrading from Breezy. You can try and do that to see if the error is still ther

---

### Post by Lord_Garfield on 2007-01-05
But in a few years. And I want to install a new Ubuntu system. It would be rather strange to still install from the 5.10 CD instead of a new or more recent one. Or do you mean that even in 5 years you simply install a 5 year old linux system and update all the way is the same as simply install the new one?

kind regards.

---

### Post by mykalreborn on 2007-01-05
> Or do you mean that even in 5 years you simply install a 5 year old linux system and update all the way is the same as simply install the new one?


he means upgrading from breezy to dapper is easy. but not all distros are like that. for example upgrading from dapper to edgy can be pretty faulty

---

### Post by Lord_Garfield on 2007-01-10
Ok

I installed 5.10
Then I changed breezy to dapper in the /etc/apt/sources.list

Then I did apt-get update
apt-get dist-upgrade

And I whas succesfuly updated to 6.06.1

Then I changed daper to edgy in the sources.list
and did the same.

And Now I'm succesfuly updated to 6.10

But new CD's of ubuntu to install 6.06 or 6.10 will fail. I have to strat with 5.10.

I can not imagine to do all those updates (in a fresh installation) if the current ubuntu is for example 8.10.
Then I need to install 5.10 update to 6.06.1 then to 6.10 then to 7.07 etc...

so..
How can I make the cd work? (The cd check says the cd is fine)

Tanks in advance.

---

