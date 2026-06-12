---
title: "Wireless Network"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by PC_Wraith on 2006-12-06
Hello everyone, I'm new to Linux. I just installed Ubuntu 6.10 (Edgy Efft) on one of my older PCs. (DELL Pentium III, 800 MHz, 256MBs PC133 SDRAM, 20Gig Hard drive) I like the looks of it, but I haven't really done much with it yet. 

I have a wireless network at home. (Linksys router - USB v1) I would like to install the software, so I can access the internet. Can anyone help me?

I read something somewhere about NDISwrapper? 

I'm not familiar with Linux's syntax / command line stuff, so please be patient with me. Eventually I'm going to ditch the wireless and hard wire the whole house. Until then, wireless will have to do.

I'm going to look for NDISwrapper and it's utilities package and go from there. Any help would be appreciated.

---

### Post by PC_Wraith on 2006-12-06
I downloaded mdiswrapper. It's now sittingon my Ubuntu desktop, but I can't seem to install it. I followed the instructions, but it says that it can't find the program? ](*,)

---

### Post by RMorris78 on 2006-12-06
run the command "lsusb" and post the output.  Well be able to see what chipset it has there, and then we can tell you what route to take to install the appropriate drivers for the adapter.

---

### Post by PC_Wraith on 2006-12-07
I ran the command "lsusb" that you suggested and this is what I got.

> Bus 001 Device 006: ID 13bl:0020 Linksys
Bus 001 Device 001: ID 0000:0000

The file I downloaded is call: ndiswrapper-1.31.tar.gz

---

### Post by PC_Wraith on 2006-12-07
More info on the Linksys USB v1 chipset:

I was told by a friend that the chipset is Broadcom - I hope this helps. I've been doing a lot of reading and I seem to get conflicting reports on what I should be doing. :confused: 

Man, Linux is a nightmare to set up. I'm sure it'll get better once it's all set up properly. I can't see this O/S replacing Windows like some of my friends suggest. It's just too complicated for the average user. However, I look at it as a challenge. :roll:

---

