---
title: "Install 8.04 on MAC external USB hard drive"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by _Poincare on 2008-05-31
Hi, 

I have been putzing with this for 3 weeks now. I have googled and searched forums galore, including this one, only to have no luck. The Apple Intel Users FAQ points to a thread about installing Ubuntu 8.04 on an external Mac USB hard drive but it's mostly nonsense and there is no direction or anything. Other forum posts have talked about installing on a PC USB hard drive; but in my case, I am working with a 3.1 MacBook. 

I have installed several times as both GPT- and MBR-formatted USB external drives. Most recently I have had luck with MBR-formatted and am now stuck.

My internal hard drive is full so do not tell me to put Ubuntu on that, I would if I had space and I'm not about to -- and the entire point of this is to get Ubuntu on an external USB drive! 

Most recently with the MBR-formatted drive I got the following error from rEFIt:

rEFIt - Booting legacy OS

Starting legacy loader
Using load options 'USB'

Error: Not Found returned from legacy loader
Error: Not Found from LocateDevicePath (repeats 7 times)

The firmware refused to boot from the selected volume (or something like that...)


So, my partition table is 
/dev/sdb1  80GB  HFS+
/dev/sdb5  369GB Linux (EXT3)
/dev/sdb6  11GB  Linux swap

These were from the "Guided - Use largest freespace" option in the Ubuntu install. I checked Advanced -> Install bootloader on /dev/sdb.

If I hold down OPTION on boot I see the (internal) Mac HD, Windows, and refit. If I select windows, the external USB drive whirls for a second then I get a black screen of death with "Missing operating system" and I can't do anything but poweroff. If I select refit -> Windows, it displays the windows logo and stalls without doing anything else. If I select refit -> Linux I get the above error message. 

There are absolutely no coherent resources on this. I simply want to know how to get Ubuntu booting on a MAC (not PC) external USB hard drive. I don't see why it's so hard especially if a PC can do it!

---

### Post by cyberdork33 on 2008-05-31
> **_Poincare said:**
> I have been putzing with this for 3 weeks now. I have googled and searched forums galore, including this one, only to have no luck. The Apple Intel Users FAQ points to a thread about installing Ubuntu 8.04 on an external Mac USB hard drive but it's mostly nonsense and there is no direction or anything. Other forum posts have talked about installing on a PC USB hard drive; but in my case, I am working with a 3.1 MacBook.It is not nonsense, it is a conglomeration of all the info we know of the subject. If you read it, you will see that many people have tried various things and failed.

> **_Poincare said:**
> There are absolutely no coherent resources on this. I simply want to know how to get Ubuntu booting on a MAC (not PC) external USB hard drive. I don't see why it's so hard especially if a PC can do it!It is hard because a Mac is not ta typical PC. It has EFI instead of a BIOS and there is an issue booting what Apple calls "legacy" operating systems from an external drive... period. 

There are two possible methods to do what you want. One is to create a boot partition on your internal. The second is to create a boot cd. Both of there are documented in the thread you referred to. If you want to experiemnt and try something new, go for it, and add your findings to the thread.

---

