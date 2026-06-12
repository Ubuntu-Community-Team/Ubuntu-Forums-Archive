---
title: "get busybox instead of booting (7.04)"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-09-21
Hi,
I've just installed ubuntu onto my windows vista machine and is the first time i have tried to dual boot. I get the initial ubuntu booting screen, however, the progress bar stays extremely small and it eventually ends up in busybox v1.13 telling me that:
*/bin/sh can't access tty, job control turned off*
anyone help?
cheers
Tom

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> Hi,
I've just installed ubuntu onto my windows vista machine and is the first time i have tried to dual boot. I get the initial ubuntu booting screen, however, the progress bar stays extremely small and it eventually ends up in busybox v1.13 telling me that:
*/bin/sh can't access tty, job control turned off*
anyone help?
cheers
Tom

Hi again, could you give us some specs on your system, also take a look at this thread.
[http://ubuntuforums.org/showthread.php?t=555763](http://ubuntuforums.org/showthread.php?t=555763)
The OP had the same issue and maybe it will help.

---

### Post by tommason on 2007-09-22
Hello again!,

My system specs are as follows:
abit quadgt mobo
C2D E6600
2Gb Ram
Gainward 8800GTS
76Gb Raptor (50Gb vista, 25Gb Ubuntu)
180Gb Seagate Barracuda

:)

---

### Post by tommason on 2007-09-22
bump

---

### Post by overdrank on 2007-09-22
> **tommason said:**
> bump

Hi did you try the methods described in the other thread I posted earlier?
Edit sorry you have it installed already, they same commands just edit the kernel on boot from the grub. When the grub is showing which kernel is booting then hit esc key and then select the kernel line and press e key and add those commands to the kernel. then hit b to boot hope this helps.

---

### Post by tommason on 2007-09-22
> **overdrank said:**
> Hi did you try the methods described in the other thread I posted earlier?
Edit sorry you have it installed already, they same commands just edit the kernel on boot from the grub. When the grub is showing which kernel is booting then hit esc key and then select the kernel line and press e key and add those commands to the kernel. then hit b to boot hope this helps.

**Adding 'break=top' to kernel**
f6 does nothing, although strangely, just after the choice of operating systems i pressed f6 and the progress bar lept up and ubuntu booted! it wasn't connected to the internet however (even though it does when i use the live cd)
This didn't work again though, same problem when i shut down. I think it may have been the same time when my bios boots it checks DMI POOL DATA and *i think * the time ubuntu booted it said 'update successful' where as usually it says nothing..... :S

When the Grub is showingwhich kernel is loading (what does this look like?)

---

### Post by overdrank on 2007-09-22
When the grub loads it will let you select between ubuntu and windows. It should be the first line loaded by default, press esp key then and it will bring you to the next window there the kernel should be the second line down. Navigate to it and press e to edit it and add the command.

---

### Post by tommason on 2007-09-22
ok will try that..
The DMI POOL DATA thing happened again!, before Grub loads, there is a line:
*Verfying DMI pool data.......*
it once again said:
 *update success*,
 whereas it usually just sits for a while and then Grub loads, 
this time ubuntu loaded correctly (albeit without network connections)

---

### Post by overdrank on 2007-09-22
> **tommason said:**
> ok will try that...it happened again, before Grub loads, there is a line:
*Verfying DMI pool data.......*
it once again said *update success*, whereas it usually just sits for a while and then Grub loads, this time ubuntu loaded correctly (albeit without network connections)

Ok so you are getting ubuntu to load to the desktop GUI?

---

### Post by tommason on 2007-09-22
yes, but only when it says the dmi pool data has updated successfully.....

---

### Post by tommason on 2007-09-22
much as i hate to do this, I'm giving up...what i first thought would be a days work to dual boot vista/ubuntu has now turned into 4 days of getting far too involved in the depths of computer trickery and has destroyed my vista install.... :( time to format and start again.
I'm going to wait until the next release of Ubuntu and try again..if this will solve any of the problems...
Thanks a lot for your time and help, I really appreaciate it :)
Tom

---

