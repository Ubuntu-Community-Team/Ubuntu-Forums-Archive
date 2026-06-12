---
title: "vmware/phoenix bios has no usb controller?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-05-31
I dunna get it.  

I installed XP on VMware and cannot contact my flash drive which is seen just fine by Ubuntu 7.04.  

It does not appear within XP, it does not appear within VMwares VM > removable device, USB controller does not appear within XP's My Computer > Properties > device manager, USB option does not appear within PhoenixBIOS Utility > Advanced > I/O Device Configuration.

Any help would be superb.  Thnx

---

### Post by jd65pl on 2007-05-31
I think you may need to unmount it in ubuntu before it is visible in vmware. It should then appear in VMwares VM > removable device

---

### Post by il-luzhin on 2007-05-31
I tried that, nothing

---

### Post by jd65pl on 2007-05-31
Did you try restarting vmware once you had unmounted ur usb?

---

### Post by il-luzhin on 2007-05-31
I tried that as well, nothing.

---

### Post by Atomic Dog on 2007-05-31
If you click on "Edit Virtual machine settings" is the USB controller listed as present?  If not can you add it?  Is the button ticked to auto connect new USB devices?

---

### Post by il-luzhin on 2007-05-31
Under VM > Settings > Hardware there is no USB controller and the add option is grayed out (not accessbile)

---

### Post by il-luzhin on 2007-06-01
bump

---

### Post by mjecha on 2007-06-11
I was looking for a solution to the same problem when I happened across your post. A good deal more searching on the vmware.com discussion boards provided my answer:
You have to add a usb controller while the vm is powered down.
I had no option to add and no usb controller in my vm, though fully function usb exists on the host. After powering down the vm (in this case, I'm running ubuntu virtually on an xpsp2 host), The "Add..." button is available, and it acts like an add hardware wizard.
From there you should have access to all your devices in the vm.
Good luck!

---

### Post by il-luzhin on 2007-06-12
I couldn't find an "Add" button.  Where did you spot it?

---

### Post by lazyart on 2007-06-12
> **il-luzhin said:**
> Under VM > Settings > Hardware there is no USB controller and the add option is grayed out (not accessbile)

You have to shut the VM down in order to add the virtual USB controller.

---

### Post by mjecha on 2007-06-21
This is the linux vmware, but the interface is identical to the one running in windows. If the vm is powered down, 
1. click "Edit Virtual Machine Settings"
[ATTACH]36012[/ATTACH]
 and "Add..." should be on the left side at the bottom
[ATTACH]36013[/ATTACH]

Apologies for the slow reply; it took me a while to realize there was more activity here.

---

