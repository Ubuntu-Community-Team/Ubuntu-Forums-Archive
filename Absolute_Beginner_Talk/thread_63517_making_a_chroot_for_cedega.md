---
title: "making a chroot for cedega"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by cacophony on 2005-09-08
I don't know what section this goes in but oh well.

I've got hoary a64.
i used the
dpkg -i `name -find <cedega package>` 

Says it I386 which obviously is'nt compatible with my linux obviously.
I was wondering on creating a chroot for it, but i don't know how to do it.
Anyone know how to make one so i can get it setup.

Or i could just use the x86 version of ubuntu.

---

### Post by LinuxGuy1234 on 2007-12-16
> **cacophony said:**
> I don't know what section this goes in but oh well.

I've got hoary a64.
i used the
dpkg -i `name -find <cedega package>` 

Says it I386 which obviously is'nt compatible with my linux obviously.
I was wondering on creating a chroot for it, but i don't know how to do it.
Anyone know how to make one so i can get it setup.

Or i could just use the x86 version of ubuntu.

You can create a chroot for Cedaga.
```
sudo apt-get install debootstrap
sudo mkdir /i368chroot
sudo debootstrap --arch i386 hoary /i368chroot http://us.archive.ubuntu.com/ubuntu/
sudo chroot /i368chroot
```

Now install Cedaga.

---

