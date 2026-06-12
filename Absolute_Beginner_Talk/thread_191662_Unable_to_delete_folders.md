---
title: "Unable to delete folders"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by IcyStorm on 2006-06-07
I'm a first time Linux user and I was trying to install Xmms and Captive (to access my other NTFS partitions). My friend told me I can convert .rpm files to .deb by installing Alien (through Package Manager) and then using the terminal.

I entered cd Desktop, and then sudo alien --to-deb packagefilename.rpm

However, all it does is create the folder on my desktop, and I cannot delete them or move them.

Error while moving.

Cannot move "/home/jason...tactic-1.1.7" to the trash because you do not have permissions to change it or its parent folder.

It gives the option to Cancel or Retry. I rebooted to see if it changed, but I still can't delete them. How do I delete them, and also, how do I properly convert .rpm to .deb?

---

### Post by maruchan on 2006-06-07
You invoked super-user priveleges to create that folder using Alien (sudo alien). Therefore, to delete the folder you will need super-user priveleges. You can run "gksudo nautilus" (gksudo is like sudo) and delete the folder from there, that should work. Just be sure to close that Nautilus window when you're done so you don't accidentally do something insanely bad.

---

### Post by Nequeo on 2006-06-07
Because you used 'sudo', to create the .deb package, those folders are owned by 'Root'. If you're comfortable with the command line, use 'sudo rm -r /home/jason/thefolder' to delete it. 

Otherwise, you'll need to type 'gksu nautilus &' on the command line, to get a file browser running as root, which you can then use to delete the folder.

Or you could even do a 'sudo chown -R jason:jason /home/jason/thefolder' from the command line to change the folder's owner back to yourself. Then delete it normally. 

Cheers,

---

### Post by catlett on 2006-06-07
I haven't run alien in a while but if my memory serves me you don't write in "to deb" you jusat enter alien,.
Unless I'm forgetting you would do it like this ```
sudo alien Xmms-1.51-i386.rpm
``` Then you would install the resulting deb with dpkg -i (debian package install) so then you would run ```
sudo dpkg -i Xmms-1.51-i386.deb
``` Just remember to cd to where the packages are.

P.S. The Xmms-1.51.i386.rpm is just for example, I find it easier to grasp when using something that looks like a file rather than "rpm package you want to convert" type of example

---

### Post by IcyStorm on 2006-06-08
Thanks for answering everyone. I managed to delete the folders with your instructions. I also installed Xmms through Package Manager, because the sudo alien thing just wouldn't work. It created a folder (that I still had to delete using the gksu nautilus command) and wouldn't create a .deb.

---

