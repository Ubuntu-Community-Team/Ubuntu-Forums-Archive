---
title: "Can not reinstall CUPS"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by tbooher on 2006-10-01
Help! I am at my wits end. I messed up my cups installation, removed my cupsd.conf file and now can't reinstall. Does anyone know why I am getting this error. I have searched the forums, web, etc and can't find anything.

tbooher@stadion:~$ sudo apt-get --reinstall install cupsys
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
 * Starting Common Unix Printing System: cupsd                                  cupsd: Child exited with status 1!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks,

Tim

---

### Post by tagra123 on 2006-10-01
Try using synaptic-package manager and completely uninstall cups and then reinstall. 

I had to do this once and I think you will have better luck using synaptic.

If someone knows a better way please post.

---

### Post by tbooher on 2006-10-02
yes -- tried that to no avail. I get the exact same error when using synaptic.

any other thoughts?

Tim

---

### Post by tagra123 on 2006-10-02
try
Unistall cups using synaptic.

then type from the command prompt

sudo rm -f -R /etc/cups

Then install cups using synaptic.

---

### Post by tbooher on 2006-10-02
tried as you said, but got the error:

E: cupsys: subprocess post-installation script returned error exit status 1

any more thoughts?

tim

---

### Post by tbooher on 2006-10-02
Just in case, searching this post might help someone else...

O.K. everything has been a breeze in Ubuntu, but printing, which has been incredibly hard. here is my update.

After deleting /etc/cups i needed to add cupsd.conf and cups.d/ports.conf and browsing.conf

I found these files by google: cupsd filetype:conf

used vi to paste then in. and at least cups installs without an error. now i am back to square one, where windows won't talk to ubuntu.

---

### Post by tagra123 on 2006-10-02
OK

I'm assuming you can print from the ubuntu machine.

Try my how-to and see if you can print.

It shows you how to workaround the broke cups 1.2

[http://ubuntuforums.org/showthread.php?t=245052](http://ubuntuforums.org/showthread.php?t=245052)

---

