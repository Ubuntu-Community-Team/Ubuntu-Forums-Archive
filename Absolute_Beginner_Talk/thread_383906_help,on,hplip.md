---
title: "help,on,hplip"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by tonymatt on 2007-03-13
Am new to ubuntu edgy (no more windows), tried to run HPLIP to setup my HP 1510 printer and got following error:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.
Running 'sudo apt-get install --yes --force-yes build-essential libjpeg62-dev build-essential python-dev libcupsys2-dev libusb-dev lsb openssl libsnmp9-dev python-qt3 python-reportlab sane-utils'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s)? (y=yes*, n=no, q=quit) : 

can anyone help and explain
thnks
tony:guitar:

---

### Post by 11hjpphty76lkjj on 2007-03-23
Can you try this:

cd ~/hplip-<version> (or cd into the hplip directory
./installer.py -g

follow the steps, post the log when you get the error.

because it's during the download dependencies step ensure that you have turned on the universe and multiverse repos in synatpic.

---

