---
title: "[SOLVED] MusicBrainz Picard on Feisty"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by meindian523 on 2008-01-25
I'm running Ubuntu Feisty and since the repo on launchpad for picard has a deb only for Gutsy,I decided to use the tarball.
Well,I ran python setup.py config
```

    easwarh@l1nuxr0cks:~/Downloads/picard-0.9.0$ python setup.py config
    running config
    checking for pkg-cfg... yes
    checking for libofa... (pkg-config) yes
    checking for libavcodec/libavformat... (pkg-config) no
    checking for directshow... no
    saving build.cfg
    easwarh@l1nuxr0cks:~/Downloads/picard-0.9.0$

```
and got the above and python setup.py install gave a long list of scrolling text and after that when I ran picard from terminal,I got the following error:
```

    easwarh@l1nuxr0cks:~/Downloads/picard-0.9.0$ picard
    Traceback (most recent call last):
      File "/usr/bin/picard", line 2, in <module>
        from picard.tagger import main; main('/usr/share/locale', True)
      File "/usr/lib/python2.5/site-packages/picard/tagger.py", line 54, in <module>
        from picard import musicdns, version_string, log
      File "/usr/lib/python2.5/site-packages/picard/musicdns/__init__.py", line 28, in <module>
        from picard.util.thread import proxy_to_main
      File "/usr/lib/python2.5/site-packages/picard/util/thread.py", line 75, in <module>
        class ThreadPool(QtCore.QObject):
      File "/usr/lib/python2.5/site-packages/picard/util/thread.py", line 107, in ThreadPool
        def call(self, queue, func, next, priority=QtCore.Qt.LowEventPriority):
    AttributeError: LowEventPriority
    easwarh@l1nuxr0cks:~/Downloads/picard-0.9.0$

```
Can someone help with decoding this error and what I'm supposed to do next?

---

### Post by rhc on 2008-01-25
[http://musicbrainz.org/doc/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2](http://musicbrainz.org/doc/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2)

Isn't this easier with repositories?
Doesn't it work?

---

### Post by meindian523 on 2008-01-25
If you noticed,I said that the debs available only for gutsy while I'm running Feisty.I also tried opening the repository in FF and there was no feisty folder under dists.

And no,it doesn't work.

---

### Post by meindian523 on 2008-01-26
bump?

---

### Post by meindian523 on 2008-01-27
bump2?

---

### Post by meindian523 on 2008-01-29
bump3?Oh God,won't I receive any help here?

---

### Post by meindian523 on 2008-02-16
MusicBrainz Picard is still not installed,but ex falso did the job for me,but that doesn't mean I wouldn't want accurate tag information,so this topic is till open.Anyone?

---

### Post by meindian523 on 2008-02-18
bump

---

### Post by meindian523 on 2008-02-24
So now I've installed Picard at the cost of a some megabytes of download of Qt,PyQt and SIP which were all dependencies for Picard and each had to be manually compiled.My first succesful compilation of software!YooHoo!

---

