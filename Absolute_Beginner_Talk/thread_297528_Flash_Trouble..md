---
title: "Flash Trouble."
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Neoito on 2006-11-11
I'm having some trouble getting flash to install.

The first time I did it from the download on the adobe website it seemed to install fine, however some (most) sites that are purley flash don't load.

When I try to do it through east Ubuntu I've been getting a message about borken packeages.

The option is now greyed out in easy Ubuntu so I can't even show you the message.

Any help on this would be greatly appriciated

---

### Post by Frak on 2006-11-11
Your aware that some computers have to download flash to the desktop and and extract all packages, open folder, click on install, then click run in terminal, right?
For some reason mine doesn't install from the missing plugins box.

---

### Post by kvonb on 2006-11-11
I had the same problems, this is how I fixed it:

1) Download and install FirefoxII (if you don't already have it)-
Download the script from here: [http://www.psychocats.net/ubuntu/installnewfirefox.sh](http://www.psychocats.net/ubuntu/installnewfirefox.sh)

2) Make the script executable, open a terminal, change to the folder where you downloaded the scrip to, then type:
chmod +x installnewfirefox.sh
./installnewfirefox.sh

Go through the questions and complete the install.

3) Download and install Flash9 beta-
In the same teminal copy and paste the following:
wget [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb)

When it has finished downloading, type this:

dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb

Close and re-open Firefox, all should be well.

Regards, Kev :)

---

### Post by Minyaliel on 2006-11-11
Just a note: the tuxfamily repo doesn't seem to work at the moment, at least it gave me a 404 error message...

---

