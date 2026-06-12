---
title: "grub usplash problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by kcd on 2007-03-27
grub usplash problem

Sorry is this is not in the right place.... just new at this (first post)

3 micros running Ubuntu 6.06 with no problems, all have lcd monitors.
Upgrade to Ubuntu 6.10 and at grub startup, each lcd display shows an error message indicating that the lcd input must be 1024x768x60hz to display. After about 15 seconds, the normal Ubuntu user/password screens display, and all 3 run normally until shutdown, when the same message is displayed.
Upgrade to Ubuntu 7.04 and the same display problem happens.
This problem is preventing me from upgrading all 3 micros.
I have searched the forums, and so far am unable to find a solution. Lots of video resolution solutions, but nothing on grub startup.
Anyone seen this before? Know the solution?
Detailed micro specs as required (all 3 asus p4 1.6-2.4gig 1gig ram)
Many thanks,
kcd
Edit/Delete Message

---

### Post by dreadlord_chris on 2007-03-28
> **kcd said:**
> grub usplash problem

Sorry is this is not in the right place.... just new at this (first post)

3 micros running Ubuntu 6.06 with no problems, all have lcd monitors.
Upgrade to Ubuntu 6.10 and at grub startup, each lcd display shows an error message indicating that the lcd input must be 1024x768x60hz to display. After about 15 seconds, the normal Ubuntu user/password screens display, and all 3 run normally until shutdown, when the same message is displayed.
Upgrade to Ubuntu 7.04 and the same display problem happens.
This problem is preventing me from upgrading all 3 micros.
I have searched the forums, and so far am unable to find a solution. Lots of video resolution solutions, but nothing on grub startup.
Anyone seen this before? Know the solution?
Detailed micro specs as required (all 3 asus p4 1.6-2.4gig 1gig ram)
Many thanks,
kcd
Edit/Delete Message

you need to edit you /boot/menu.lst file ```
gksudo gedit /boot/menu.lst
```. Down near the bottom you'll find the GRUB menu options for the boot kernels (you'll probalbly have several), look for the lines that start **kernel**:
```

kernel		/boot/vmlinuz-2.6.20-13-386 root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro quiet splash

```
at the end of each kernel line add: vga=791
```

kernel		/boot/vmlinuz-2.6.20-13-386 root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro quiet splash vga=791

```

This should fix ya up....

---

### Post by kcd on 2007-03-30
dreadlord_chris
Many thanks,
Actually vga=791 did not work, but vga=773 did work...:) 
After modifying menu.1st, I had to do a 
'sudo update-grub" and restart, then it all works.
I also tried "=verbose" and was able to see the entire bootup process in text mode.
Thanks again for the help
kcd

---

