---
title: "Black screen"
date: 2021-08-30
forum: Apple Hardware Users
---

### Post by myboblife on 2021-08-30
Hello everyone,

So I just recently installed Ubuntu on an external HDD in the mindset that I could use it on different machine. While I use it on mt desktop pc, everything is good, but when I try to use it with my macbook, then it dosen t work. When I boot it up I pressed the option key to select the boot option, then I have 2 choices either the Macintosh HD which I have my MacOs on and there is an EFI boot (wich I presumed is the external HDD). The problem is that when I try to boot it, nothing happen. Its just a black screen and I couldn t find anything online. Please help me with this, I have to use it for school and its a real pain right now.

Thanks in advance.

---

### Post by slickymaster on 2021-08-30
*Thread moved to **Apple Hardware Users**.*

---

### Post by scorp123 on 2021-08-31
> **myboblife said:**
>  So I just recently installed Ubuntu on an external HDD in the mindset that I could use it on different machine. 

No idea why you assumed that this would even work!? The PC you installed this on probably has very very different hardware from your Apple MacBook. And MacBooks produced after 2016 will not work with Linux anyway because of the Apple T2 security chip those MacBooks have. The T2 chip will block pretty much every hardware component from working with Linux. And the very newest MacBooks don't even have an Intel CPU any more, they are all based on Apple's M1 CPU design. You cannot boot an Operating System written for Intel CPU's on a different chip architecture such as the Apple M1.

> **myboblife said:**
>  I have to use it for school and its a real pain right now. 

Then boot into your MacOS, get Virtualbox and then install Ubuntu into a virtual machine. That's assuming you even still have an Intel CPU in your MacBook. If you have an Apple M1 CPU ... then good luck, I have no idea what virtualisation options are available to you on that architecture. "Parallels" I guess? But that product isn't free.

---

### Post by dirkjot on 2021-09-25
Installing on a harddisk on computer 1 and using on computer 2 may not work, it is best to install and use on the same computer.

I also had the blank screen issue, ReFind helped me out.  See also this pretty recent and well written article:  [https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)

As you can see from that article, Ubuntu runs on Mac hardware with T2 chips.

---

