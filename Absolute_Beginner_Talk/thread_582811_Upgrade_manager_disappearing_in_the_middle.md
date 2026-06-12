---
title: "Upgrade manager disappearing in the middle"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by skippy_dude on 2007-10-20
I'm using Kubuntu 7.04 and downloaded the alternate cd and tried to update using gksu "sh /cdrom/cdromupgrade" , I already have gksu so it started the upgrade process. Then when it comes to the "installing files" part it still says fetching files? No biggie guess.
The problem starts when it finishes the "installing files" part. The upgrade program just disappears, no warning, no error no nothing. I tried this twice and have checked the md5 hash of the image. What's going on?

Also after all that I just started aptitude and unchecked all repos except the cd one and tried updraging that way. It seems to be waiting for headers for the past 20 minutes and is 44% into that with no headers showing up....

---

### Post by MelodyHacker on 2007-10-25
I'm having the *very same* problem :( The difference is just that I'm using kdesu instead of gksu. Is there any way to find out what the problem is? Cannot find anything useful in /var/log/* (maybe should look somewhere else?)

UPD: Ah... It seems that I've dug something. Wondering, could it be of any help?

_/var/log/dist-upgrade/main.log:_

2007-10-26 01:27:41,853 ERROR not handled expection in KDE frontend:
Traceback (most recent call last):

  File "/tmp/tmpVwYEgi/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 1328, in fullUpgrade
    if not self.doDistUpgrade():

  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 798, in doDistUpgrade
    res = self.cache.commit(fprogress,iprogress)

  File "/tmp/tmpVwYEgi/DistUpgradeCache.py", line 69, in commit
    apt.Cache.commit(self, fprogress, iprogress)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 203, in commit
    res = self.installArchives(pm, installProgress)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 178, in installArchives
    res = installProgress.run(pm)

  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 213, in run
    pid = self.fork()

  File "/tmp/tmpVwYEgi/DistUpgradeViewKDE.py", line 244, in fork
    self.child_pid = os.fork()

OSError: [Errno 12] Cannot allocate memory

_/var/log/dist-upgrade/apt.log:_

Error in sys.excepthook:
Traceback (most recent call last):
  File "/tmp/tmpVwYEgi/DistUpgradeViewKDE.py", line 460, in _handleException
    if not run_apport():
  File "/tmp/tmpVwYEgi/DistUpgradeApport.py", line 44, in run_apport
    ret = subprocess.call(p)
  File "/usr/lib/python2.5/subprocess.py", line 443, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1061, in _execute_child
    self.pid = os.fork()
OSError: [Errno 12] Cannot allocate memory

Original exception was:
Traceback (most recent call last):
  File "/tmp/tmpVwYEgi/gutsy", line 59, in <module>
    app.run()
  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()
  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 1328, in fullUpgrade
    if not self.doDistUpgrade():
  File "/tmp/tmpVwYEgi/DistUpgradeControler.py", line 798, in doDistUpgrade
    res = self.cache.commit(fprogress,iprogress)
  File "/tmp/tmpVwYEgi/DistUpgradeCache.py", line 69, in commit
    apt.Cache.commit(self, fprogress, iprogress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 203, in commit
    res = self.installArchives(pm, installProgress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 178, in installArchives
    res = installProgress.run(pm)
  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 213, in run
    pid = self.fork()
  File "/tmp/tmpVwYEgi/DistUpgradeViewKDE.py", line 244, in fork
    self.child_pid = os.fork()
OSError: [Errno 12] Cannot allocate memory

---

