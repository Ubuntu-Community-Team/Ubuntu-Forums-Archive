---
title: "DansGuardian Upgrade broke DansGuardian"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by harpazo on 2007-04-24
I would greatly appreciate anyone's help with the following problem.  I have search the forums and could not find anything related.

I just upgraded from Edgy to Feisty.  My DansGuardian/FireHol/Tinyproxy stopped working so I completely removed them and reinstalled them following the instructions here:

[http://ubuntuforums.org/showthread.php?t=207008]("http://ubuntuforums.org/showthread.php?t=207008")
[http://ubuntuforums.org/showthread.php?p=2493322]("http://ubuntuforums.org/showthread.php?p=2493322")

DansGuardian worked perfectly until...  I received notification from the package manager that DansGuardian, Tinyproxy, and FireHol all needed to be upgraded.  

After the upgrade DansGuardian stopped working and when I tried (4 times) to remove and reinstall I get the following message:

Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: forkscanlength
Too short or missing.
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am fairly new to Linux and Ubuntu, so If you can help, please give detailed instructions. 

Thanks very much in advance, 

Harpazo

---

### Post by harpazo on 2007-04-25
I fixed the Problem! 

Went to /etc/init.d and removed dansguardian and dpkg-dansguardian scripts, then deleted dansguardian file folder.

Now back to square one, but no more error messages when I run Synaptic.  Also able to remove clamav, tinyproxy, and firehol with no error messages.

Next step - try reinstalling everything....

Ah Linux - sometimes a pain - but at least I can fix the problems myself - not like Windows that hijacks everything, breaks, and then can't be fixed...

Harpazo

---

### Post by Cigar Jack on 2007-04-25
This worked great I was having the same issue. 

Thanks for following up on your problem.

---

### Post by nbcloud on 2008-01-12
I am having the same trouble.  My question is how do I delete files in /etc/init.d?

Thanks

---

### Post by harpazo on 2008-03-20
Sorry I didn't reply to your post.  I'm not used to ready forums and looking for responses to my posts.

To delete the files, I did this (used to windows so I prefer not using command line unless I have to)

Open a terminal and typed:
sudo nautilus

that opens nautilus as root(?)...

then I clicked on "File System" 
then "etc" folder
then "init.d" folder
then found the files I needed to delete, right clicked on each and deleted them.

Hope this helps

Harpazo

---

### Post by f0084r on 2008-04-09
I actually had the same problem.  After reading this post, I tried apt-get -remove dansguardian.  It failed with an error that said to run dpkg --configure -a.  I ran this command, and it let me reinstall the dansguardian.conf file.  I then commented the UNCONFIGURED line and all was well.

---

