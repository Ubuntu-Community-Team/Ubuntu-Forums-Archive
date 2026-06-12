---
title: "Apps close"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by ranman on 2005-09-18
Hi i wouldn't consider myself an absolute beginner because I have been using a linux shell account for about 3 years and anyway let me get onto the questtion:
I just got ubuntu and for some reason a number of programs begin to start up and then imediatly crash or quit.  here is a list of the programs:
BloGTK
ImageVeiwer
Firefox - This only happens when i goto a page with java on it.

Any help would be greatly appreciated thank you   :)

---

### Post by auburn on 2005-09-18
they discussed firefox with java crashes here:
[http://www.ubuntuforums.org/showthread.php?t=41031&page=1&pp=10&highlight=firefox+java](http://www.ubuntuforums.org/showthread.php?t=41031&page=1&pp=10&highlight=firefox+java)

---

### Post by ranman on 2005-09-19
thanks ok this is the terminal output from BloGTK

~~~~~~@~~~~~:~$ BloGTK
Traceback (most recent call last):
  File "/usr/bin/BloGTK", line 1230, in ?
    blogtk = BloGTK()
  File "/usr/bin/BloGTK", line 133, in __init__
    self.grabConfig()
  File "/usr/bin/BloGTK", line 421, in grabConfig
    self.rpcServer = proxy.get_xmlrpc_server(self.url)
  File "/usr/lib/blogtk/proxy.py", line 66, in get_xmlrpc_server
    return server(url)
  File "/usr/lib/python2.4/xmlrpclib.py", line 1357, in __init__
    raise IOError, "unsupported XML-RPC protocol"
IOError: unsupported XML-RPC protocol
~~~~~@~~~~~:~$
 can anyone help?

---

### Post by ranman on 2005-09-20
nvm i fixed it!
just delete the .BloGTK file in your home directory

---

