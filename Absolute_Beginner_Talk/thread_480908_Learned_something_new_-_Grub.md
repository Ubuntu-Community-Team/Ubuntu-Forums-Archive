---
title: "Learned something new - Grub"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by NJC on 2007-06-21
I was following the [SuspendHowto]("https://help.ubuntu.com/community/SuspendHowto") and learned a few things about menu.lst:
 
First, defoptions will add boot options at end of boot line. Example: ```
# defoptions=**quiet splash acpi=off** 
```
 
adds
```
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro** quiet splash acpi=off**
```
 
Second, to specify which drive Linux will boot from (IE not hda1), use kopt. Example:```
# kopt=root=**/dev/hdb1 ro**
```
 
adds
```
kernel        /boot/vmlinuz-2.6.15-26-386 root=**/dev/hdb1 ro** quiet splash acpi=off 
```
 
After the changes have been run to defoptions and kopt lines, use```
sudo update-grub
``` And all of the appropriate grub boot options will be updated. This was VERY HELPFUL to know since everytime I ran a security upgrade, my machine would not boot because kopt was set to /hda1 and my linux is on /hdb1. As well, I'd lose the custom acpi=off option too - and I never knew why. 
 
NOTE: If you have a dualboot line for Win, DON'T put corresponding code in this section of menu.lst:```
## ## End Default Options ## [...] ### END DEBIAN AUTOMAGIC KERNELS LIST
```
 
The security upgrade will wipe it out. For more info on Grub options, see this link:
 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

