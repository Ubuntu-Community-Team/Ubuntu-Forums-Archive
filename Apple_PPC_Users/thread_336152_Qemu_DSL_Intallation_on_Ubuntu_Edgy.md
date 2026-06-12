---
title: "Qemu DSL Intallation on Ubuntu Edgy"
date: 2007-01-11
forum: Apple PPC Users
---

### Post by prb on 2007-01-11
I'm trying to install a DSL instance of linux and launch it with QEMU.
I can launch with a CD, but I plan to use this to watch flash movies so I want to configure it
once and store it on a qemu image.  So here's my process:
qemu-img create -f qcow dsl.img 250M
Great works.   
I boot onto the CD using this command:
qemu -cdrom /media/cdrom0/dsl-3.1.iso -boot d dsl.img
Great.  Up comes DSL linux.  
Then as per instructions here:
[http://www.damnsmalllinux.org/dsl-hd-install.html](http://www.damnsmalllinux.org/dsl-hd-install.html)
I type : sudo -u root dsl-hdinstall
It then asks for a target partition.  
My question is: what to I enter here?  I want to install this linux onto the emulated hard drive from qemu, but how do I enter this from within the linux install sequence within qemu?
:rolleyes:

---

### Post by prb on 2007-01-12
This was an arcane question that didn't really deserve a response.
More to the point, I've been struggling for a couple days for some kind of hack workaround to show flash movies in PPC firefox 2.0.  I've got that ghetto open source flash player that only renders flash 4, with static noise.
Is there any hope for accomplishing this in edgy?  I feel like someone must have gotten some sort of work-around.
My little experiment with qemu ended with a thud.  Too slow and too flaky.
cheers

---

### Post by ssam on 2007-01-12
for the original question, it would probably be /dev/hda

for flash, you might want to look at gnash, there are a few threads in this forum if you search.

---

### Post by 3rdalbum on 2007-01-13
The command you should have put for Qemu is:

qemu -cdrom /media/cdrom0/dsl-3.1.iso -boot d -hda dsl.img

Then you could specify /dev/hda as the target drive for the DSL installation.

There is such a thing as Qemu User-mode Emulation - according to popular belief, it lets you run x86 programs on PPC without the overhead of emulating an entire operating system. The reason why I say "according to popular belief" is that I haven't yet met anyone who's done it!

If you start experimenting with it, and you get this working (with a set of instructions about how to accomplish it), please pretty please send me the instructions, because I want this as a feature for [Copland]("http://code.google.com/p/coplandppc/wiki/MainPage") 1.0

---

