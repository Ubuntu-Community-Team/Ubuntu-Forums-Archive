---
title: "dual core?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by syedn on 2006-07-26
How would I check to make sure both my processors are being used?

I'm running dapper on an amd x2 3800.

thanks!

---

### Post by scxtt on 2006-07-26
you should have 2 CPUs listed in the system monitor "Resources" tab ...

System --> Administration --> System Monitor

or type gnome-system-monitor into a terminal ...

typing **top** into a terminal should also show you info for each processor ...

---

### Post by daniel of sarnia on 2006-07-26
In kde info center will show you cpu 0 and cpu 1. I'm not sure what it is in gnome. If you have the 686 or 686 smp linux kernel installed they should both be running

---

### Post by syedn on 2006-07-26
hmm, it only lists one under the system monitor > resources.

so i'm guessing i need a different kernel image then?

I think 2.6.15-26-386 PREEMPT is what i have.

Do I need to update it to something else?

Thanks for the help!

---

### Post by trent dillman on 2006-07-26
install the 686 smp kernel, then
```
cat /proc/cpuinfo
```

---

### Post by syedn on 2006-07-26
Thanks guys!  Successfully have both cores supported now :)

One more question: when I boot up it lists 3 different kernels (the 686-smp, and then two of the same 386) how would i get rid of the 2 older ones? or should i not do that?

thanks again!

---

### Post by scxtt on 2006-07-26
if you're not pressed for HDD space, it's fine to leave them there (in the /boot directory) ... if you don't want them listed in grub on boot, edit /boot/grub/menu.lst and remove their entries ...

---

### Post by moma on 2006-07-26
**Keep always one stable kernel (normally the current you run) + at least one OLD kernel as reserve.**

This is howto remove old, obsolete kernels from the system.

0) Check what is your current, running kernel
$ [COLOR="Green"]uname -r [/COLOR]

1) List installed kernels
$ [COLOR="Green"]dpkg -l "linux-image*" | grep ii[/COLOR]

Sample output (make the terminal window wide enough so the kernel name becomes visible):
[FONT="Courier New"][SIZE="2"]ii  linux-image-2.6.15-18-386 2.6.15-18.27   Linux kernel image for version 2.6.15 on 386
ii  linux-image-2.6.15-23-386 2.6.15-23.39   Linux kernel image for version 2.6.15 on 386
ii  linux-image-2.6.15-23-k7  2.6.15-23.39   Linux kernel image for version 2.6.15 on AMD
ii  linux-image-2.6.15-25-386 2.6.15-25.43   Linux kernel image for version 2.6.15 on 386
ii  linux-image-2.6.15-26-k7  2.6.15-26.45   Linux kernel image for version 2.6.15 on AMD
ii  linux-image-2.6.16.19-686 custom.1.0     Linux kernel binary image for version 2.6.16[/SIZE][/FONT]

or do:
$ [COLOR="Green"]dpkg --get-selections | grep linux-image[/COLOR]

2) Remove old kernels 
$ [COLOR="Green"]sudo apt-get remove --purge linux-image-2.6.15-X-Y[/COLOR]

Replace linux-image-2.6.15-X-Y with correct kernel name.

Remove command will also edit /boot/grub/menu.lst. If you have GRUB installed on another disk/partition you may have to edit the menu.lst manually.

Note: [COLOR="Blue"]Synaptic Package Manager[/COLOR] can also do the "remove" job.

// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by syedn on 2006-07-26
Thanks guys!

I decided to just leave them be for now, as is, I only have 3 kernels listed (the current 686 smp, the 386, and the generic one).

Everythings running much quicker though, thanks again!

---

