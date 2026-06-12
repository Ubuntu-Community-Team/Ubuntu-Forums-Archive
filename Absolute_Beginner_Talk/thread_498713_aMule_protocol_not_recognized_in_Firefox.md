---
title: "aMule protocol not recognized in Firefox"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-07-11
cant seem to launch ed2k protocol links from FF into aMule . 
I searched the forums and this advice was given. 
In amule select...
> Preferences->General, and select your browser as FirefoxBut this doesn't work for me. I also tried the user defined browser selection and pointed it to FF again, but still no luck. 
Does anyone have anything else I can try? 
Thanks.

---

### Post by felicity on 2007-07-12
You need to configure firefox itself to accept that MIME type. There is a firefox extension called MIME edit that can do this.. though there should be a better way.. I find that extension to be buggy.. but it's all I know for now. :)

---

### Post by Hallvor on 2007-07-12
I just copy and paste the ed2k links.

---

### Post by masingerz on 2008-03-02
thank you that worked

---

### Post by Hallvor on 2008-03-02
From my How-to:

"9. Make Firefox accept eD2k links
eD2k links are available on the web and function pretty much the same way as torrentfiles. It is possible to copy the links, paste them into aMule`s eD2k link handler on the bottom of the screen. But a much easier way is to associate eD2k-links to aMule through Firefox. eD2k links will then be added directly to aMule with a click of a button.

eD2k links will not launch in a browser of you haven`t got amule-utils installed. Install it with

Code:

sudo apt-get install amule-utils

(1.) Launch Firefox.

(2.) Then, insert about:config in the address bar. Right click on the list, select New, then Boolean; insert network.protocol-handler.external.ed2k as Preference Name and true as Value.

(3.) Now another right click, select New and String; insert network.protocol-handler.app.ed2k as Preference Name and /usr/bin/ed2k (or path to where the file is installed on you system) as Value.

(4.) Restart Firefox.

Now eD2k links will be captured by aMule"

That should do it.

---

### Post by dover19 on 2008-05-01
Nope, that HowTo doesn't do anything for me anyway...it can't be this complicated.

---

### Post by cisforcojo on 2008-05-20
Doesn't do anything for me either.

---

### Post by Hallvor on 2008-05-20
> **cisforcojo said:**
> Doesn't do anything for me either.


Do you have amule-utils installed?

---

### Post by bit-a on 2008-06-01
Just to have this complete for future readers (there is much confusion about this in other threads of this forum):

whatever you enter into network.protocol-handler.app.ed2k, you can easily make sure it works by typing exactly the same string on a command line.
```
john@doe:~$ /usr/bin/ed2k
bash: /usr/bin/ed2k: No such file or directory
john@doe:~$ /usr/bin/mldonkey_submit
You must provide an ed2k link
```

btw: as there's no such thing like amule-utils for mldonkey (both variants of mldonkey_submit look broken) you can do the following to make firefox 3.0 work together with mlnet:

**/usr/bin/ed2k** (don't forget to make it executable)
```
#! /usr/bin/python

import sys
import telnetlib
import xml.dom.minidom as dom

def isEd2kUri(uri):
  #todo: security-relevant!!!
  return True

def getConnectionData():
  config=dom.parse('/etc/ed2k.mldonkey').documentElement
  return (
    str(config.getAttribute('host')),
    int(config.getAttribute('port')),
  )

if __name__=='__main__':
  assert len(sys.argv)==2
  assert isEd2kUri(sys.argv[1])
 
  host,port=getConnectionData()
  uri=sys.argv[1]
  
  session=telnetlib.Telnet(host,port)
  session.read_until('\n>')
  session.write('dllink %s\n'%uri)
  session.write('exit\n')
  session.read_all()
```

**/etc/ed2k.mldonkey**
```
<config
  host="localhost"
  port="4000"
/>
```

---

