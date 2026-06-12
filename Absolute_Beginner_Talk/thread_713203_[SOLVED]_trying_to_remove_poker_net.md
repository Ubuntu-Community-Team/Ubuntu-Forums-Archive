---
title: "[SOLVED] trying to remove poker net"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Bobrm2 on 2008-03-02
I receive when trying to remove "poker-net" and associated files via Synaptic, Help and suggestions most appreciated. Have also removed Mysql.

Traceback (most recent call last):
  File "/usr/sbin/pokerconfigupgrade", line 121, in <module>
    sys.exit(main())
  File "/usr/sbin/pokerconfigupgrade", line 103, in main
    config.load(file)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokernetworkconfig.py", line 46, in load
    status = pokerengineconfig.Config.load(self, path)
  File "/usr/lib/python2.5/site-packages/pokerengine/pokerengineconfig.py", line 69, in load
    self.doc = libxml2.parseFile(self.path)
  File "/var/lib/python-support/python2.5/libxml2.py", line 1280, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
libxml2.parserError: xmlParseFile() failed
dpkg: error processing python-poker-network (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-poker-network
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thank you

---

