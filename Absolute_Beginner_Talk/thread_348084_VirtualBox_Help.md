---
title: "VirtualBox Help"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-28
Hi,

Yesterday, I downloaded and installed VirtualBox and managed to install a copy of Windows XP within it.  It all worked wonderfully well.  However, when I try to launch Windows XP via VirtualBox I get the following error message in the screen where Windows should have loaded...

      "FATAL: Could not read from the boot medium! System halted."

The only way I can launch the operating system is to keep the Windows disc in the CD reader all the time...  It boots fine this way.  Is this meant to be the case when using software like VirtualBox or VMware or is there another method I can use without the need to keep the Windows disc in the tray all the time?

---

### Post by MkfIbK7a on 2007-01-28
hmm im guessing from the error (because i have no experience whatsoever with virtual machines) that it boots from the cd because if you actually installed windows it would take up all of your harddrive space 

correct me if im wrong

wert

---

### Post by Norfolk 'n' Good on 2007-01-28
When setting up VirtualBox I was presented with an option to create hard-drive space, either dynamic or fixed.  I chose the fixed option.  Because I have dedicated 100 GB of HD (160 GB HD is partitioned) to Ubuntu - clearly more than I need - I allowed 50 GB for the XP installation in VirtualBox.  I would have guessed that was more than enough space.

---

### Post by MkfIbK7a on 2007-01-28
hmmm

i dont know maybe after booting widows remove the cd and see what happens?

---

### Post by Norfolk 'n' Good on 2007-01-28
Most of the files necessary for Windows are installed on the virtual machine.  I have also installed Office and a number of other programs.  Removing the CD from the tray after booting does not effect anything.

---

### Post by MkfIbK7a on 2007-01-28
so it continues to run?

if so then just do that everytime!:D

---

### Post by Karl S. on 2007-01-28
Total beginner, so not sure how helpful this is, but you might want to start over. I created a disk image from my Windows install disk, put that on my Ubuntu desktop, and pointed VirtualBox to that. You do get some desktop clutter--so you might want to put the image someplace else--but at least you don't have to have the CD in your computer all the time.

---

### Post by L14UX_1NS1D3 on 2007-02-04
I have another solution that would wield the same results as Karl suggested.

1. Create a iso image.
2. Create a mount point for the iso image or use the cdrom0 or something like that.
3.execute the command :
[B]
~$sudo mount /dir/image.iso -o loop /media/cdrom[/B]

doing that will mount the iso file-system as if it were a mounted cd thus enabling you to direct virtualbox to mount the cdrom0

to unmount the image type: 

**~$sudo umount  /dev/cdrom0** or the designated mount-point 

HOPE THIS HELPS!

---

