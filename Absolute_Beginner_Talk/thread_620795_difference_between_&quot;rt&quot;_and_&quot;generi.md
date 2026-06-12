---
title: "difference between &quot;rt&quot; and &quot;generic&quot; kernels"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by 244f on 2007-11-23
after installing ubuntu audio tools, i noticed that upon bootup there is another kernel on the list. instead of generic, it is rt, i don't understand the difference.. but noticed that when booting up with the "rt" my audio does not work at all.

i checked the menu.lst and here are the two

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=71fba7a8-1993-4b15-9904-7aeaa1fd3c7f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=71fba7a8-1993-4b15-9904-7aeaa1fd3c7f ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71fba7a8-1993-4b15-9904-7aeaa1fd3c7f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


what is the difference between /boot/vmlinuz-2.6.22-14-rt  and  /boot/vmlinuz-2.6.22-14-generic ? i'm going to remove rt from my menu.lst but would like your input before I do so

---

### Post by LaRoza on 2007-11-23
RT is "real time", look into why you have it before doing anything.

---

### Post by 244f on 2007-11-23
how do I do that?
i still don't understand the difference

---

### Post by 244f on 2007-11-24
after installing ubuntu audio tools, i noticed that upon bootup there is another kernel on the list. instead of generic, it is rt, i don't understand the difference.. but noticed that when booting up with the "rt" my audio does not work at all.

i checked the menu.lst and here are the two

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=71fba7a8-1993-4b15-9904-7aeaa1fd3c7f ro quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=71fba7a8-1993-4b15-9904-7aeaa1fd3c7f ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet


what is the difference between /boot/vmlinuz-2.6.22-14-rt and /boot/vmlinuz-2.6.22-14-generic ? i'm going to remove rt from my menu.lst but would like your input before I do so
__________________

---

### Post by hardyn on 2007-11-24
the RT suffix would indicate "realtime" or at least "low latentcy kernel"  the kernel has been modified by the audio extensions to behave a little differently.

as for not having audio, did you have to manually modprobe the audio drivers for the orignial install? you may have to do this with the RT kernel.

---

