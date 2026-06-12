---
title: "Restart after &quot;Starting up...&quot; is displayed on boot."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by nimalan on 2007-02-20
Hi

I installed the server version of Edgy onto my old computer after wiping the harddrive. I can boot into it from the cd, but when booting from the harddrive, it gets to "Starting up..." and then reboots the machine.

I have used grub to look at the syslog and boot log files, but there is nothing in them.

Is there anyway of increasing the logging on bootup to narrow down the problem?

Any other suggestions would be gratefully received.

Thanks Nim

---

### Post by n8bounds on 2007-02-21
when grub loads, hit esc to see the menu and then hit the E key, go down to the second line and hit E again...take out the QUIET SPLASH part and then hit ENTER then hit B...i think.....

---

### Post by jpflathead on 2007-02-23
I have the same problem. CPU is a VIA C3. server is UBUNTU 6.10
when installing from cd press F8 and it says for VIA-based machines add pci=noacpi to the boot line:
boot: install pci=noacpi
but I don't get a boot: line.
So I tried putting it behind the boot command in the GRUB boot menu
And nothing works.
It seems 6.10 is not working on VIA cpu's as more people have problems with it.

---

### Post by confused57 on 2007-02-23
You might be able to install a server using the alternate cd(select "Command Line" install):
[http://www.ubuntuforums.org/showthread.php?t=290903&page=2](http://www.ubuntuforums.org/showthread.php?t=290903&page=2)

---

