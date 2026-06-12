---
title: "Hard Disk Wrong Size, ubuntu live 6.06 LTS install"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by krazyderek on 2008-02-22
I'm dealing with a wiped 20gb IBM deskstar drive (yes a bit old). When ever i boot into the ubuntu live cd, gparted and the disk manager both only see the drive as 1.97gb of free unpartitioned space, instead of 19.7gb. If i boot with something like the HIREN cd and open partition magic i can see 19 gigs of unpartitioned space 
What gives? 

Anyways, needless to say i get an error when trying to install ubuntu.

[IMG]http://i171.photobucket.com/albums/u318/krazyderek/GParted.png[/IMG]
[IMG]http://i171.photobucket.com/albums/u318/krazyderek/Disks_Manager.png[/IMG]

```
Installer Crashed

We're sorry; the installer crashed. Please file a new bug report at
https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not
attach your details to any existing bug) and a developer will attend
to the problem as soon as possible. To help the developers understand
what went wrong, include the following detail in your bug report, and
attach the files /var/log/installer/syslog, /var/log/syslog, and
/var/log/partman:

Traceback (most recent call last):
 File "/usr/bin/ubiquity", line 130, in ?
   install(sys.argv[1])
 File "/usr/bin/ubiquity", line 55, in install
   ret = wizard.run()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py",
line 264, in run
   self.progress_loop()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py",
line 550, in progress_loop
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
```
p

---

### Post by freelinuxhelp on 2008-02-22
I have an old 16GB IBM drive. It has a jumper settings to limit the size to 2GB... a work around for some old limitation or something...
Anyway, that might be something to look into. I think it was called 2GB Clip.

---

### Post by krazyderek on 2008-02-22
hmm i was playing with the jumpers now that you mention it.... it's odd that it would still show up in partition magic from a boot cd..... but maybe....

---

### Post by freelinuxhelp on 2008-03-08
Did you ever have any luck with this?

---

### Post by handy on 2008-03-08
> **freelinuxhelp said:**
> Did you ever have any luck with this?

I'd forgotten about that...

I'm sure that was his problem.

PartitionMagic can be a law unto itself.

---

