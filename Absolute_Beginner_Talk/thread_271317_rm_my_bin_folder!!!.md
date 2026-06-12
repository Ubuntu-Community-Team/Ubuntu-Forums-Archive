---
title: "rm my bin folder!!!"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Bizmac on 2006-10-04
I was doing some tests and I delete all my usr/bin folder!!!
Do you know how to restore a system without bin?

No apt-get, sudo anymore!!!
Do I need to reboot, and afte what do I need to do?

Thank you

---

### Post by whizbaby on 2006-10-04
Start from liveCD and copy the /usr/bin folder of that to your hard drive, this will give you the necessary commands to rebuild the rest.

---

### Post by jorn on 2006-10-04
Have you deleted them using sudo? Have you looked in /root/.Trash?

---

### Post by Bizmac on 2006-10-04
I properly deleted them without keeping them in Trash.
I will try to boot from the live cd and copy the bin folder (whizbaby)!

Thank you

---

### Post by Bizmac on 2006-10-04
Big problem, I restore the bin folder and I was able to logon in Kubuntu but in command line only!!!

Do you know how to start X or uninstall X to reinstall it.
I try apt-get upgrade, update, install, Kubuntu claims that all my files are updated!

---

### Post by whizbaby on 2006-10-04
to start x
sudo /etc/init.d/gdm start

---

### Post by whizbaby on 2006-10-04
BTW did you verify if you copied it right (contents of liveCD /usr/bin are now on the HD/user/bin)?

Files from the CD are naturally older versions than those from the net, so updating should do no harm.

---

### Post by lamego on 2006-10-04
Copying the /usr/bin from the CD will not restore all the binaries from other packages which are not used on the Live CD. Your best option is to reinstall the system.

---

### Post by Bizmac on 2006-10-04
Thank you all :) ,
I will try and let you know...

Thanks again!!!

---

