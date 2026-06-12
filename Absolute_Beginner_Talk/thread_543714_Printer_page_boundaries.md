---
title: "Printer page boundaries"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by d2843 on 2007-09-05
I am running Ubuntu Feisty trying to print with an HP Deskjet D1420. I can find no way to set the print boundaries, so the printer cuts off the edges of whatever I'm printing. The contents of the page are also shifted down and slightly to the right.

---

### Post by LowSky on 2007-09-05
do you have the correct driver installed?

what are you trying to print? I know Openoffice does have a page setup under the file menu

---

### Post by d2843 on 2007-09-05
I'm using hpijs. There aren't very many settings available. My printer has been cutting the edges off everything I've been printing.

---

### Post by aws910 on 2007-10-15
I'm getting this same problem too.  Here's my env:

*Ubuntu 7.04 with all updates

*Printer is HP Laserjet 1200, installed on winXP and shared over SMB(direct connection not possible)

*Drivers - I've tried all the ones that system->administration->printers allows me to do: postscript, pxlmono, hpijs, gutenprint-cups

*I even tried [this hak]("https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/25105") and it didn't change anything.

...and no matter what I do, it cuts off the bottom of the page.  The paper size was A4 by default so I changed it to Letter(which is what we use) and it got a little worse!  I've googled it up and down and haven't been able to find a solution.  A lot of people have this issue with other printers but the threads never reveal the solution.  I would be inclined to say "It's not a driver issue" but I'm still pretty new to all this.  Can anyone help me here?

---

### Post by aws910 on 2007-10-19
Fresh-installed to 7.10 Gutsy and the problem was corrected.

---

