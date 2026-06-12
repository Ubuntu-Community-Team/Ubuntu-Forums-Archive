---
title: "VMWare / Equivalent"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Tarquin on 2007-05-19
Hello there.

Basically Im looking to find out if theres some kind of other virtual machine other than VMWare I could use.
I cannot install VMare as I always get the same error message:
> 
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

And for some reason 2 different partition editor type things cannot make me a new partition to run Windows on.
I wouldnt be bothered about Windows if I didnt need my MP3 player (Sony - ie have to use stupid Sonicstage) and one or two other things.

I have also tried to install various things using Wine, but to be honest I dont have that much of an idea what Im doing when I do, so nothing ever works!

Many thanks in advance for any help!! Tarquin

---

### Post by Najand on 2007-05-19
Try to put "sudo" command before the command you used for installation.

---

### Post by Tarquin on 2007-05-19
I havent actually tried it without using sudo.
I have tried so many times with a few small variants while installing, thats why I was wondering if theres another program I could use.

---

### Post by Marsolin on 2007-05-19
[VirtualBox]("http://linuxappfinder.com/package/virtualbox") is one option. [QEMU]("http://linuxappfinder.com/package/qemu") and [KVM]("http://linuxappfinder.com/package/kvm") are other options. On their own they don't have a GUI, but programs like [Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher") or [Qemuctl]("http://linuxappfinder.com/package/qemuctl") can be used be used with them.

---

