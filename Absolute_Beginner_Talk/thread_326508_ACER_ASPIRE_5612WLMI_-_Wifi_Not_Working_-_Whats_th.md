---
title: "ACER ASPIRE 5612WLMI - Wifi Not Working - Whats the best way to get working?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by williamt on 2006-12-27
Hello everyone, before I ask you all to help me, I think it's polite to introduce myself, my name is William Tildesley, I live in the UK and have been a Ubuntu user for less that 5 hours, in those five hours It's been a great experience.  I'm a mac man, but was given an Acer Aspire 5612WLMI as a gift, now I don't like windows, so I thought I'd check out Linux and especially Ubuntu, I've seen good review about it, anyway, everything (apart from my wifi) works perfectly/

But like I say the wifi is not working, now like I've said to you I'm really a complete 'n00b' at Ubuntu/Linux so please excuse me for not know how to fix this before hand, so basically, can someone point me in the right directions to getting my wifi up and running, my main problem is the fact that I don't have a clue what my wifi card (internal) is, it would help I know if I new what it was, I have contacted Acer asking this but I probably wont get a reply until after the new year and I'd like to get connected.

Any help would be much appreciated.

Thanks,

William

---

### Post by williamt on 2006-12-28
Just so you know I'm running Ubuntu 6.1, if thats of any help to you.

---

### Post by KenSentMe on 2006-12-28
You could begin your search here: [https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

On help.ubuntu.com there are a lot of documents on how to do certain tasks in Ubuntu, so for other problems you could first search the [http://wiki.ubuntu.com](http://wiki.ubuntu.com) or go straight to [http://help.ubuntu.com](http://help.ubuntu.com).

For your wireless card it's necessary that you know what kind of wireless card/device you have. That way you can find out what the best way is to get it working. Most cards/chipsets are mentioned in the docs, so check there.

Oh, btw: you have version 6.10 (Edgy Eft), the version number stands for the release year (2006) and month (10, october).

---

### Post by williamt on 2006-12-28
> You could begin your search here: [https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

On help.ubuntu.com there are a lot of documents on how to do certain tasks in Ubuntu, so for other problems you could first search the [http://wiki.ubuntu.com](http://wiki.ubuntu.com) or go straight to [http://help.ubuntu.com](http://help.ubuntu.com).

Okay thanks, I will check that out.

> For your wireless card it's necessary that you know what kind of wireless card/device you have. That way you can find out what the best way is to get it working. Most cards/chipsets are mentioned in the docs, so check there.

Yep, I will check my documents out, just need to dig them out.

> Oh, btw: you have version 6.10 (Edgy Eft), the version number stands for the release year (2006) and month (10, october).

Really? Well you learn something new everyday.

---

### Post by OffHand on 2006-12-28
> **williamt said:**
> Okay thanks, I will check that out.



Yep, I will check my documents out, just need to dig them out.



Really? Well you learn something new everyday.

I f you open a terminal and type ' lspci' (without quotes) it will show all pci devices. The 'lsusb' will list all usb devices. It should show up in the lspci list.

---

