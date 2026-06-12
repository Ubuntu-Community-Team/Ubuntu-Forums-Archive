---
title: "Looking for an XDMCP client"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by steve.horsley on 2007-07-08
I have just installed an old PC as a server. I enabled XDMCP login, and can log in from the ligin screen of my desktop. But I would like to be able to have a login to the server running in a window in my normal login, like VNC, rdesktop or VMware does. Is there an XDMCP client that will allow me to do this?

---

### Post by ayenack on 2007-07-09
Not to sure but I think this does the job [pxdmcp]("http://linux.softpedia.com/get/System/Networking/pxdmcp-6463.shtml#"). google it for more info. I know that it's a stand alone client but haven't used this particular app so not to sure exactly how it displays. I think XNEST might work also sudo apt-get install xnest it's should be in the repo's.

---

### Post by steve.horsley on 2007-07-09
Thank you. 

pxdmcp won't compile (can't find libsocket).
xnest (in the repos) has a note that says Xephyr is to be preferred, but Xephyr won't run - it just complains there's already an X server running - duh!

But xnest installs and works fine, thanks. It enables the (initially greyed out) XDMCP optiion in Internet->Terminal Server Client, and is just what I was looking for.

---

### Post by ayenack on 2007-07-09
Great stuff glad to hear it.

---

