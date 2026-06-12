---
title: "Installing Ubuntu on VMWare"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2007-03-25
Hi!

I've been using Ubuntu for a while as my second OS, however most of the time I work on WinXP. It's getting quite annoying switching between them, so I'm thinking removing Ubuntu and installing it as a virtual machine.

However I'm not sure which VMWare product should I use - VMWare Player or Server? I'd like to be able to run some http and db servers, however mostly for developing and testing some simple apps.

Do I have to download some already made special Ubuntu version for VMWare or can I just use Ubuntu CD to create a new one?

What about the network? Is it possible to assign different IP address than my WinXP machine has to virtual Ubuntu machine, or does VMWare use some NAT mechanism?

How should I install it? Can I remove both Ubuntu partitions (ext3 and swap) and create a new NTFS partition for the virtual machine?

Thank you in advance

---

### Post by lamalex on 2007-03-25
you can use either one, if you use vmware player youll need to download an ubuntu .vmx file. if you use server you can install ubuntu from disk. i think with server window needs IIS to work. you can use NAT or have ubuntu with its own IP via bridged networking. uninstalling ubuntu can be tricky because of grub. I've never done it so i don't know, someone else can help you with that.

---

### Post by NyteGeek on 2007-03-25
> **Iamalex said:**
> you can use either one, if you use vmware player youll need to download an ubuntu .vmx file. if you use server you can install ubuntu from disk. i think with server window needs IIS to work.

Only if you want a web management interface, otherwise there is no need for IIS. If you are using XP Pro you can install IIS if you need it.

---

### Post by lamalex on 2007-03-25
> **NyteGeek said:**
> Only if you want a web management interface, otherwise there is no need for IIS. If you are using XP Pro you can install IIS if you need it.

really? last time i tried to install vmware on windows it wouldnt install without IIS. good to know. either way server is much more flexible, i recommend that.

---

### Post by NyteGeek on 2007-03-25
> **Iamalex said:**
> really? last time i tried to install vmware on windows it wouldnt install without IIS. good to know. either way server is much more flexible, i recommend that.

there is more than one file you can select from when you download vmware server for windows, just download the client package if you do not have IIS.

---

### Post by framinglory on 2007-03-25
if you remove ubuntu's partition grub won't load, so you will have to fix the master boot record for windows xp. 
this link has a thorough explanation of replacing windows mbr. you will need your windows xp disk to do this procedure though.

[http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c28621675.mspx#EJ5AE](http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c28621675.mspx#EJ5AE)

---

### Post by g0nzo on 2007-03-25
Thanks a lot guys.

Just one more question - do I need to boot from a CD to run fixmbr, or is it possible to run it when I select Recovery Console (or something similar, can't remember exact name) when booting from the hard disk?

EDIT: Nevermind, already done it by booting from the hard disk.

---

### Post by Ambimom on 2007-03-25
Very simple procedure:

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

You need the recovery console, and you'll need the XP disk.

VMWare Server works just fine out of the box; it automatically bridges the ethernet.

You might also try Parallels for Windows/Linux.  There's a free trial.  

.

---

### Post by victorbrca on 2007-03-25
You can also download an Ubuntu image ready to use from the VmWare site if you are too lazy to install. Tha's what I usually do :) 


[*_Link_*]("http://www.vmware.com/vmtn/appliances/directory/693")



Vic.

---

### Post by Marsolin on 2007-03-27
Have any of you gotten multiple CPU support working with VMware Server? I don't see any difference once I boot into Kubuntu and there doesn't appear to be a separate kernel for smp support.

---

