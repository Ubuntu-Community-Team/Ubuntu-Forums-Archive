---
title: "Ubuntu can't access XP files on network"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Oomska on 2006-05-10
Hi,

I'm a total nob when it comes to linux and networking so I hope someone can give me some clear answers. I am trying to network 2 PC's, one using XP and the other Ubuntu, through a cable router. I've installed Samba, set security to 'share', and set up some shared folders on both computers.

The networked computers show up in Network places on both machines. However, I can only browse the Ubuntu shared folders the XP computer. If I try to browse the XP shared folders using Ubuntu, I get the following error message:

'The folder contents could not be displayed.'

Any idea how to solve this?

Further info:
1) Windows firewall is on (is it safe to disable this and let my router act as firewall?)
2) The shared folders on XP are on newly created FAT 32 partitions. However, my primary partition for XP itself is NTFS.

Any idea how I can allow the Linux PC to access files the XP PC?

---

### Post by raovq on 2006-05-10
although the partitions are fat32, they are sent over the network in TCI/IP, a protocol that both windows and linux (and pretty well every machine on earth) can understand. you are allright to turn off the xp firewall (i personally wouldn't use it even if i wasn't behind a router, id get zone alarm or something) and i'm guessing the source of your problem.


one question though, have you got linux shares working? because i share a folder, i can see it on my windows box, but it spits out a permissions error if it try to open it. does linux automatically set a password or something?

---

### Post by user1397 on 2006-05-10
if you got to system->administartion->shared folders, does your shared folder say something like root/home/whatever, or does it include root at all?
this is vital information so that i can help you, raovq

---

### Post by Oomska on 2006-05-11
[QUOTE=raovq]one question though, have you got linux shares working? because i share a folder, i can see it on my windows box, but it spits out a permissions error if it try to open it. does linux automatically set a password or something?[/QUOTE]


Yeah, I can open shared Linux files on my XP machine (open office documents). They open as read only though.

---

### Post by Oomska on 2006-05-11
[QUOTE=erik1397]if you got to system->administartion->shared folders, does your shared folder say something like root/home/whatever, or does it include root at all?
this is vital information so that i can help you, raovq[/QUOTE]

No, it just says home/myname. Is this vital to alow me to access files on my XP machine frm Linux?

---

### Post by raovq on 2006-05-11
so how do i properly set up shared folders on linux? in the shared folders window it's shown as /home/me/.....
is that bad?

---

