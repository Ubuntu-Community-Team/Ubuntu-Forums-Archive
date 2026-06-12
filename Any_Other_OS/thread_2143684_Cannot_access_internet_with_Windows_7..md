---
title: "Cannot access internet with Windows 7."
date: 2013-05-09
forum: Any Other OS
---

### Post by NBPX on 2013-05-09
A desktop with ethernet and a laptop with ethernet and/or wi-fi.

I cannot access internet on Windows 7 on both, but with Ubuntu 13.04 I can. 

I already rebooted and reseted the modem/router, a D-link DSL2640B, but without solution.

It happend some time after install a HP wireless printer using Windows, but I think it's not related.

I can ping to 8.8.8.8 and sometimes appears a yellow triangle on ethernet connection icon.

---

### Post by gnusci on 2013-05-09
WinSeven why in this earth this is a post in the Ubuntu forums????

---

### Post by Sam Mills on 2013-05-09
> **gnusci said:**
> WinSeven why in this earth this is a post in the Ubuntu forums????
Because it's in "**Other OS**/Distro Support". That includes windows.

---

### Post by Sam Mills on 2013-05-09
Just for the heck of it, uninstall the printer and reboot.

---

### Post by nsync on 2013-05-11
try reporting it to microsoft forums they would actually fix your problem more quick,

---

### Post by mips on 2013-05-11
> **gnusci said:**
> WinSeven why in this earth this is a post in the Ubuntu forums????

The sub forum is called "**Other OS/Distro Support**" in case you have failed to notice. So he's free to ask questions about any distro or OS under the sun.

NBPX,

Open a dos prompt/terminal Run-->cmd and post the output of the following command **ipconfig /all**

---

### Post by QIII on 2013-05-11
Furthermore...

Since it appears the OP is dual booting, it's a fair question here.  So let's keep it civil and either help solve the issue or not.

Fair enough?

Thanks, everyone.

---

### Post by Erik1984 on 2013-05-11
You could try to revert to the most recent restore point or a restore point before that. I used to have the same problem on a Windows 7 desktop and using restore points worked (untill the good restore points were gone). Maybe it's also a good idea to change the update settings to ask you for permissions (if they are set to automatically install now). That way you can read the update descriptions and Google the codes to see if they caused network trouble for other users.

---

### Post by NBPX on 2013-05-11
> **Sam Mills said:**
> Because it's in "**Other OS**/Distro Support". That includes windows.

Exactly! And also to show that Windows can be a pain in the ass in some situations and Ubuntu not. :o

I've tried graphical ui and command line to solve the problem, but until now I have no solution.

Anyway it's related to Ubuntu in some way, because Ubuntu is working...

> **Sam Mills said:**
> Just for the heck of it, uninstall the printer and reboot.

Not solved.

> **Euroman said:**
> You could try to revert to the most recent restore point or a restore point before that. I used to have the same problem on a Windows 7 desktop and using restore points worked (untill the good restore points were gone). Maybe it's also a good idea to change the update settings to ask you for permissions (if they are set to automatically install now). That way you can read the update descriptions and Google the codes to see if they caused network trouble for other users.

I will try to restore.


Another detail. I can access internet with Windows via access point. The access point is connected with the modem/router via cable. I Cannot access internet connected directly to the modem/router. A great problem here is that the desktop has not wi-fi, so it cannot use the access point.


Ps.: No restore point avaiable.

---

### Post by NBPX on 2013-05-12
Solved!

Cause: Outdated version of the Comodo firewall.

Solution: Remove the firewall and install a newer version.

---

### Post by Rukiri on 2013-05-12
Post this in the seven or eight forums, but sounds like a driver issue, does it work in Linux? If it does download the latest driver from the Linux host and install it on windows and it should work.  Have you also just tried reinstalling windows?

---

