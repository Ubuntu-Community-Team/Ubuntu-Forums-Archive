---
title: "KVM Trouble"
date: 2005-08-26
forum: Bug Reports / Support
---

### Post by gruehagen on 2005-08-26
I have successfully installed Ubuntu but I have 2 PC's and they are connected thru a USB KVM switch. As soon as I switch away from Linux and return my installation freezes. Is there any way to fix this? I like the way Ubuntu looks but I am stuck.

---

### Post by msgyrd on 2005-08-27
Don't switch away, ever!!!!

Anyways, to maybe help some, I think your problem lies with your KVM being a USB version.  I have a PS/2 KVM switch and have never encountered this.  There is probably something going on with the "hotplug" kernel module (a pause in sending data back and forth via USB from the KVM as it switches your hardware over might cause this).  If the loaded kernel has some issue like it's drivers crashing because of interruption, then it would be understandable that your installation would fail.

I don't know what a solution would be.  My first guess would be to try using one of those USB->PS/2 adapters that comes with mice and see if avoiding the USB driver keeps your installation from stalling.

---

### Post by the_person0 on 2005-09-04
im having a similar problem, whenever i switch back to ubuntu the keyboard and mouse lock up and take a long time to return to working and more often than not never start working again,  and i have a ps2 switch. a solution i have heard for this problem is to remove all keyboards and mice except the one on the kvm switch.  the problem that i encountered however is that my machine is a laptop.

---

### Post by Technoviking on 2005-09-08
I have had luck by unplugging and replugging my mouse, to unfreeze my linux box on a KVM.

---

### Post by the_person0 on 2005-09-08
were you using usb or ps2?, when i tried to do that nothing happened.

---

### Post by the_person0 on 2005-09-13
i personally have a trendnet tk-205i and the problem was fixed by shutting everything down and plugging it alltogether then booting it up all at once, don't know if it will work for you but it worked for me.

---

