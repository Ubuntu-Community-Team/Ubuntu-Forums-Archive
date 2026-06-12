---
title: "Virtual Macine Query"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by mcgooie on 2007-04-14
I have successfully setup a virtual machine on Edgy Eft running XP. My question is if this VM is accessing the internet do i have to install antivir/firewall/spyware software on it as well?

Also is it possible to set the virtual machine XP so that it can access an external USB hard drive?

Thanks in advance

---

### Post by Bushfire on 2007-04-14
You will have to anti-virus/firewall it, because as far as Windows knows, it's on a seperate computer.

As for the USB thing, most Virtual Machines would be able to by default, in my experience...
which Virtual Machine software are you using?

---

### Post by mcgooie on 2007-04-14
im using VMware. I noticed a section in the settings for USB and i have enabled it but neither my external drive or flash dive come up

---

### Post by Bushfire on 2007-04-14
Well, I don't have much experience with VMware. Perhaps it would be a better question for a VMware-oriented forum/mailing list. But I'm sure someone here will know...it just ain't me ;)

-Bernard.

---

### Post by mcgooie on 2007-04-14
Im an idiot, its not VMware at all its VirtaulBox i am using. Also, when i select Devices - USB Devices - Western Digital External HDD [0108] i get this error message

[[IMG]http://img132.imageshack.us/img132/2043/screenshotid4.th.png[/IMG]](http://img132.imageshack.us/my.php?image=screenshotid4.png)

---

### Post by hyper_ch on 2007-04-14
I haven't had much luck getting usb devices to work in older versions of VBox... however they work fine in VmWare...
Best thing to do is: Cut your internet conncetion, setup the windows box (just basic install without doing anything) - using the "expand when needed space option" so that it's not like 10GB from the beginning...
Once you've installed it, just make a backup of that machine... later on you'll just have to copy it back...
Then you can put some antivirus on it as well as firewall (well, I don't do anymore - I just use winxp for a few things and I'm not anylonger concerned about viruses... no essential documents are stored there anyway...)

---

### Post by mcgooie on 2007-04-14
i think i have it working now, just needed to setup access group

---

