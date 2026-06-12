---
title: "Network rlogin"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by mechanic on 2005-11-02
I notice that Ubuntu has found the local network (Windows workgroup) on connection and I can copy files from the W. machines to U. On the other hand U refuses to accept even a rlogin from cygwin on the W box, although I can ping it ok. What do I have to do to enable a remote login to the U box?

m.

---

### Post by tonym on 2005-11-02
You need to ensure the appropriate server package is loaded on te Ubuntu system.  Not sure what you need for rlogin but ssh is seems to be preferred for security reasons.  You would need to install the openssh-server package on Ubuntu if it isn't loaded already and an ssh client on cygwin.  There is also a native Windows ssh client - putty - that works fine.

---

### Post by mechanic on 2005-11-02
What about this WinSCP prog recommended in the 'how to' document? Although that seems to be an automated FTP client it looks useful.

m.

---

### Post by mechanic on 2005-11-02
Update: after installing openssh on cygwin (usual fuss trying to find the appropriate package) and ssh on Unbuntu I was able to ssh into the U box and explore files, run vim on them and so on. Installing the WinSCP on the Windows box gave me a useful gui to swap files around with, and all worked fine. Success!

m.

---

