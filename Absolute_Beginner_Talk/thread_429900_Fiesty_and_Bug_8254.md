---
title: "Fiesty and Bug 8254"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by paulholbrook on 2007-05-01
I have just installed Fiesty on by Compaq PC.  I am using Grub to boot Fiesty and get the 8254 error message.  I have found several forum threads about this problem.

One solution was to use e during the boot and add noapic to the Kernel line and then   b   to boot.  That got me up and running.

The next instructions were to go to the Terminal and enter

sudo getit /boot/grub/menu.lst

and append noapic to the #defoptions=    line.

I did than and saved it.

Next i tried

update grub

and I got the invalid command message

What do I do now?  I am brand new to Ubuntu

---

### Post by icechen1 on 2007-05-01
> **paulholbrook said:**
> I have just installed Fiesty on by Compaq PC.  I am using Grub to boot Fiesty and get the 8254 error message.  I have found several forum threads about this problem.

One solution was to use e during the boot and add noapic to the Kernel line and then   b   to boot.  That got me up and running.

The next instructions were to go to the Terminal and enter

sudo getit /boot/grub/menu.lst

and append noapic to the #defoptions=    line.

I did than and saved it.

Next i tried

update grub

and I got the invalid command message

What do I do now?  I am brand new to Ubuntu
When you changed the grub menu.lst you don't need to update it,it will update itself,i think.

---

### Post by paulholbrook on 2007-05-01
I rebooted and got the 8254 bug back after I had saved the update.

---

### Post by denver on 2007-05-01
Scroll down to the line:

```
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=77ca33d3-9321-4e62-b3b9-8413ffdc6eb6 ro quiet splash **noapic**
```

and add the option there as well...it should take care of the problem.

NOTE !!

the option root=UUID=77ca33d3-9321-4e62-b3b9-8413ffdc6eb6 may differ from yourse but the rest should be the same.

---

### Post by paulholbrook on 2007-05-01
I added noapic to the line you suggested in boot/grub/menu.lst and saved it.  When I rebooted, I still had the 8254 bug.  I think I need a command to update and refresh the boot process with the changes.

When I edit the grub entry at boot time and add "noapic" to the kernel line, it comes up correctly.

---

