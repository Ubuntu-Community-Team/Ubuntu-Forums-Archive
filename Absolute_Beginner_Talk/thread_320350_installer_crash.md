---
title: "installer crash?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-17
so i've partitioned and all that jazz (at least i'm pretty sure i did) and i begin to install ubuntu and this comes up...

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 466, in copy_all
    shutil.copyfile(sourcepath, targetpath)
  File "/usr/lib/python2.4/shutil.py", line 49, in copyfile
    copyfileobj(fsrc, fdst)
  File "/usr/lib/python2.4/shutil.py", line 25, in copyfileobj
    fdst.write(buf)
IOError: [Errno 28] No space left on device


now what does that mean?

---

### Post by maxamillion on 2006-12-17
> IOError: [Errno 28] No space left on device

This would indicate that either the physical disk has run out of space for installation or the partition you selected to install ubuntu onto has run out of space. 

What is the size of your hard drive and how did you setup your partitions?

/me

---

### Post by andrewpb on 2006-12-17
well i don't really know how to describe how i set up the partitions, however when i restarted my computer i was hoping to get back into windows for the time being, however it seems as though during the installation that did occur windows or the partition windows was on was erased, so now i my only OS is ubuntu from the cd...HELP!

---

### Post by maxamillion on 2006-12-17
While on the live cd, look on gparted to see if there is a ntfs partition still on the hard drive, if not then your windows is gone and if there is we would just need to edit the grub.conf file to point to it.

/me

---

### Post by andrewpb on 2006-12-17
i'm looking in disks manager and i see no "ntfs" just "hdc#" with # being whatever number partition it is

---

### Post by andrewpb on 2006-12-17
wait i just found the "ntfs" it is under partition 2 or /dev/hdc2

now how can we edit that grub.comf stuff?

thanks

---

### Post by andrewpb on 2006-12-17
anybody know how to edit grub to do this?](*,)

---

### Post by maxamillion on 2006-12-17
sudo update-grub

run that in the command line, should write it for you ...

---

### Post by andrewpb on 2006-12-17
thanks, however i am so new at this even that is kinda confusing, explain a little more, i really appreciate it

---

### Post by andrewpb on 2006-12-17
so i punched in that command and it reads

Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

i then triedboth suggestions and came to no avail...

any ideers?

---

### Post by andrewpb on 2006-12-17
i'm pretty close to just reformating the entire drive and starting over with ubuntu.  but i would like to save the rest of my windows stuff first.  i would appreciate any feedback on what may be happening
:-k

---

### Post by andrewpb on 2006-12-18
could anybody give let me know how to do this?  :confused: 

danka

---

### Post by shareMenaPeace on 2006-12-31
I run into the same error, but i wonder if this is related to disc space as the partition i assigned is 24 gigabyte hugh....

I will check and make a new partition or resize.

---

### Post by shareMenaPeace on 2006-12-31
Great now when i boot i get Error loading operating system ....

---

### Post by shareMenaPeace on 2006-12-31
Strange,
i retried it this time i didnt repartioned the choosen drive and it worked...

and gogod news win xp is still accessable!

haha!

---

