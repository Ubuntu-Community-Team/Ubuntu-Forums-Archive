---
title: "had to recreate /boot, grub unworking"
date: 2011-04-09
forum: Apple Hardware Users
---

### Post by Harkins on 2011-04-09
I have a Macbook1,1 that triple-boots OS X, Windows, and Ubuntu 10.10, which has a /boot partition and an encrypted root partition. iPartition ran amok and deleted the /boot partition. I've used the LiveCD to recreate it and used aptitude to reinstall initramfs-*, grub-pc, and linux-kernel, but I can't boot.

rEFIt loads normally (it was never harmed) and displays the icons for my three OSs. If I choose Windows or either Linux (there are now two Linux icons instead of just the one I had previously) I get a blank black screen with a cursor blinking in the upper-left corner. Nothing ever loads.

I don't even know where to start trying to debug this, as I don't even get an error message I can work from. Can anyone make a suggestion for how to repair this? Did I miss an important step for recreating my /boot?

---

