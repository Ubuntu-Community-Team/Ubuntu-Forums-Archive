---
title: "Update Packages Fail - how to fix."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-03-22
Yikes -- cannot process updates.

I have been using Ubuntu for the last three months or so, after abandoning MS Windows. As an totally new guy to Linux, I have been able to get Ubuntu to work with most features. Amazing.

However, all of a sudden, the various package managers have failed and updates or indeed new installs cannot be performed.

I always get the following message:

=====

[B]<libmpeg2-4_0.4.0b-4ubuntu1_i386.deb' ;echo RESULT=$?
(Reading database ... dpkg: error processing ///var/cache/apt/archives/libmpeg2-4_0.4.0b-4ubuntu1_i386.deb (--install):
files list file for package `libmpeg2-4' is missing final newline
ssing was Errors were encountered while processing:
///var/cache/apt/archives/libmpeg2-4_0.4.0b-4ubuntu1_i386.deb
Process halted because there were too many errors.
RESULT=1[/B]
=====

Went to the reference file folder, and indeed the archive file seems to be there. The above error indicates that the " file list is missing final new line" I have absolutely no idea where that line might be or how to fix same.


My set up:

IBM Desktop 6792, 2GHz pentium 4, Mem=1.256 GHZ ram, 80 gig disk, USB Creative Extigy sound card, DWL-2000AP+ wireless (in client mode), Nvidia 6600GT 256meg video acceleration installed and working, Logitech MX wireless mouse,

I would appreciate any assistance to fix this issue. Thanks
Edit/Delete Message

---

### Post by sad_iq on 2007-03-22
Try **sudo aptitude update** then **sudo aptitude dist-upgrade** 
 You could also try **sudo apt-get install --reinstall libmpeg2-4** or **sudo dpkg-reconfigure libmpeg2-4** (don't know if this will work though )!
 Also I hope you're not mixing repos are you?

---

### Post by sdgreen on 2007-03-22
Thanks for the reply

I tried your suggestions as indicated in another forum, however such was a no go.

As far as I can tell, all the repros reflect Dapper.

The issue seems to be related to a file list that cannot be found. I have no idea where that file list might be.

---

### Post by Yoooder on 2007-03-22
I'm really not sure this is a solution, however if you bring up your sources list (I think it's under System / Admin / Manage Sources) you could try disabling any 3rd party sources, then re-try the commands given by sad_iq.

This will basically make sure you are only trying to get official Ubuntu packages--although let me reiterate that this is more of a shot in the dark than a solid theory.

---

### Post by sdgreen on 2007-03-22
Thanks for the reply.

Did as suggested, but no go. 

I am really at a loss on this one. Can't even remove the offending file.....

---

### Post by Daremo on 2007-03-22
This is a guess, so anyone else please jump in here. It sounds like a corrupt .deb package that was downloaded. Ununtu will cache (store) these files for future use, such as a reinstall of the package.  When you attempt to redo the update process, Ubuntu is using the same file that is currently stored in the cache folder.

You could clean out the cache folder and then retry the update process. this should force the update manager to download a new copy of that .deb package

To clean out the cache opena terminal window and enter:

sudo apt-get clean

I have done this before without any bad results...

---

### Post by moffa on 2007-03-22
If that does not work out please try:
```
sudo apt-get update
sudo apt-get install -f

```

---

