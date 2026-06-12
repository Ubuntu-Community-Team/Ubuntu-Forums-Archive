---
title: "Azureus crashes"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by turtlecloud on 2007-06-22
every time I start up azureus it shows the main window for like a second and then it just dissappears. How do i fix this? I did this before by like doing the remove the log saves but then now it won't work. This occurs like every few days..Does anyone have a solution?

---

### Post by turtlecloud on 2007-06-22
when i type azureus in the terminal it gives
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb485e172, pid=7804, tid=3084786576
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid7804.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by NeoLithium on 2007-06-22
Well, you can try a couple of things.

1) Go into your /home/USERNAME/.azureus folder and delete all the logs
2) Double check that your computer is still using sun java as an option with this command in terminal:  **sudo update-alternatives --config java**

Hope this helps! :)

---

### Post by turtlecloud on 2007-06-22
thanks. The second option worked. I switched it to 
 /usr/bin/gij-wrapper-4.1
and then azureus worked. Thanks alot

---

### Post by jb3nny on 2007-06-23
yes the wrapper one works for me as well.. thanks!

---

### Post by maxim1 on 2007-06-23
Thanks for theinfo sorted me out a treat NeoLithium

---

### Post by Macros42 on 2007-06-23
This is a [known bug](https://bugs.launchpad.net/ubuntu/feisty/+source/azureus/+bug/68020). Problem with using gcj is that it uses a lot more resources to run it. And on that thread some people have reported random crashes then using gcj. A better fix seems to be to download the vanilla installation from azureus.sourceforge.net and it works perfectly with the sun jre.

---

### Post by Buendia on 2007-06-24
The problem with the wrapper is that it causes DHT firewalling, any idea why azureus doesn't work with sun java? Is it a 64 bit problem?

---

### Post by pimlottc on 2007-06-24
The problem happens when Azureus detects an improper shutdown (or other error) and tries to notify you with that "slide-in" dialog box that appears in the lower-right hand corner.  For some reason, this causes a crash when using sun Java (either 5 or 6) with the Fiesty shipped version.

This is why removing the log directories works (Azureus uses them to determine if it was shutdown properly).

A permanent solution is to update Azureus, there's a new revision recently uploaded to feisty-proposed: [http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

Alternatively, you can directly replace your systems Azureus jar with one from the upstream (if you know what you're doing).

More discussion at the launchpad bug entry: [https://bugs.launchpad.net/ubuntu/feisty/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/feisty/+source/azureus/+bug/68020)

---

### Post by drably on 2007-06-26
I downloaded the latest version from [http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270)
- **Azureus_2.5.0.4_linux.tar.bz2**

extracted it to **/.azureus**
opened the main config shell script file that starts the program
and edited the below
```
######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR=""				# use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
#PROGRAM_DIR="/home/username/apps/azureus"	# use full path to Azureus bin dir
#######################################
```

to read as:
```
######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR="/usr/lib/jvm/java-6-sun/jre/bin/"				# use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
#PROGRAM_DIR="/home/username/apps/azureus"	# use full path to Azureus bin dir
#######################################
```

start by typing ./azureus in console

or

go to your (**options -> plugins -> upnp ->**)
- **uncheck** the reporting of unsuccessful port mappings / ports owned by other computers

fixed it for me
now it works without having to change java source :)

---

### Post by menancito on 2007-10-08
Permanent solution worked like a charm on Gutsy.

---

