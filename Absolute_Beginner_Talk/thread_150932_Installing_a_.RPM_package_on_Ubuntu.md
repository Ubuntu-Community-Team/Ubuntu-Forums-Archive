---
title: "Installing a .RPM package on Ubuntu"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-03-27
How will I be able to do this. I am trying to install Crossover.Office.Pro-3.0.0. And I am using the sudo and su commands to try and install it but I keep gettin this message prompt saying, you must logged in as root or use "su" rather than "sudo". I don't know what to do. I did already. And I tried logging in as root using the su- command.

---

### Post by Sef on 2006-03-27
To install RPM, you need to convert it to deb.  Copy and paste this link on how to do that.


[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

From Psychocats.net

3. Manual installation of a .rpm
Occasionally, for a program, you're just not able to find a .deb. There may seem to be, however, a plethora of .rpm files for the program. If you must use an .rpm (not native to Debian-based distros), then use an .rpm. It's a very similar procedure to the .deb one described above, just using a different command (one that converts the "alien" format of .rpm):

One-time deal, just to get alien:

sudo apt-get update
sudo apt-get install alien

Now you can actually use alien:

cd Desktop
sudo alien -i opera-8.50-20050916.5-shared-qt.i386-en.rpm

Again, no dependencies will be resolved.

---

### Post by Reggaeton King on 2006-03-27
Thanks a lot man!

---

### Post by Perfect Storm on 2006-03-27
Any reason why using Crossover Pro 3 when Crossover 5 is out there. On Crossweavers homepage, when you login and choose my downloads there's .deb file.

---

