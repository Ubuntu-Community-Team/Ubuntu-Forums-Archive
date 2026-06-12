---
title: "Sun Java 5.0 Runtime Add/Remove Problem"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Escanor Tanthul on 2007-03-08
Heh, I've reinstalled 6.06 Dapper on my laptop today after a few botched attempts at installing Beryl/Compiz and the fact that 6.10 Edgy is buggy on my laptop. I'm trying to install JRE 5 so I can use limewire/frostwire etc. 

When I click the check box to select it I get this message:

"'sun-java5-bin' is not available in any software channel"

The application might not support your system architecture.


All I've done is install the updates that were rdy when I first logged in, my nvidia drivers, and 3ddesk...

the jre doesn't show up in synaptics either, and I believe I installed in tuesday night from synaptics or add/remove just fine..

Any Ideas?

---

### Post by igknighted on 2007-03-08
Java was updated to version 6.  Add/Remove must not have gotten the message (I would avoid it anyway, its not as good as Synaptic/Adept).  Use  synaptic to add all software repo's and search for sun-java6*

---

### Post by phossal on 2007-03-08
Grab it from synaptic *backports* as noted in the previous post, *or* simply download it yourself. Get the appropriate .bin file from java.sun.com and execute it. There probably isn't an easier way to stay current. The backports version, *sun-java6-jdk* uses the .bin file anyway, it's just a more complicated (though partially automated) process - one prepared by a third party.

---

