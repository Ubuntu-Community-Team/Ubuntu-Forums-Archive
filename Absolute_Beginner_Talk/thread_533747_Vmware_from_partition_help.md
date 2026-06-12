---
title: "Vmware from partition help"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-08-24
I'm trying to load an existing partition using vmware and came across this guide: [https://help.ubuntu.com/community/VMware/Workstation/NativeVirtualMachine?action=show&redirect=VMWareBootInNativeandVM](https://help.ubuntu.com/community/VMware/Workstation/NativeVirtualMachine?action=show&redirect=VMWareBootInNativeandVM)

Something I got stuck on is the fourth step.

4. Once it is created; in the VM copy c:\windows\system32\hal.dll to a floppy or any other medium by which you will be able to transfer it to the native install

I don't understand this at all, where can I find the windows folder or system32 for that matter in VM? The only thing I got is the .vmx file which is the virtual image of Windows XP but no actual files.

---

### Post by cyberdork33 on 2007-08-24
> **kcirtap said:**
> I'm trying to load an existing partition using vmware and came across this guide: [https://help.ubuntu.com/community/VMware/Workstation/NativeVirtualMachine?action=show&redirect=VMWareBootInNativeandVM](https://help.ubuntu.com/community/VMware/Workstation/NativeVirtualMachine?action=show&redirect=VMWareBootInNativeandVM)

Something I got stuck on is the fourth step.

4. Once it is created; in the VM copy c:\windows\system32\hal.dll to a floppy or any other medium by which you will be able to transfer it to the native install

I don't understand this at all, where can I find the windows folder or system32 for that matter in VM? The only thing I got is the .vmx file which is the virtual image of Windows XP but no actual files.

Step one in this how to is to install XP. You can mount the XP partition in Ubuntu and copy the file you need.

---

### Post by kcirtap on 2007-08-24
> **cyberdork33 said:**
> Step one in this how to is to install XP. You can mount the XP partition in Ubuntu and copy the file you need.

I've already installed XP but I don't see the point in copying a file from windows/system32 to windows/system32. It says, copy the file from system32 into the native Windows system32 :confused:

---

### Post by cyberdork33 on 2007-08-24
> **kcirtap said:**
> I've already installed XP but I don't see the point in copying a file from windows/system32 to windows/system32. It says, copy the file from system32 into the native Windows system32 :confused:

OK, I misunderstood. You have to start XP in the VM to get the other hal.dll
I think it is implied that you are to install XP to the temporary virtual hard drive.
In the VM, hardware is different (virtual hardware) than "native" therefore, you need the hal.dll from both "systems" to make two hardware profiles.

[quote=original how to]7. Rename hal.dll that you copied to the floppy from the VM to halvm.dll  
8. Copy it to c:\windows\system32 in the native install[/quote]

---

