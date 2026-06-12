---
title: "Kernel update in Dapper 6.06 stops me from booting"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by alanmzifa on 2007-09-10
Hi, my old Dell Laptop runs as a single boot Ubuntu system. 

Last thing I did when I last had it on was accept the auto update which I believe downloaded a new kernel update. 

When I turn it on now I get to the **login and password screens** then it does nothing.** No command prompt, no splash just an empty screen.** There's a short burst of HDD activity then all goes quiet.

*Can someone help me get back to a working system please?* Kernel version trying to load seems to be 2.6.15.29-386.


thanks.

---

### Post by mikeyphi on 2007-09-10
If you can see the Grub screen during the boot process - you should see options to boot into the latest and previous kernels. Just select the previous kernel and you should be able to boot your system. If this is successful you might then want to think about removing the 'new' kernel if it continues to be a problem.

---

### Post by alanmzifa on 2007-09-10
> **mikeyphi said:**
> If you can see the Grub screen during the boot process - you should see options to boot into the latest and previous kernels. Just select the previous kernel and you should be able to boot your system. If this is successful you might then want to think about removing the 'new' kernel if it continues to be a problem.

Thanks for your reply but I've already tries that. Two previous kernels show and I've tried them both and their respective recovery modes. After the password and log-in splash I just get a blank screen.

Have you or anyone else reading this any suggestions for getting around it?

---

### Post by speedy67 on 2007-09-17
> **alanmzifa said:**
> Thanks for your reply but I've already tries that. Two previous kernels show and I've tried them both and their respective recovery modes. After the password and log-in splash I just get a blank screen.

Have you or anyone else reading this any suggestions for getting around it?

I also had trouble with 6.06LTS after the kernel was updated from 2.6.15-26 to 2.6.15-29. The error I got after grub loaded was 

```
mp-bios bug: 8254 timer not connected to IO-APIC
```

and Ubuntu would not boot. After some googling I found the solution by adding "noapic" to the "# defoptions=" line in /boot/grub/menu.lst and then running update-grub.

Ubuntu would boot again, but unfortunately this noapic setting caused some clock errors, for example a task running for an hour only showed as running for only 20 minutes in the system monitor. After setting the previous kernel (2.6.15-26) as default in /boot/grub/menu.lst and removing the noapic from the "# defoptions = " line ubuntu boots again and the clock runs like it should.

Just to be complete, this problem only occurs on my Asus A8V with Athlon64 3000+, and not on my HP EVO with Intel Pentium IV 1.70GHz, both running 6.06LTS server with all updates applied.

Greetings,
Sander

---

### Post by alanmzifa on 2007-09-19
speedy67, thanks for your reply. Mine was an old PIII.  

Same error but I couldn't get any way to edit the file and reboot so it's had to have it's HDD wiped and a fresh install of XP from an OEM disc I have which used to be installed on now upgraded desktop hardware. It even validated itself with Microsoft.

---

