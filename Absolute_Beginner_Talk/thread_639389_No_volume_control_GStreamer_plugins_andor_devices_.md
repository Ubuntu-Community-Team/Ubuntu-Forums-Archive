---
title: "No volume control GStreamer plugins and/or devices found."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by fi0na on 2007-12-13
I have this problem with my sound/volume control exactly as mentioned here: [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)
  
So I began to follow this guide to get it fixed, and suddenly errors occured after I launched the commands “chmod -R a+rwx /dev/snd” and “sudo usermod -G audio <user>", as root. 

Then things from the menu Administration disappeared, and I tried to add them back via System->Preferences->Main Menu but they simply uncheck themselves after I’ve checked them. Strange isn’t it? So I decided to try Update Manager to correct errors, and when I type my password to perform administrative tasks, this error message appears:

“Failed to run /usr/sbin/synaptic ‘–hide-main-window’ ‘–non-interactive’ ‘–parent-window-id’ ‘56623107&#8242; ‘–update-at-startup’ as user root.
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.”

Any particular reason why this happend? How to correct it? And how to make my sound work?

via lspci:
Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

---

### Post by dsplabs on 2007-12-13
Hi fi0na,

Here are a few things you can try:

The error after running **chmod -R a+rwx /dev/snd** is likely to occur because the user you are running this command under does not have adequate permissions. In that case the command should be **sudo chmod -R a+rwx /dev/snd**. 

Assuming that you are logged in as *fiona*. The command which re-adds the *fiona* user to the *audio* group, should look like this: **sudo usermod -G audio fiona**. Run this command, then enter password for *fiona*, reboot, login as *fiona* and test if the sound is working.

You can also have a look at some further details here:  [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/#comment-41](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/#comment-41)

Cheers
Kamil

---

### Post by fi0na on 2008-01-07
Thanks but this thread solved my problem: [http://ubuntuforums.org/showthread.php?p=2170978#post2170978](http://ubuntuforums.org/showthread.php?p=2170978#post2170978)

---

