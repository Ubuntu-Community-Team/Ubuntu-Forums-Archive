---
title: "How do i use an ethernet modem?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by completelinuxnoob on 2006-01-15
Hi guys i use a realtek Broadcom NetXtreme 57xx Gigabit Controller to connect to the internet on my xp pc.

Ubuntu doesn't seem to recognise the integrated ethernet port on my new pc.The motherboard is an abit kv8 pro.Im running the 64 bit ubuntu with an amd athlon 64.

Can someone who has had this problem bring me through it in tiny baby steps as i'm kinda going crosseyed trying to read some of the other posts

Thanks a million

Liom

---

### Post by bscbrit on 2006-01-15
Exactly what do you mean by "doesn't recognise" - is there no record of the ethernet device, does it describe it as an 'unknown' ethernet device, or does it see it but refuse to do anything with it?

---

### Post by completelinuxnoob on 2006-01-15
in device manager its listed as "Unknown(0x3119)" subheading "networking interface"

since first post i have activated eth0 in networking but still no joy.Firefox tells me it cant find the webpage

---

### Post by bscbrit on 2006-01-15
OK, your device is probably working but hasn't been configured yet.  

Both your ethernet modem and your network interface card (NIC) need to have IP addresses so that they can talk to each other.  Your NIC is actually built in to your motherboard but it still tends to be described as a NIC.

Your modem will already have an address allocated to it and you should be able to get that from your XP machine if you do not already know it.  When we have that, we can decide what address to allocate to your NIC and, with luck, you will soon be up and running.

Please tell me the address of your ethernet modem, either from the manufacturer's documentation or by entering XP, looking at your network devices, TCP/IP, Properties, and let me know the values of the IP address and gateway address that XP is using.

---

### Post by completelinuxnoob on 2006-01-15
address type: assigned by dhcp
ip address: 83.141.95.165
gateway: 83.141.95.1

---

### Post by bscbrit on 2006-01-15
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

OK, follow the guide in the link, making sure that you select dhcp and your gateway as 83.141.95.1.

---

### Post by completelinuxnoob on 2006-01-15
Ive tried the  troubleshooter and im getting to 

"Once the driver is loaded, verify from the output of ifconfig that you have an IP address. 


Code:
mlomker@mlomkernote:/$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:03:0D:33:CC:F0
          inet addr:10.2.3.7  Bcast:10.2.255.255  Mask:255.255.0.0"

My inet address isn't showing up, as we knew, but i don't know how to fix it.

Also if i select dhcp in the graphical network setup i can't type in the gateway

---

### Post by bscbrit on 2006-01-15
Doesn't your code example show that the inet address is  'inet addr:10.2.3.7'?

---

