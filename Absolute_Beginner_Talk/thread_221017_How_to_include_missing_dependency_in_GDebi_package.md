---
title: "How to include missing dependency in GDebi package installer?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-07-22
Am trying to install Mailwasher.

Have downloaded the .deb file but when I double-click on it to install it with GDdebi package installer, it fails with a message about a "dependency not satisfiable", along with the name of the missing module.

I have now downloaded the missing module, also a .deb file.

How do I now execute the installer in such a way as to include the missing module? Both .deb files have been downloaded onto my desktop.

---

### Post by Arisna on 2006-07-22
I would simply install the .deb with the required module first, then install Mailwasher.  Would that work, or do you need it to be pulled in automatically or something?

---

### Post by DSn0wMan on 2006-07-22
Use this:```
sudo dpkg -i the_name_of_the_file.deb
```

---

### Post by SteveHoffmanUK on 2006-07-22
DSnowman wrote:
> Use this:
Code:

sudo dpkg -i the_name_of_the_file.deb


Erm, don't forget, you're in newbie country here. WHICH file do I install? I've got two of them: the Mailwasher package (with the missing .deb file) and the missing .deb file. 

Do I install both, if so, in which order?

Many thanks for your help.

---

### Post by DSn0wMan on 2006-07-22
Sorry, install the dependency first.

---

### Post by SteveHoffmanUK on 2006-07-22
Dsnowman: thanks for the clarification.

Started by trying to install the missing .deb file and got this:
```
steve@steve-desktop:~$ sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb
Password:
dpkg: error processing libqt3c102-mt_3.3.4-3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libqt3c102-mt_3.3.4-3_i386.deb

```
I've rechecked the file name and I've typed it OK. Am I in the wrong directory when doing this, maybe? Both deb files are in my desktop.

---

### Post by DSn0wMan on 2006-07-22
You usually get that if you don't get the file name typed in correctly. Try using tab completion. Just type the first few letters then hit tab and it will complete the file name for you.

You need to be in the directory that the file is in.

It may also be esier to install this stuff using synaptic, or apt-get.

edit: if the files are on your desktop they should be at "/home/your_user_name/desktop/the_file.deb"

---

### Post by SteveHoffmanUK on 2006-07-22
DSnowMan

It's OK -- got it to install by double-clicking on the missing file first (invoking the GDebi installer), then doing the same on the main Mailwasher program. It was quite happy with that order, and is now up and running.

Many thanks for your advice.

---

### Post by tonywhelan on 2006-09-24
Having just migrated from WinXP to Ubuntu 6, the one thing I missed was Mailwasher Pro. So pleased to see a Linux version. Thanks for the tips on getting it installed. 

It was also good to find that my licence key from Windows worked on the Linux version.

There seem to be a couple of bugs still. First, when mailwasher starts it doesn't minimise even when I tick the 'minimise on startup' option. Not a big deal.

Second, more annoying, is then when I try to log off the computer, I get a dialog box popping up that says "Your session has been saved". When I close the dialog, nothing happens. No logoff. Have to kill the mailwasher process then can log off as normal.

This may be specific to my machine, but if anyone else has the same problem I'd like to know so can email Firetrust about it.


------------------------------------------------
Here's my version of the instructions for the record

In order to have Mailwasher Pro install on Ubuntu Dapper change the DEBIAN/control file to check for the libqt3-mt library:

=========================================
Issue these commands from root terminal in folder where DEB file is located:

mv mailwasher_1.1.2_i386_kubuntu.deb mailwasher_1.1.2_i386_kubuntu.deb.orig

mkdir mailwasher.tmp

dpkg-deb --extract mailwasher_1.1.2_i386_kubuntu.deb.orig mailwasher.tmp

dpkg-deb --control mailwasher_1.1.2_i386_kubuntu.deb.orig mailwasher.tmp/DEBIAN

# Now use your favorite editor to edit the control file and add in an "OR" for libqt3-mt:

# Change From:
# Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libqt3c102-mt (>= 3:3.3.3), libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
#To:
# Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libqt3c102-mt (>= 3:3.3.3) | libqt3-mt, libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)

gedit mailwasher.tmp/DEBIAN/control

dpkg --build mailwasher.tmp

mv mailwasher.tmp.deb mailwasher_1.1.2_i386_ubuntu.deb

---

### Post by Argyll on 2006-10-14
Thanks for the discussion about Mailwasher. I was having the same dependency problem and as a newbie was unsure just what I was doing. I followed what you had done and now Mailwasher is up and running. Steve.

---

