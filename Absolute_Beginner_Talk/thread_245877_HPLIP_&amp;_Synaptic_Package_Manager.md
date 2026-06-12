---
title: "HPLIP &amp; Synaptic Package Manager"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by useResa on 2006-08-28
I am trying to get my HP PSC 1410 printer working.

Searching the web and this forum I came across a link to LinuxPrinting.org.
When I look up the recommended driver for my printer I get sent to [http://hplip.sourceforge.net](http://hplip.sourceforge.net)

Here I read that the latest driver for the printer is version 1.6.7.
However, when I look in the Synaptic Package Manager the version indicated there is 0.9.7.

Can anyone explain why these versions seem/are different?

Another question I have is: How do I install the version 1.6.7?
I have downloaded hplip-1.6.7.tar.gz to my desktop.
And will this version not be overwritten by the version that is indicated in Synaptic?

All help is really appreciated.

Additional info: I have also posted a related question in this thread [http://www.ubuntuforums.org/showthread.php?t=245673](http://www.ubuntuforums.org/showthread.php?t=245673)

Configuration:
I have Ubuntu 6.06 LTS on a Dell Latitude D620 laptop and the printer is connected to a Dell desktop on which I (unfortunately) must run WinXp.

---

### Post by bodhi.zazen on 2006-08-28
Not sure if this will help, but....

Try configuring you printer with cups. I have found this to sometimes be easier.

In a web browser (firefox) type (in the address bar)
```
localhost:631
```
This will bring up cups -> click "add printer" --> select yuor printer from HP list or use hplip.

To use your tar file: This is an archived file. Unarchive and look for a README.

In a terminal:
```
cd ~ #
mkdir SRC
mv ~/Desktop/hplip-1.6.7.tar.gz SRC/
cd SRC
tar -xzfv hplip-1.6.7.tar.gz

```
Note: the cd ~ just moves you to your home directory.
I use a directory "SRC" for all tar balls/source in the event they are needed.

There should be a directory in ~/SRC called hplip-1.6.7. Look in that directory for further instruction (README).

If you need to "install" you will need to configure -> make -> make install. Post if you have further questions.

---

### Post by useResa on 2006-08-28
Bodhi.Zazen

Thank you for your suggestion.
I have installed the printer using CUPS.
However, the same problem occurs as when not using CUPS. :???:

The printer makes a sound as if it is going to print something, the busy light starts flashing but it stops reading the "print file" at 64 Kb and nothing else happens. The same as I described in thread [http://www.ubuntuforums.org/showthread.php?t=245673](http://www.ubuntuforums.org/showthread.php?t=245673)

Regarding the installation of the tar file, I have not yet tried that yet.
But if I do have any questions about that I will come back.

---

### Post by bodhi.zazen on 2006-08-28
Download the driver:

[http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-PSC_1400&show=0](http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-PSC_1400&show=0)

now, in a terminal
```
sudo cp HP-PSC_1400-hpijs.ppd /usr/share/cups/model
```

Re-start cups:
```
sudo /etc/init.d/cups restart
```
 Should be good to go, may need to delete and re-add the printer in CUPS. Don't forget to set the printer as defalut (in cups).

---

### Post by useResa on 2006-08-28
I have succeeded in extracting the new driver to a src directory as suggested by you (used the archive manager). So now I have a ~/src/hplip-1.6.7 directory.

Unfortunately there is no readme file anywhere.
What I can find is a install-sh shell script. But when I try to execute this (with sudo) I get the following error: no input file specified.

Any suggestions?

---

### Post by bodhi.zazen on 2006-08-28
1. Try the driver in my previous post first.

2. I know it sounds obvious... What is in the directory ~/SRC/hplip-1.6.7 ? Is there a README or install.sh ?

(cd ~/SRC/hplip-1.6.7
ls)

---

### Post by useResa on 2006-08-28
When I follow your instruction on installing the CUPS printer by using the terminal I cannot give the restart command (Error message is command not found).

In the init.d directory is no "cups" only a "cupsys".

Any suggestions

---

### Post by bodhi.zazen on 2006-08-28
Sorry, try sudo /etc/initr.d/cupsys restart

If that does not work, reboot.

---

### Post by useResa on 2006-08-28
The restart still didn't work so I rebooted, but I still get the same result.
Light flashing and stops reading at 64 Kb.

In the hplip-1.6.7 directory is NO readme and there is only an install-sh file, but that doesn't seem to work (see my previous post).

Maybe the only option is to install this new version and I hope you can help me further.

---

### Post by bodhi.zazen on 2006-08-28
OK, back to the new driver then.

```

cd ~/SRC/hplip-1.6.7
sudo chmod a+x install.sh
sudo sh install.sh
```

Also, what is the output of

ls -l /usr/share/cups
ls -l /usr/share/cups/model

---

### Post by useResa on 2006-08-28
To reply to your last questions first:
The result of ls -l /usr/share/cups is:
drwxr-xr-x 2 root root   4096 2006-08-11 11:12 banners
-rwxr-xr-x 1 root root    835 2006-08-03 10:54 browsing_status
-rw-r--r-- 1 root root 331836 2006-05-03 22:41 calibrate.ppm
drwxr-xr-x 2 root root   4096 2006-08-11 11:12 charmaps
drwxr-xr-x 2 root root   4096 2006-08-11 11:12 charsets
drwxr-xr-x 2 root root   4096 2006-08-11 11:12 data
drwxr-xr-x 9 root root   4096 2006-08-11 11:16 doc-root
-rwxr-xr-x 1 root root   1291 2006-08-03 10:54 enable_browsing
-rwxr-xr-x 1 root root   1391 2006-08-03 10:54 enable_sharing
drwxr-xr-x 2 root root   4096 2006-08-11 11:12 fonts
drwxr-xr-x 2 root root   4096 2006-08-28 23:09 model
-rwxr-xr-x 1 root root    831 2006-08-03 10:54 sharing_status
drwxr-xr-x 7 root root   4096 2006-08-11 11:12 templates

The result of ls-l /usr/share/cups/model is:
lrwxrwxrwx 1 root     root        23 2006-08-11 10:41 cups-included -> ../../ppd/cups-included
lrwxrwxrwx 1 root     root        16 2006-08-11 10:41 custom -> ../../ppd/custom
-rw-r--r-- 1 root     root      3623 2006-01-02 14:16 Generic-OAKT_Printer.ppd.gz
-rw-r--r-- 1 root     root      4092 2006-01-02 14:16 Generic-ZjStream_Printer.ppd.gz
lrwxrwxrwx 1 root     root        20 2006-08-11 10:41 gutenprint -> ../../ppd/gutenprint
-rw-r--r-- 1 root     root      3736 2006-01-02 14:16 HP-Color_LaserJet_1500.ppd.gz
-rw-r--r-- 1 root     root      3452 2006-01-02 14:16 HP-Color_LaserJet_2600n.ppd.gz
lrwxrwxrwx 1 root     root        15 2006-08-11 10:41 hpijs -> ../../ppd/hpijs
-rw-r--r-- 1 root     root      3730 2006-01-02 14:16 HP-LaserJet_1000.ppd.gz
-rw-r--r-- 1 root     root      3734 2006-01-02 14:16 HP-LaserJet_1005.ppd.gz
-rw-r--r-- 1 root     root      3733 2006-01-02 14:16 HP-LaserJet_1020.ppd.gz
-rw-r--r-- 1 rdrijsen rdrijsen 20993 2006-08-28 23:07 HP-PSC_1400-hpijs.ppd
lrwxrwxrwx 1 root     root        38 2006-08-11 10:41 linuxprinting.org-gs-builtin -> ../../ppd/linuxprinting.org-gs-builtin
-rw-r--r-- 1 root     root      4078 2006-01-02 14:16 Minolta-Color_PageWorks_Pro_L.ppd.gz
-rw-r--r-- 1 root     root      4079 2006-01-02 14:16 Minolta-magicolor_2200_DL.ppd.gz
-rw-r--r-- 1 root     root      4177 2006-01-02 14:16 Minolta-magicolor_2300_DL.ppd.gz
-rw-r--r-- 1 root     root      4152 2006-01-02 14:16 Minolta-magicolor_2430_DL.ppd.gz
-rw-r--r-- 1 root     root      9645 2006-05-03 13:45 pxlcolor.ppd
-rw-r--r-- 1 root     root      9453 2006-05-03 13:45 pxlmono.ppd

Does this help?

---

### Post by useResa on 2006-08-28
Regarding the new driver:
I do NOT have an install.sh, there is only an install-sh file.
Or is this the install that you refer to?

PS: How do you get your text in a separate window in your replies?

---

### Post by bodhi.zazen on 2006-08-28
sorry, my eyes read the "-" as a "."

sudo sh install-sh it is then.....

---

### Post by useResa on 2006-08-28
When I try this, the following result I get:
install-sh: no input file specified.

I think I call it a day now (I'm from Holland and we're after midnight here now). 
Should you have any more suggestions I'll read them tomorrow.
Thnx in advance

---

### Post by bodhi.zazen on 2006-08-28
> **useResa said:**
> PS: How do you get your text in a separate window in your replies?

Use a set of brackets:]code[ TEXT TO INSERT ]/code[

or ]quote[ TEXT TO INSERT ]/quote[

Like this: [co_de]TEXT TO INSERT[co_de] without the underscore.

---

### Post by bodhi.zazen on 2006-08-28
> **useResa said:**
> When I try this, the following result I get:
install-sh: no input file specified.

I think I call it a day now (I'm from Holland and we're after midnight here now). 
Should you have any more suggestions I'll read them tomorrow.
Thnx in advance

I understand.

I downloaded hplip-1.6.7 and looked at the contents.

Try this:
```

cd ~/SRC/hplip-1.6.7
./configure
make
sudo make install
```

You may want to use check install, makes a .deb file, will make apt-get/synaptic able to track hplip.

Install check-install via synaptic.

Then:
```
cd ~/SRC/hplip-1.6.7
./configure
make
sudo checkinstall
```

[http://ubuntuforums.org/archive/index.php/t-2356.html](http://ubuntuforums.org/archive/index.php/t-2356.html)

(look at the first post)

---

### Post by NewDisciple on 2006-08-29
I have the same printer and I use the 0.9.7 version found in Synaptic package manager and it works just fine.  I also installed the hpijs driver as well.  I too, am forced into sharing with a windows machine.  We can no longer use a periphial switch though, and we must manually switch between the two computers.  Anyhow, good luck!

---

### Post by useResa on 2006-08-29
@ bodhi.zazen

I have followed your instructions in your last post.
Had to overcome some error statements like: "cannot find libusb support", "cannot find cups-devel support" and "cannot find net-snmp support" by downloading and installing additional packages with synaptic.

Next I ran into a "command 'gcc' failed with exit status 1", but got passed that as well. Things seemed to be going well ...

Next the configure went ok, the make went ok but the checkinstall gave the following error: /bin/sh: line 9: hplip: command not found

Searching the forum I came across this thread: [http://www.ubuntuforums.org/showthread.php?t=196067](http://www.ubuntuforums.org/showthread.php?t=196067) (Uninstall hplip to path it). There it was indicated that the problem was dependency problem and the following was suggested:
```
sudo make uninstall
make clean
sudo rm -rf /usr/share/hplip/

sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev

./configure --prefix=/usr
make
sudo make install
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart
``` 
The apt-get was not necessary for me, solving the items listed below had already resulted for me in installing these packages.
Instead of the sudo make install, I issue sudo checkinstall.
Now the following error is given to me in the log:
> 
Unpacking hplip-1.6.7 (from .../hplip-1.6.7_1.6.7-1_i386.deb) ...
dpkg: error processing ~/src/hplip-1.6.7/hplip-1.6.7_1.6.7-1_i386.deb (--install):
 trying to overwrite `/etc/hp/hplip.conf', which is also in package hplip
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ~/src/hplip-1.6.7/hplip-1.6.7_1.6.7-1_i386.deb 
Any suggestions, I am out of options now.

---

### Post by bodhi.zazen on 2006-08-29
Very nice work !!!

run:
```
apt-get remove hplip
sudo checkinstall hplip-1.6.7
```

---

### Post by useResa on 2006-08-29
Bodhi.zazen,

We're getting closer (I believe). Got past the previous error, it now says

> Unpacking hplip-1.6.7 (from .../hplip-1.6.7_1.6.7-1_i386.deb) ...
dpkg: error processing ~/src/hplip-1.6.7/hplip-1.6.7_1.6.7-1_i386.deb (--install):
 trying to overwrite `/usr/bin/foomatic-rip', which is also in package foomatic-filters
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
~/src/hplip-1.6.7/hplip-1.6.7_1.6.7-1_i386.deb 
Should I apt-get remove foomatic too?

---

### Post by bodhi.zazen on 2006-08-29
Yes I would try removing foomatic.

---

### Post by useResa on 2006-08-29
Succes!!  :p

After continually checking the log and looking at what was already installed by using Synaptic Package Manager the following code did the trick

```
sudo apt-get remove hplip
sudo apt-get remove hplip-data
sudo apt-get remove hplip-ppds
sudo make uninstall
sudo make clean
sudo rm -rf /usr/share/hplip

./configure --prefix=/usr
make
sudo checkinstall
```

After this issued the following command:
```
sudo /etc/init.d/hplip restart
```
with the following result:
> Stopping hpiod:                             [  OK  ]
Stopping hpssd:                                         [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                           [  OK  ]

And finally: ```
sudo /etc/init.d/cupsys restart
```
with the following result:
>  * Restarting Common Unix Printing System: cupsd

Thank you for all your suggestions and support!

---

### Post by bodhi.zazen on 2006-08-29
Congratulations !!

You deserve all the credit, all I did was point you in the right direction.

You should post a link or the solution in the other threads.

Did you learn anything?

---

