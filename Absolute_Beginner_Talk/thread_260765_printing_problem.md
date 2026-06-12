---
title: "printing problem"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-09-19
i have an HP deskjet 710 here at my home, and i've had it installed and working here on ubuntu.

the problem is that everytime it prints, about an inch at the bottom of the page gets "cut off" (page numbers, margins, etc... below). i've checked the paper size and all in the print setup, but a portion is still cut off.

anyone knows how to solve this or had similar problems?

thanks for the help!

---

### Post by whizbaby on 2006-09-19
Have you tried from the cups-webfrontend? If not
sudo adduser cupsys shadow
/etc/init.d/cupsys restart
open firefox and type in adress bar
localhost:631

---

