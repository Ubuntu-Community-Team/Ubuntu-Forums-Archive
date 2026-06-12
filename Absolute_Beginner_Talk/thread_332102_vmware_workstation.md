---
title: "vmware workstation"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-05
Hi all,

I am new to ubuntu and installed 6.10, very satisfied. To access winxp I installed vmware workstation by this very useful link: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

I did evrything as default, so nothing changed. After install, I can see VMWare workstation. When I click on it, it started but never saw winxp, there is a directory created /vmware/Windows XP Professional and under it, there are some files such as .log, .vmx, .vmdk. That's all I get, I could not open virtual machine at all. When I was waiting to connect (about ~30 sec) it was saying configuration tools are not set but actaually I went over default configuration again, I dont know why it happened. It's getting worse: now even I cannot open vmware server although there is still that logo. I tried sudo but it gave same response.

Any help appreciated,

Thank you
findik

---

### Post by findik1 on 2007-01-05
I can open with sudo vmware. However it cannot find operating system. Do I have to install winxp again for vmware, or is there a way that it can see winxp that was already installed when I bought this laptop (before linux installation?
thanks
findik

---

### Post by dbqp on 2007-01-05
Yes, you must install the operating system to reside in the allocated disk space you have set for this virtual machine. It's like installing onto a new computer...

You can't just install VM Ware and expect to retrieve your files and WIN XP OS located on your hard drive elsewhere.  The VM Ware creates a Virtual Machine. This vm will use physical hard drive space and system resources (mem, cpu, sound, etc...), but you have to create it from the "ground" up.

---

### Post by dbqp on 2007-01-05
Also, vm ware tools gets installed AFTER the OS has been installed.

---

### Post by findik1 on 2007-01-05
ok thank you

---

