---
title: "install on sd card?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Jdratcliffe on 2007-05-01
is it posible to run normal install off sd card .

reasons i intrested in ubuntu for ages just brought new laptop and forget to refomatted hdd but it has sd card slot from whic i can boot from but i m wondring which size sd card i would need 

laptop is
Tosiba tecra m5 
model PTM51E-0NC03JEN


[http://www.dabs.com/productview.aspx?Quicklinx=4BCB&SearchType=1&SearchTerms=tecra+m5&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=49170000](http://www.dabs.com/productview.aspx?Quicklinx=4BCB&SearchType=1&SearchTerms=tecra+m5&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=49170000)

any ideas cos i wanna run ubuntu and join the fun ....:KS

---

### Post by starcraft.man on 2007-05-01
Ummmm, well can't say I'm that much of an expert at SD, I only really use a 1 GB one for my PSP. If you want to just do a simple install with the CD installer live or alternate, you will need  700 MB of space and since I don't think they make them that size, you would need a 1 GB minimum to fit the data on it. 

I don't know however if your computer would recognize it as a bootable installer, can't say I've ever booted any SDs. Question: Is there a reason you can't use the live or alternate Feisty installer? Basic rule of computing is that simple is best >.>.

---

### Post by Jdratcliffe on 2007-05-01
:guitar: any other ideas? :guitar:

---

### Post by starcraft.man on 2007-05-01
Not really... I mean 99% of people install Ubuntu from the CD. Does your labtop not come equipped with a CD drive? Apart from that I believe there is a way to do a network install but thats gonna require more effort and time than just using the cd.

---

### Post by Jdratcliffe on 2007-05-01
yea it has a cd drive but i was after a way to get a duel boot system without having to reinstall win and partian hdd and hasle involed so thought i could use the sd card as hdd when installing ubuntu so i was after the size i need the largest sd card i can find is a  8gb would this be enough to install to ...? or too much?:confused:

---

### Post by rondmc170 on 2007-05-01
I don't think that it is possible to have GRUB, or any other bootloader, recognize an SD card as a hard drive. I believe it can be done in virtualization, but not from loader.

I would suggest partitioning. It's reletively painless and Ubuntu can help you do it right from the live CD. Otherwise, for a very easy graphical partitioning setup, download an iso image for Gparted and partition with that. It's graphical and very supurb. Then take the Ubuntu CD and install. That is how I always do it, and it's a piece of cake.

---

### Post by Jdratcliffe on 2007-05-02
does this partion with a os and data on disk or do i need to reformat?

---

### Post by lukew on 2007-05-02
> **Jdratcliffe said:**
> does this partion with a os and data on disk or do i need to reformat?

You can resize the primary dos partition during installation. Can i add that installing Linux on a sd card mounted vis a usb reader would be really really slow. As long as your BIOS supports booting through a device, ie network, hd, usb etc you can run an OS from it.

---

### Post by Jdratcliffe on 2007-05-04
the sd card is inbuilt

---

