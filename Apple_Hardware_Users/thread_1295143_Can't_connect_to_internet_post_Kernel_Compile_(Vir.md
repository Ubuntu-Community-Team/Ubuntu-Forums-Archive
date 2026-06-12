---
title: "Can't connect to internet post Kernel Compile (VirtualBox Macbook)"
date: 2009-10-19
forum: Apple Hardware Users
---

### Post by Elguapo_85 on 2009-10-19
I compiled the kernel using a the preset configuration for macs as referred to by one of the guides here. I swear I have seen this question somewhere before but I can't seem to find it. Anyway, before compiling the internet (wireless) was working fine, but now there are no networks available. I am running it in Virtualbox. So please help me recover the internet! Thank you.

---

### Post by Bachstelze on 2009-10-19
What is the host OS, and how is your virtual network configured?

---

### Post by Elguapo_85 on 2009-10-19
Host is snow leopard, guest is Ubuntu. Network is set to NAT. It was working before I compiled the Linux Kernel.

---

### Post by Bachstelze on 2009-10-19
> **Elguapo_85 said:**
> Host is snow leopard, guest is Ubuntu. Network is set to NAT. It was working before I compiled the Linux Kernel.

Your kernel probably doesn't have support for the NIC your virtual machine uses. Can you please post the kernel config and tell us which NIC your VM uses?

---

### Post by Elguapo_85 on 2009-10-19
Here's a link to the kernel config: 
[http://en.gentoo-wiki.com/w/images/0/0d/Kernel_2628tuxonicer1.txt](http://en.gentoo-wiki.com/w/images/0/0d/Kernel_2628tuxonicer1.txt)

I am not sure where I find the NIC setting of Virtual Box... is it this?
Adapter type is set to:
PCnet-FAST III

Other choices are:
PCnet-PC II
IntelPro 1000 MT Desktop
IntelPro 1000 T Server
IntelPro 1000 MT Server

---

### Post by Bachstelze on 2009-10-19
You need to enable PCNET32 in your kernel confguration.

---

### Post by Elguapo_85 on 2009-10-19
Ok, I added it, recompiled and it worked! Thank you so much :P

---

