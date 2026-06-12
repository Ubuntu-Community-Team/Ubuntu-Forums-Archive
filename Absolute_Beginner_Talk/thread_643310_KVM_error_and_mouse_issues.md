---
title: "KVM error and mouse issues"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by bbirdy on 2007-12-17
Hello:

First post and hope I can find some help!!

Using this link:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

to setup KVM on my new Dell Latitude D630 I have it working with two
buggy issues:

1. I keep getting this error:

open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

when running this command:

bbird@m-1250:~$ kvm -no-acpi -m 384 -cdrom /dev/cdrom windows.img

to start my vm. However, it runs the vm anyway.

2. The mouse is not working in my vm. I have to tab around.

I've installed Windows XP Pro SP2 on the vm.

Can anyone comment on these problems? Your help is appreciated.

Bill

---

### Post by ewr2san on 2007-12-18
Usually this is caused by the kernel module not having been loaded..


Did the KVM kernel module load?
lsmod |grep kvm

You should see either kvm-intel or kvm-amd

If not then issue a:
sudo modprobe kvm-intel
or
sudo modprobe kvm-amd


You are probably aware of them, but there is an excelent guide at:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by learning curve on 2007-12-18
Just try a different mouse.  I had to swap out 2 before the 3rd one finally worked.

---

