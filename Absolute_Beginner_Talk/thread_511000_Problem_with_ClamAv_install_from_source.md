---
title: "Problem with ClamAv install from source"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-07-27
To all,

Can anyone help?

I am relatively new to Linux.  I attempted to compile ClamAv from source to get the latest version.  I removed my original ClamAv package before starting.  I downloaded the source code, and, as far as I could tell, got it installed using "./configure, make, and sudo make install."

I then ran freshclam from the command line and received some error messages, with instructions to edit the example config file for freshclam.config, and also to edit the example config file for clamd.config.  Another error message noted that I could not parse the example clamd.config (or something like that).  I could not manage to work past this.  I don't understand "parse."

Then, I installed clamTk from the synaptic packages, which is an older version of the current clamTk version per the clamTk home page.  When clamTk installed, it appeared to re-install the older version of ClamAv (0.88).  I went to Synaptic Package Manager and the older ClamAv package is marked as installed.

How can I tell what version of ClamAv I actually have on my system?  I have confirmation that my signatures are up to date, and I can run scans via the clamTk GUI, but I don't know the version.

If anyone has any suggestions I would appreciate it.

---

### Post by Mornedhel on 2007-07-27
If you reinstalled a package depending on the ClamAV package, it's pretty normal that the Ubuntu repository package for ClamAV got reinstalled (apt-get does not know about what you may or may not have installed from source). If you want ClamTK to work, you cannot install it from Synaptic. I think dpkg does not care about dependencies, could someone confirm/help ?

---

### Post by F_r_e_d on 2007-07-27
OK that sounds logical;  I'll probably remove ClamAv and ClamTk and start all over again from source code only.

Can anyone help with my other issues about configuring the freshclam files?

---

### Post by F_r_e_d on 2007-07-30
I originally loaded Clamav from the ubuntu/debian packages, then un-installed it because freshclam kept saying my version was out of date (though everything was working well), then I loaded it from source, after which things didn't work right.

Then I tried reloading the package over the source download, since the wiki page said it wasn't critical to remove the source files.

Now, my plan is to remove everything associated with clamav and start over, but the clamav and associated files are located throughout my file system and I can't figure out how to remove them all; hence, my question below about using the "make uninstall" command to remove all the source packages.  Or, I guess I could just manually remove the files, but I tried removing a clamd.config file and there didn't seem to be a "delete" option.

Since I can't get the version of clamav (that I compiled from source)
to work properly, I'm going to remove it, then reinstall it from a
(debian) package, which I know will work.  

To remove clamav compiled from source, the clamav wiki says to enter
"make uninstall" from the command line.  I tried "make uninstall clamav", but that didn't work.

Question:  How do I remove all the files that were downloaded 
when I compiled clamav from source so that I can do a fresh install
from the packages?

---

### Post by Paul820 on 2007-07-30
If you still have the folder with all the source code where you built it from make uninstall should work.
It has to be done from that folder so make can backtrack. cd to the folder with the source in, and just type 'make uninstall' without the quotes into the terminal. If you don't have the original folder from where you compiled it from it will be difficult to take it back out. You could try looking for all the files and deleting them but will you get them all? That's the trouble with compiling from source, synaptic does not know what has been installed on you computer so it can't help you there. The best way is after you compile it is to make it into a .deb file and install it that way. Too late now though.

Hopefully you didn't delete your original folder.

---

### Post by F_r_e_d on 2007-07-30
OK I'm not sure where the souce folder is but I'll look.

Do you have any links that could show me how to turn a source download into a .deb file?  I didn't know you could do that!

Thanks.

---

