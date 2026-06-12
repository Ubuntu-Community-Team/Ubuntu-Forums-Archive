---
title: "What is latest Dapper kernel image?"
date: 2006-10-17
forum: Apple PPC Users
---

### Post by seatea on 2006-10-17
I have been troubleshooting  my yaboot  configuration trying to get my firewire install of ubuntu to boot, which  is not  working right yet, and noticed two boot images in /boot in my main system on my internal hard drive which is booting ok. One  is vmlinux-2.6.15-26-powerpc and the  other is vmlinux-2.6.15-27-powerpc. The symbolic link vmlinux points to the vmlinux-2.6.15-26-powerpc image and uname -r shows I am using 2.6.15-26-powerpc. Shouldn't I be  using the vmlinux-2.6.15-27-powerpc image? I reinstalled the linux-2.6.15-27-powerpc image from synaptic and  restarted, but I still am using 2.6.15-26-powerpc according  to uname -r. There is no vmlinux.old symlink. Was there  some  step of the  kernel update  that  is  not being  carried out or was left out? I presume I could create new symlinks with the correct references? What was the purpose of the last kernel update?

Thanks

---

