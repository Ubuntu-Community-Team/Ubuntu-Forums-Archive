---
title: "Uninstall java by deleting directory?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-08-07
I want to uninstall java, and reinstall into a different directory location.

If this were a Windows situation, MS would have put garbage all over my machine making cleanup impossible. 

Since this is Ubuntu, can I simply delete the java directory and re-do the install?

---

### Post by steve.horsley on 2007-08-07
That depends on how you installed the java in the first place. Just reverse the installation process. 

Actually, I just install java in /opt and put symlinks to it in /usr/local/bin, and ignore the original java that comnes with Ubuntu.

---

### Post by brent113 on 2007-08-07
You can't quite delete the directory as linux still has references that need to be cleaned up.  Open Synaptic (System->Administration) and search for java.  You can right click on it and do a Complete Removal.  If you didn't install java from a deb file or from synaptic, do that next time.

---

### Post by bettyhills on 2007-08-07
I believe that I just installed java to its own directory and created a link, but am not smart enough in Ubuntu to know for sure.  (Jre6 for Amd64 is not available in Synaptic so I did not think I could use Synaptic.)  I am also not smart enough to know how to reverse the steps.

Can you read through what I did (below) to see if indeed it is in its own /java directory?

If so, can I just delete the directory and start over?

I downloaded Jre6 from java.com. Then instructions said to ...
4) Run Installer
From the Terminal, enter these commands: 
$ cd apps/java
$ ls -l
$ chmod +x jre*.bin
$ ./jre*.bin
$ ln -s jre*/bin bin

The chmod command makes the file executable so you can run it. The ln command creates a symbolic link to the bin folder so it's easier to access.

5) Add Java to Your PATH
While still in the Terminal, enter these commands: 
$ cd ~
$ echo 'PATH=~/bin:$PATH' >> .gnomerc
$ cat .gnomerc
$ mkdir bin
$ cd bin
$ ln -s ~/apps/java/bin/java java

The echo command tells the GNOME desktop startup script to add your bin folder to the PATH. The cat command displays the startup script so you can verify your update. If the mkdir command reports that the folder already exists, that's ok.

6) Log Back On
Because the PATH variable is set on startup, you need to log out and then log back in for the Java installation to be complete.

---

### Post by steve.horsley on 2007-08-08
From those instructions to install, I think the removel procedure would be:

1) Edit ~/.gnomerc and remove the last line (should start with "PATH=").
Do this with the gedit editor - this is the command:
**gedit .gnomerc**
But in fact I haven't got a .gnomerc file, so yours probably only has that one line, in which case you can just delete the file instead:
**rm .gnomerc**

2) Delete the apps/java/bin directory where java was installed:
**rm -rf apps/java/bin**

3) delete the installer file that you downloaded if you want

---

