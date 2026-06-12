---
title: "Booting problem....."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by micman.manoj on 2008-01-17
Hello!
  I m using a dual boot (Windows XP and Ubuntu 7.10). I had installed Ubuntu recently and everyhting was fine ,post installation,for few days .I even upgraded Ubuntu using the few Linux commands i knew.
Everything was fine,but,now at boot time (after selecting Ubuntu option),it takes up a lot of time .
There r few messages which get displayed ,like :
*Reading files needed to boot
*Setting preliminary keymap
*Preparing restricted drivers

and so on....
and it takes a lot of time and doesnt even login sometimes.Meanwhile,i have installed VMware server in Windows and had a copy of Ubuntu 7.10 installed thru it. and i m using it without satisfaction .I thank God tat even after all this my Grub loader hasnt crashed.
[COLOR="DarkOrange"]How to solve the boot problem?
My Vmware Ubuntu doesnt   mount the windows partitions automatically,how to resolve it?[/COLOR]

Thank You !!

---

### Post by kpkeerthi on 2008-01-17
Your virtualized ubuntu cannot see physical partitions for the very fact it is installed on a virtual disk (which is basically a file on your system). it can only see partitions on the virtual disk. You can however share folders between the host and the guest.

[http://www.howtogeek.com/howto/ubuntu/how-to-share-folders-with-your-ubuntu-virtual-machine-guest/](http://www.howtogeek.com/howto/ubuntu/how-to-share-folders-with-your-ubuntu-virtual-machine-guest/)

---

