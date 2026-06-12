---
title: "A Few Simple VMWARE questions"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by 71CH on 2007-05-01
Hey all
I currently have vmware configured with 10 gigs in the partition. Can I increase and decrease this? I have the same question for RAM as well. Also, do I need to shut down XP everytime I'm done with vmware or can I just shut down vmware. Lastly, is the RAM that I allocated to vmware only used when vmware is open or do I pretty much lose that RAM even when I don't have vmware open. Thanks guys. :P

---

### Post by Cypher on 2007-05-01
These questions aren't exactly Ubuntu or Linux related, I think you might have much better luck with a VMware forum?

---

### Post by LaurelLynn on 2007-05-01
Dear 71CH,

I'm not sure, since I use Qemu instead. With that I would make a backup copy (very important).

Then I would  try appendiing any large file to the end.  Boot with the image and an iso image of the Live CD
as the cdrom and use Gparted to resize the partition.  It should see the drive as being the size of file,
and any extra garbage on the end as just free space.

$  cat  original.qemu   somethingbig  > bigger.qemu

Should work in VMWare too, since the partitioning is done completely within the virtual machine.

---

### Post by veloce on 2007-05-03
> **71CH said:**
> Hey all
I currently have vmware configured with 10 gigs in the partition. Can I increase and decrease this? I have the same question for RAM as well. Also, do I need to shut down XP everytime I'm done with vmware or can I just shut down vmware. Lastly, is the RAM that I allocated to vmware only used when vmware is open or do I pretty much lose that RAM even when I don't have vmware open. Thanks guys. :P

I am assuming that you are running a winxp virtual machine under vmware server running on ubuntu.

1. You cannot change the size of a virtual machine's virtual disk.
2. You can change the RAM allocated to a vm in the vmware server console - the virtual machine must be off.
3. If you shut down vmware console, your virtual machine is still running.  You are best to at least "pause" your vm.
4. Ubuntu manages the RAM for your vms dynamically.  Seldom is all the ram allocated to your vm in use.  (This is in stark contrast to memory management by an xp host for vms - it's horrible). When the vm is not in use it will probably be swapped out of physical memory.

---

