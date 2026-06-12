---
title: "mysql-common error when installing Breezy Badger"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by mystrim on 2006-04-15
Hello,

This is my first time installing Ubuntu - I normally use the Live CD.  I downloaded the ISO labelled Ubuntu 5.10 Install CD.  It seems that my installation is stuck in a loop during the Ubuntu Configuration. Once the installation looks like it is at 100%, it restarts GDM and appears to start the installation over.  If I switch to the fourth console, I can see errors complaining about dependency conflicts between mysql-common and mysql-common-4.1.  One dependency message (the one for mysql-common) says Ubuntu 4.1.12 is installed, The other message (for mysql-common-4.1) says Ubuntu 4.0.24 is to be installed.  I'm very, very confused.

Another confusing thing is I tried using apt-get to remove mysql-common-4.1 and to install mysql-common, which got me through the configuration (although it still restarts at the end, after restarting gdm), but then now when I switch to console 7 the desktop changed from regular Ubuntu wallpaper to edubuntu wallpaper.

Please help!

Thanks,

Tim

---

### Post by Bloch on 2006-04-15
Are you sure you aare doing a clean install? Where is that edubuntu wallpaper coming from? It's not in standard ubuntu AFAIK.

Try from the beginning again, making sure you choose the correct option when it  askes where you want to intall it. You shouldn't be having dependency problems during an installation.

---

