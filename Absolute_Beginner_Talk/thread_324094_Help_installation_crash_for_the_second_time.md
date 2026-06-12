---
title: "Help installation crash for the second time"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-23
this is the second time the installation of ubuntu 6.06 has crashed, i don't know whats going on.  i've partitioned to have 18 gigs for ubuntu under a linux swap and that doesn't seem to do it.  this is what the computer churned out when it crashed...

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
  File "/usr/share/ubiquity/install.py", line 455, in copy_all
    os.mkdir(targetpath, mode)
OSError: [Errno 2] No such file or directory: '/target/bin'


could somebody please be kind enough to walk me through this
](*,) ](*,) ](*,) ](*,) ](*,) :confused:

---

### Post by peterj on 2006-12-23
> i've partitioned to have 18 gigs for ubuntu under a linux swap and that doesn't seem to do it.


Not sure I understan you correctly there, did you allocate 18gb for /swap? and none for /?

You should allocate about 1gb for swap space which is a linux's way of increasing (slower) RAM. You then need to allocate you 17gb's to / which is the root filesystem for linux. check this out:

[http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html]("http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html")

Maybe worth a read before you go any further,

---

