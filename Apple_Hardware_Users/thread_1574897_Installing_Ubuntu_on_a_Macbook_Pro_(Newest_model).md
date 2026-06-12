---
title: "Installing Ubuntu on a Macbook Pro (Newest model)"
date: 2010-09-14
forum: Apple Hardware Users
---

### Post by StevenR3792 on 2010-09-14
I've been having an awesome experience with Linux on my Android phone- I figured I'd try Ubuntu, and I've gotten as far as having a partition and booting a CD without installing it. I like the system, so I figure I will install it... maybe completely switch over sooner or later. :)

Now, when I tried to make a partitions table or something in Ubuntu it told me I'd have to wipe my disks... is this telling me I need to essentially do a factory reset? I don't exactly want to delete everything... 

Also, has anyone gotten it working so sound, backlit keyboard, wireless internet, the multitouch pad (three finger back/forwards?), camera/mic, etc are working? Sorry if these are noobish questions... I do intend to swap over entirely, so just checking. 

Thanks for the help and your time! :)

---

### Post by linuxopjemac on 2010-09-15
[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

---

### Post by dngfng on 2010-09-16
I have complied a helpful guide that should walk you through every step of installing Ubuntu on your MacBook. Just have a look in my Signature for the dual/triple booting guide.

---

### Post by arviso on 2010-09-23
[QUOTE=StevenR3792;9847204]I've been having an awesome experience with Linux on my Android phone- I figured I'd try Ubuntu, and I've gotten as far as having a partition and booting a CD without installing it. I like the system, so I figure I will install it... maybe completely switch over sooner or later. :)

Now, when I tried to make a partitions table or something in Ubuntu it told me I'd have to wipe my disks... is this telling me I need to essentially do a factory reset? I don't exactly want to delete everything... 

Also, has anyone gotten it working so sound, backlit keyboard, wireless internet, the multitouch pad (three finger back/forwards?), camera/mic, etc are working? Sorry if these are noobish questions... I do intend to swap over entirely, so just checking. [ENDQUOTE]



I managed to install Ubuntu 10.4 and then 10.4.1 onto a MacBook Pro5.3, but neither installed partition worked. The latest, 10.4.1, always indicated a "kernel panic" on boot-up. I could still boot up from the live CD. With 10.4.0 I could not boot up from the partition or the live CD.


Having had my hard disk repaired for a probably unrelated problem, I now want to install 10.4.1, but I hang up on the "Install" page. I want a 75GB partition in the 240GB of free space available, but I can't formulate the number of bytes necessary for this. I keep getting my format refused for being too small a number. I googled for "75GB + ?mb" and learned that 1 GB is 1 trillion bytes (or so my friend Google seems to tell me). Is the number I want to install 60 000 000 000? I am afraid of making an unalterable 7.5 GB partition.

---

### Post by trevolio on 2010-10-10
you can easily re do partitions with the same tool if you get your numbers wrong

---

### Post by trevolio on 2010-10-10
you can easily re do partitions with the same tool if you get your numbers wrong

---

### Post by tpievila on 2010-10-11
> **arviso said:**
> Having had my hard disk repaired for a probably unrelated problem, I now want to install 10.4.1, but I hang up on the "Install" page. I want a 75GB partition in the 240GB of free space available, but I can't formulate the number of bytes necessary for this. I keep getting my format refused for being too small a number. I googled for "75GB + ?mb" and learned that 1 GB is 1 trillion bytes (or so my friend Google seems to tell me). Is the number I want to install 60 000 000 000? I am afraid of making an unalterable 7.5 GB partition.

Hard drive manufacturers use GB to mean 10^9 bytes. Almost everyone else, including most of the partition tools, use the meaning 2^30 bytes. This is the reason why your hard drive can seem smaller than what it says on the sticker (though manufacturers also vary the exact number of bytes, so two hds of different brand can be different size even when they claim the same amount of bytes).

But then again, in most tools you should be able to just input the amount you want in GB. What are you using to partition your disk, the tool on installation cd? I haven't used the installer partition tool in a while (gparted IIRC), I usually prepartition my hd from command line, so hopefully someone else will comment on specifics.

---

