---
title: "Required Kernel Toshiba support"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-04-03
I how do I enable kernel support for my Toshiba Satellite A100-SK9 so that I can use the toshset utility ?
Is there a module or will I have to build a kernel ?

---

### Post by GTvulse on 2008-04-04
Do a "sudo modprobe toshiba_acpi" and test if toshet works or not. If it doesn't, your particular model may not be supported. If it is supported, edit /etc/modules and add toshiba_acpi to the list and save the file. The driver will be loaded automatically when you boot up the machine.

---

### Post by noorez on 2008-04-04
Hmm....it didn't work.....is there another way to get support for my model ?

Also, is the toshiba support needed to control CPU, LCD, fan in my laptop ?

It seems as if the cpu controller that comes with Ubuntu doesn't work well ?  when I'm doing some processor intensive stuff such as running VirtualBox, the CPU temp shows at 100 C's ! 

Also, the brightness app doesn't function well. The only way i can properly set up my lcd brightness is by do this:

# echo <setting> -n > /proc/acpi/video/VGA/LCD/brightness

---

### Post by GTvulse on 2008-04-04
Hmm... I'm afraid not, at least without hacks like adding proc serttings to /etc/rc.local. I strongly suggest you post a bug to launchpad following the [guidelines for kernel bugs]("https://wiki.ubuntu.com/KernelTeamBugPolicies"). With luck they may be able to include the fixes in Hardy's kernel.

---

