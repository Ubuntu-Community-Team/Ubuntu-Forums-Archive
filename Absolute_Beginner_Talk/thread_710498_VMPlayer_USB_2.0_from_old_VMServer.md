---
title: "VMPlayer USB 2.0 from old VMServer"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by sacedric on 2008-02-28
Hi
I initially installed VMServer and created a XP Pro guest VM. After many Windows updates etc, and installing iTunes, mapping network drives etc, I discovered VMServer does not support USB 2.0. So I then installed VMPlayer (which according to VMWare supports USB 2.0).
I can start my Windows XP VM but when I connect the USB devices, it still keeps saying it is not connected to a HI-SPEED USB. Does anyone know if this is an XP issue on my VM or some setting in my .vmx file. I read somewhere about needing to update VMtool or the actual VM but not sure how to do that.
Any help would be appreciated.

---

### Post by chrono310 on 2008-02-28
I'm not sure if you can do it in VMWare Player, but I know you can install VMWare Tools with VMWare Server. That may help, but I'm not sure as I haven't tried to use usb 2.0 in a guest before.

Just click on VM -> Install VMWare Tools while the VM is running and Windows will act like a CD has just been insterted and will go through the VMWare Tools install.

---

