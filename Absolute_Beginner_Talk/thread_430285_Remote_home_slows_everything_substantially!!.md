---
title: "Remote /home: slows everything substantially?!?!?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mulligan.can on 2007-05-02
Ok, I've set up a home fileserver in conjunction with my normal desktop mainly for back up purposes.

The server is a basic LAMP rig + apt-cacher + NFS.

I have UID's/GUID's synced between both computers.

I'm exporting /home using nfs and then mounting it on my main rig.

Did this at the same time as upgrading main rig to fiesty, server still runs edgy (server version).

However ever since I've done this amarok is very very unresponsive. It takes about 2 mins to change songs (as in the windoe updating to show whats actually playing)

Would the upgrade or the remote home be causing this? Or perhaps the new version of amarok.

Anyway in addition is having a remote /home a bad idea?

---

### Post by Cypher on 2007-05-02
Take amorak out of the picture for the moment and see if anything else has slowed down as well or if it's isolated to just amorak. Having a remote /home shouldn't necessarily cause a lot of slowdowns since you're in a local network with very low latency. As long as there aren't any creepy errors on the server in relation to NFS then you should be OK.

Also check on your main rig to see if you have any NFS timeouts occuring..

---

