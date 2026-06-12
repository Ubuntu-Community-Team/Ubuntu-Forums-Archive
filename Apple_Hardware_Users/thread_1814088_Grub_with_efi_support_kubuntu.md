---
title: "Grub with efi support kubuntu?"
date: 2011-07-28
forum: Apple Hardware Users
---

### Post by kaizo2560 on 2011-07-28
Hi I currently have kubuntu 11.04 on my laptop harddrive that is in an external enclosure. i.e. it is on the outside of the machine and connect to the computer via USB.

It works fine on my windows machine and I love the fact I could also plug it into my kubuntu machine at home and use it as a regular harddrive too.

Although my new job basically wants me to use a mac. Apparently you need something called an efi support on my grub so here are the questions:


[LIST=1]
[*]Does kubuntu 11.04 have efi support on its grub i.e. can I plug my hard drive with my kubuntu on via USB to a mac and boot from there? If not how could I get one?
[*]Also does getting efi support make any difference when I plug it into my kubuntu machine at home? So can I back up my data as I used to?(by simply plugging it in)
[*]Could I still plug it into my windows machine as before and work if I get efi support?
[/LIST]
All help is welcome and thanks in advance :)

p.s. If you have trouble with heavy laptops give external harddrives a go its like carrying an ultra light linux machine (with all your data in it)!

---

### Post by pindar on 2011-07-29
If I understand your post, you want to be able to boot up your mac from an external hard drive. Good news first: yes, this is possible; I have an external usb hard drive with kubuntu 11.04 and can boot my mac from that, the grub version supports this. The bad news: this hard drive needs to have a special setup: it needs to be partitioned as GUID, the first partition needs to be an EFI system partition which holds the grub.efi image. Your current hard disk is very unlikely to have this setup, so you will probably need to reformat it. I have no idea if the same hard disk would also boot a windows computer, I have never used windows and hope I will never have to.

---

### Post by kaizo2560 on 2011-07-29
Hi thanks for your reply :)

In that case when I get my mac I will reinstall kubuntu with the efi image on my external

Again thanks for your help :)

---

