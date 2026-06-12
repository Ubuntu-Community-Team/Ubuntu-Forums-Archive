---
title: "ssh Ubuntu--&gt;OS X: Port 22 Connection Refused"
date: 2011-02-13
forum: Apple Hardware Users
---

### Post by p.s. on 2011-02-13
I'm relatively new to using ssh.

I'm able to log in to my ubuntu box from my girlfriend's mac with no problem. Unfortunately, when I try to reverse it (using her mac as the remote) I get the message: Port 22: Connection Refused.

I think there's probably something very simple that I'm missing here, and I'm currently searching around the internet, but a point in the right direction would be much appreciated.

---

### Post by uRock on 2011-02-13
You need a ssh server installed and running on the Mac host.

Moving to Apple Users sub-forum where you might get quicker and more specialized help.

---

### Post by lael on 2011-02-14
Her mac doesn't have ssh enabled.  

In OSX its pretty easy: System Preferences -> Sharing -> Remote Login

Just search for [enable ssh in OSX]("http://www.google.com/search?client=ubuntu&channel=fs&q=enabled+SSH+in+OSX&ie=utf-8&oe=utf-8#sclient=psy&hl=en&source=hp&q=enable+SSH+in+OSX&aq=f&aqi=&aql=f&oq=&pbx=1&fp=c1f3adc9cfc4964")

[http://www.bluishcoder.co.nz/articles/mac-ssh.html](http://www.bluishcoder.co.nz/articles/mac-ssh.html)

---

### Post by p.s. on 2011-02-27
Worked great! Thanks!

---

