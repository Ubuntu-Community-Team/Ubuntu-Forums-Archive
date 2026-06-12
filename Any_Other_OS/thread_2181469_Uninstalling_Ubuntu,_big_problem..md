---
title: "Uninstalling Ubuntu, big problem."
date: 2013-10-18
forum: Any Other OS
---

### Post by cAAseMe on 2013-10-18
So I decided to uninstall Ubuntu from my laptop, and ran into a big problem.

I booted Windows, and deleted the Linux partitions in Disk Management. However i then misread the directions from the guide i was using and restarted my computer instead of booting it with a Windows recovery CD.

So now it won't load either operating system, i get the following message:
"error: no such device: f1447306-db13-4931-b6e0-9761a8a7f4b6.
grub rescue>"

I know its completely idiotic what i've done. So is there any way to fix this?

Thanks.

---

### Post by Bucky Ball on 2013-10-18
You should have booted from a Ubuntu LiveCD and deleted the Ubuntu partitions with Gparted, but that's beside the point now. Windows does not even know what an EXT* partition is. 

Have no idea how to fix what you've done but you could try booting from the Windows recovery CD, which was instructed in the first place.

---

### Post by jeehyun on 2013-10-18
1. Reinstall ubuntu
2. Boot windows and install easybcd.
3. Recover mbr in easybcd - I don't remember exactly so you should search this. Easybcd free version may be available.
4. Delete ubuntu partition.

---

### Post by Andrew Bastin on 2013-10-30
Hello there,

Same problem happened to me last year.

I know the solution.

Step-1 :- Grab a Ubuntu live cd/usb and boot to ubuntu with it.
Step-2 :-Click on Try Ubuntu
Step-3 :- open terminal
Step-4 :- type "sudo apt-get install lilo" (without the quotes)
Step-4.5:- if step 4 fails then do "sudo apt-get update" (without the quotes) and then do step-4 again
Step-5:-type "sudo lilo -M /dev/sda mbr" (without the quotes)
Step-6:- Reboot the computer. And be Happy \\:D/

---

