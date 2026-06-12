---
title: "Booting Windows 7, Mac OS and Ubuntu"
date: 2012-06-18
forum: Apple Hardware Users
---

### Post by temiyemi on 2012-06-18
I had Win 7 installed on my MacBook Pro, but I recently installed Ubuntu 12.04 alongside the other two OSes. Now Win 7 wont boot. I made a boot summary with Boot Repair on Ubuntu, and here are the summaries: [http://paste.ubuntu.com/1044305](http://paste.ubuntu.com/1044305) and [http://paste.ubuntu.com/1044287](http://paste.ubuntu.com/1044287).

Can I get some help please? Thanks.

---

### Post by vazduxosbra4kania on 2012-06-18
> **temiyemi said:**
> I had Win 7 installed on my MacBook Pro, but I recently installed Ubuntu 12.04 alongside the other two OSes. Now Win 7 wont boot. I made a boot summary with Boot Repair on Ubuntu, and here are the summaries: [http://paste.ubuntu.com/1044305](http://paste.ubuntu.com/1044305) and [http://paste.ubuntu.com/1044287](http://paste.ubuntu.com/1044287).

Can I get some help please? Thanks.

I am very curious and please tell me , what possible reason could you have to install so many OS`s. I think you could use vmware assuming you got good mashine.

---

### Post by temiyemi on 2012-06-18
Lol. vazduxosbra4kania... Well, I'm just as curious too, what does that mean? 

Anyways, I needed to install Ubuntu, but I didn't want to split RAM running OSes in VMWare, hence I installed directly on HDD. But I resolved the OS boot issue with rEFIt, thankfully. That's a great tool.

Thanks.

---

### Post by YannBuntu on 2012-06-19
Hello
If one day you want to use GRUB (the Ubuntu bootloader), I think you will need to force it not using EFI, by eg :
running Boot-Repair, click "Advanced options", go to "GRUB location" tab, untick the "Separate /efi" option, apply.

---

### Post by temiyemi on 2012-06-19
Noted! Thanks for the hint. Boot Repair is great too!

---

