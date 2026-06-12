---
title: "VirtualBox not working"
date: 2012-11-08
forum: Any Other OS
---

### Post by tech291083 on 2012-11-08
Hi,
 
I have just installed the latest VirtualBox on my Win 7 64+ bit home edition OS. The pc works fine. I tried to install Ubuntu 12.04 LTS (32 bit) and Fedora 16 (32 bit) in VirtualBox. Both were installed one by one. But on each ocassion there was a problem. While Ubuntu install well it did not boot after the installation finished and it threw the CD out as it the case with normal install on a physical HDD, VirtualBox showed an errro saying > oracle vm virtualbox manager is not responding
 
When Fedora install finished well and it also kicked the DVD out asking me too reboot, it again showed the same error ie QUOTE]oracle vm virtualbox manager is not responding[/QUOTE] when I pressed reboot to finish the 2nd part of install which requires a normal user creation. 
 
My pc has a lot of space left (HDD is 500 GB), RAM is 4 GB. What could have gone wrong here? Please help me out, thanks.

---

### Post by tech291083 on 2012-11-08
Please have a look at the screenshots attached, thanks.

---

### Post by 2F4U on 2012-11-08
I would guess this is a Windows error, probably due to high load on the machine. How is your CPU and RAM load when this happens? How are the VM's configured (CPU, RAM, etc.)?

---

### Post by tech291083 on 2012-11-08
> **2F4U said:**
> I would guess this is a Windows error, probably due to high load on the machine. How is your CPU and RAM load when this happens? How are the VM's configured (CPU, RAM, etc.)?
 
 
Hi,
 
Thanks for the reply, appreciated.
 
Just after my last post, I re-install VirtualBox and tried to install Ubuntu 12.04 LTS (32 bit) VirtualBox. I encountered the same problem just like before, installation went smoothly, but it did not reboot. I have attached screenshots to this post to make my problem clear. There is also an image displaying VM configuration ie CPU, RAM etc. Please help me this is driving me nuts. Thanks.

---

### Post by pkadeel on 2012-11-08
This is not a solution to your problem. Just an observation regarding your client configuration. It may or may not solve your problem.

Apparently you have allocated only one CPU to client therefore you do not need VTx/AMD-V enabled.

Also check that "Live CD" option is not selected when you highlight the IDE subnode in Settings > Storage

---

### Post by tech291083 on 2012-11-08
> **pkadeel said:**
>  
Apparently you have allocated only one CPU to client therefore you do not need VTx/AMD-V enabled.
 
Should I enable all the 4 cpus? I thought that since mine is just a simple desktop pc with only one cpu, so I do not need to use 4 cpus for my Ubuntu install. 
 
>  
Also check that "Live CD" option is not selected when you highlight the IDE subnode in Settings > Storage 

 
Sorry, I can't find the Live CD option. Thanks for your help so far, appreciated.

---

