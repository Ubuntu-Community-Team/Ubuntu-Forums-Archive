---
title: "How to format/wipe hard drive?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by whoa_551 on 2006-05-27
Can anyone post a link(s) for a good step-by-step guide(s) for wiping a hdd clean and installing a new os from scratch?

---

### Post by mostwanted on 2006-05-27
1) Insert OS installer disc (Ubuntu or XP for example).

2) Install.

The installer should be capable of wiping out the harddisk itself.

---

### Post by AndyCooll on 2006-05-27
If that OS is Ubuntu then you just need to install the CD, follow the instructions and when it comes to the partitioning bit select a manual setup.

For formatting, there's an excellent website listed in my signature, "HOWTO dual boot" The website actually contains much more than just details about dual-booting.

:cool:

---

### Post by whoa_551 on 2006-05-27
I guess what I'm looking for is something that describes how to setup a cd-rom and floppy drive after a complete format (which might make those drives inaccessable) so one can then install a new os (like FreeDOS, linux, etc.)

---

### Post by SDREnate on 2006-05-27
[QUOTE=whoa_551]I guess what I'm looking for is something that describes how to setup a cd-rom and floppy drive after a complete format (which might make those drives inaccessable) so one can then install a new os (like FreeDOS, linux, etc.)[/QUOTE]You set up cdrom and floppy drives through BIOS, which is completely seperate from your hard drive.

---

### Post by lumpki on 2006-05-27
The cdrom and floppy drives are accessible even if there is no hard drive on the computer. So don't worry, just insert your installation cd and reboot. As long as your system can boot from the cdrom drive (see below), you can always install a new operating system regardless of what's on the hard drive.

With Ubuntu, the installation is quick and easy, just follow the prompts. When you get to the partitioning step, selecting "use entire disk" will reformat the entire drive. Since you are wiping out everthing and starting over fresh, there's no concern about messing anything up. 

One thing you might want to set up is the "boot order" or "boot sequence" in the system BIOS. There is a basic system setup utility that appears if you press the proper key when the system is booting. The key to press might be ins, del, F1, F2, F10... depending on your machine. It's usually a text-based utility but there is on-screen help and hints. Look around in the menus for the proper option. The cdrom and floppy drives should appear before the hard drive in the boot order.

Another common problem: When you're downloading and burning a boot cd, make sure you use the "burn cd image" or "burn ISO image" option. The disc won't boot if you simply make a data disc containing the iso file.

Good luck!

---

