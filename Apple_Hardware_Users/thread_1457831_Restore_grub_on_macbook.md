---
title: "Restore grub on macbook"
date: 2010-04-19
forum: Apple Hardware Users
---

### Post by DARKAD on 2010-04-19
On my macbook 4.1 I had Mac OSX and ubuntustudio 9.10 64bit.
Everything worked well with ubuntustudio before.
I reinstalled macos x with refit 0.14 and I synchronized the partitions with the refit tool. 
I still can see the previous ubuntu partitions with the boot label on /dev/sda3.

If I boot with the alt(option) key pressed, it says "Missing operating system".

I'm trying this: [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

So I booted with ubuntustudio install cd chosing the option for rescue damaged system and chosing to enter as root on the / (root partition):

I'm trying "METHOD 3 - CHROOT" from: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

chroot:
bin/sh not found

---

