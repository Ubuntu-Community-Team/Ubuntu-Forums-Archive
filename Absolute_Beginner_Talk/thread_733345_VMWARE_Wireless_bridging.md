---
title: "VMWARE Wireless bridging"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by georgew77 on 2008-03-23
Hi,

I have got ubuntu up and running on a Vista PC within VMWare and doing some coding but I cant get on the internet from within ubuntu without plugging a cat cable into the laptop.

I have bridged the wireless to VMnet1 but that does seem to work, bit at a loss of what I need to do in terms of setting an IP address, the laptop gets one automatically the vm shouldnt really need one but I assume ubuntu needs one to work

I so confused :confused::KS

Any pointers will be greatly recieved...

G.

---

### Post by iansane on 2008-03-23
I believe briging means that your vista pc should make a brige basically to the virtual machine, so when ubuntu looks for an IP it gets the IP from the same router or modem that the vista machine gets its IP from. Like you said, it should not be a problem, if I understand briging right it's vistas job to pass the IP through vmnet to the machine. I'm curious to learn what the problem is.

---

### Post by georgew77 on 2008-03-23
Well yeah in theory you would think it would work but it is microsoft.

VMnet1 is labelled "host only"

The other option would be bridging VMnet8 which is NAT....  I might try that now.

G.

---

### Post by georgew77 on 2008-03-23
So bridging VMnet8 disconnects everything from the web.

Somebody must have done this before, im only about a week out of blowing of this vista install all together and going linux I reckon.

G.

---

### Post by georgew77 on 2008-03-24
Okay I couldnt get it to work.

NAT works after some playing.  For completeness you have to do the following

Configure the virtual machine before booting to use VMnet8 (NAT)
Boot the vm machine
Note down gateway and subnet from host->virtual network settings for VMnet8
Go to the ubuntu vm
Choose a random IP which is in the same domain as gateway, set the subnet and
VIOLA

It should be on the world wide web wirelessly.

G.

---

