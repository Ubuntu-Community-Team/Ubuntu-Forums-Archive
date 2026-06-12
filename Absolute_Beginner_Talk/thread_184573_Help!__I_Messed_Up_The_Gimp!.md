---
title: "Help!  I Messed Up The Gimp!"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by unoobu on 2006-05-30
Okay, I went to install gimp_2.3.8-1_i386.deb without uninstalling my old version of GIMP first...  Then when I realized what I had done it was too late.  So, I completely removed GIMP and Ubuntu-Desktop...  Then I reinstalled the new deb file, and I used synapse to reinstall Ubuntu-Desktop...

Now, In my applications bar, I get two GIMP icons...  One gives this error:

"Cannot launch entry

Details: Failed to execute child process "gimp-remote-2.2" (No such file or directory)"

The other one starts GIMP, but doesn't show the splash screen.  Then it just kills itself before booting the GUI.  I checked this under the system monitor.  It pops up saying, "starting GNU Image Manipulation Program...  and then it just kills itself before even showing up on the system monitor.  

PLEASE HELP, I NEED GIMP!  I want to stop using Photoshop 7.0 w/ GIMP.  I want to resolve ALL of my dependencies on proprietary software!  Please help!!!!

**ANOTHER UPDATE**  I uninstalled all gimps using the following commands...  sudo apt-get remove gimp & sudo dpkg -r gimp

They both remove, but I still get the errors posted in the below update.  Now, when I try to install this gimp deb file, this is the error message I get:

usrname@pcname:~/Desktop$ sudo dpkg -i gimp_2.3.7-1_i386.deb
Selecting previously deselected package gimp.
(Reading database ... 95913 files and directories currently installed.)
Unpacking gimp (from gimp_2.3.7-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in cop y)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing gimp_2.3.7-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/lib/libgimpui-2 .0.so.0.307.0')
Errors were encountered while processing:
 gimp_2.3.7-1_i386.deb


**UPDATE**  This may be the problem, although I do not know how to fix it.  I tried to uninstall GIMP again and this is what I get... (Full terminal copy and paste)

usrname@pcname:~$ sudo apt-get remove gimp
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gimp ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 48.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98241 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gimp ...
dpkg - warning: while removing gimp, directory `/usr/local/share/locale' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/bin' not empty so not removed.

Does this mean I need to uninstall all of GIMP's dependents first?  That is a hastle, I will wait for comfirmation before I do it.

Peace,

uNOOB

---

### Post by sudomania4 on 2006-05-30
you shouldnt remove ubuntu-desktop, it will break your system. open a terminal and type```
sudo apt-get install ubuntu-desktop
``` That probably wont fix your problem, but if you remove ubuntu-desktop, you will have other problems.

---

### Post by [S|G] on 2006-05-30
Try this:
```

sudo apt-get install -f
sudo apt-get install --reinstall gimp

```
Also, try to start gimp from your terminal and then post the error messages here... That will make troubleshooting a lot easier :) (To start gimp from a terminal just type "gimp" on it)

---

### Post by unoobu on 2006-05-31
[QUOTE='[S|G]']Try this:
```

sudo apt-get install -f
sudo apt-get install --reinstall gimp

```
Also, try to start gimp from your terminal and then post the error messages here... That will make troubleshooting a lot easier :) (To start gimp from a terminal just type "gimp" on it)[/QUOTE]

**ANOTHER UPDATE**  I uninstalled all gimps using the following commands...  sudo apt-get remove gimp & sudo dpkg -r gimp

They both remove, but I still get the errors posted in the below update.  Now, when I try to install this gimp deb file, this is the error message I get:

usrname@pcname:~/Desktop$ sudo dpkg -i gimp_2.3.7-1_i386.deb
Selecting previously deselected package gimp.
(Reading database ... 95913 files and directories currently installed.)
Unpacking gimp (from gimp_2.3.7-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in cop y)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing gimp_2.3.7-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/lib/libgimpui-2 .0.so.0.307.0')
Errors were encountered while processing:
 gimp_2.3.7-1_i386.deb


**UPDATE**  This may be the problem, although I do not know how to fix it.  I tried to uninstall GIMP again and this is what I get... (Full terminal copy and paste)

usrname@pcname:~$ sudo apt-get remove gimp
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gimp ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 48.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98241 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gimp ...
dpkg - warning: while removing gimp, directory `/usr/local/share/locale' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing gimp, directory `/usr/local/bin' not empty so not removed.

---

### Post by unoobu on 2006-05-31
P.S.  I am running 5.01, and these deb packages may have been meant for 6.06...  However, if this is the problem, can somebody just tell me how to get rid of the Debian GIMP INSTALL icon in the applications menu...  The icon doesn't appear in the Applications Menu Editor, but the icon is right there under Graphics...  and I can't remove it.  So that I can just run the old version of GIMP, and wait until 6.06 is officially released?

However, if anyone has a full solution, I would like to learn GIMP via the latest functional version which is in my downloaded deb file.

Peace,

uNOOBu

---

### Post by [S|G] on 2006-05-31
Did you try sudo apt-get install --reinstall gimp ? Or, if that doesn't work, just sudo apt-get install gimp

---

### Post by unoobu on 2006-05-31
[QUOTE='[S|G]']Did you try sudo apt-get install --reinstall gimp ? Or, if that doesn't work, just sudo apt-get install gimp[/QUOTE]

Thanks S|G, the problem sort of fixed itself.  I removed both packages, rebooted, and then reinstalled gimp via apt-get install...

It works.

Thanks,

uNOOBu

---

