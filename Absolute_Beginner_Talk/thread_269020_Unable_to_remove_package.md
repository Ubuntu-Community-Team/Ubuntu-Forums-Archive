---
title: "Unable to remove package"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Humph on 2006-10-01
In an effort to get my Brother HL-1030 printer working I downloaded the LPR package from [Brother's website](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) and attempted to install it. The original installation attempt threw a bunch of stuff back at me like this:

andyo@andyo-ubuntu:~$ sudo dpkg -i hl1030lpr-1.1.2-1.i386.deb
Selecting previously deselected package hl1030lpr.
(Reading database ... 73289 files and directories currently installed.)
Preparing to replace hl1030lpr 1.1.2-1 (using hl1030lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1030lpr ...
/var/lib/dpkg/info/hl1030lpr.postrm: line 3: /etc/init.d/lpd: No such file or di rectory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1030lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1030lpr-1.1.2-1.i386.deb

After RTFM I realised that this was not the correct way to install the package (see the "Click Here" link on above web page which I didn't spot until the damage was done!).

And now when I open Package Manager I get the following message:

E: The package hl1030lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

As the printer works fine without lpr (it happily uses the cups package) I decided I'd just get rid of the package. I have tried re-installing, removing and purging, (using both aptitude and dpkg) but I just can't seem to remove the dang thing:

andyo@andyo-ubuntu:~$ sudo aptitude purge hl1030lpr
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  hl1030lpr{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing hl1030lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
andyo@andyo-ubuntu:~$ Errors were encountered while processing:
 hl1030lpr

Is there any way I can manually remove the information about this package so Package Manager quits whining about it?

I've only been using Ubuntu for a day (most of which was spent trying to remove this damn thing!) so some lead-me-by-the-hand help would be very much appreciated.

---

### Post by nthdegree on 2006-10-01
Sorry to sound a little evil but are those drivers FOSS or Proprietary?

1st try apt-get -f install
2nd of all use dpkg to force it's removal

dpkg --help should list all the switches you should need to force a removal and ignore errors.

---

### Post by Humph on 2006-10-01
Bah. Tried forcing uninstall, etc., etc.

I gave up in the end and re-installed Ubuntu. 

Works fine now.

Now I just need to figure out how to get Ubuntu to talk with my print server...

---

