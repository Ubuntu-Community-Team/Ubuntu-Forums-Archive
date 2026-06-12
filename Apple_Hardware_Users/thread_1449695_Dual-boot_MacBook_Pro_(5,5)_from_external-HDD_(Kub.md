---
title: "Dual-boot MacBook Pro (5,5) from external-HDD (Kubuntu 9.10/10.04)"
date: 2010-04-08
forum: Apple Hardware Users
---

### Post by rantomt on 2010-04-08
Hi!

I tried to look quickly for someone, who'd done this too (with Ubuntu, though this is about Kubuntu), but didn't find any up-to-date information regarding this one. So I'd try to get my MacBook Pro (5.5=mid-2009) to boot via rEFIt Kubuntu 9.04. Now, this did work, but only very limitedly.

I started by downloading rEFIt and making a Time Machine backup of my computer (just in case something goes wrong, which is not new for me at all) and then installing rEFIt. rEFIt installed just fine, I had to though restart twice and press ALT in order to get it show up during every boot. Now, here's where everything went well.

After this I decided to completely erase all data from my Kingston 16 Gb USB-stick (thumb drive one may prefer) and made it to use FAT. After this I booted to my live-cd, started to install the 9.04 (I couldn't find my 9.10 at that time) and this took some time but seemed to go very well. I did tell the installer to use all space from Kingston, not from my SSD (since I don't want any data of Kubuntu on my SSD, I don't have much space on it and thus I'm using external-HDD later on).

Now, after the installation, something went badly wrong, since I lost the whole rEFIt. No, there was no Apple-logo nor boot-menu, just gray background with folder marked with question-mark. Now, this has happened to me before as well but I've always solved it with one, stupid method : get rid of Kubuntu and just use the OS X. This is not an option anymore, since I do want to get this to work this time around.

So now that I'm trying this again I'd like to know, that has anyone succeeded on installing 9.10 on external drive on MacBook Pro (5,5) with rEFIt? I'm going to use USB-enclosure for my HDD so yes, I'm on USB this time as well. The point is to keep my SSD clear of Linux, since (as I already mentioned) don't have that much space on it left. And if yes, then **how exactly**? I'm  a beginner here so I'd really appreciate detailed instructions.

I'd also clear out that I have not booted via rEFIt to Kubuntu, since I had no chance to do so. I've used the live-cd of 9.04 and got it to boot via that by selecting "Boot from first HDD"/etc.

Thanks in advance for replies. :)

---

### Post by linuxopjemac on 2010-04-08
I have a link for you, about installing on USB media. I tried to do it once (without the manual) but I did not succeed. It all depends on the firmware of your Mac, whether it will boot from USB or not.

[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

---

