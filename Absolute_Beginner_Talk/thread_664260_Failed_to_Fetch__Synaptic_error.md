---
title: "Failed to Fetch  Synaptic error"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by desertphotog on 2008-01-11
I'm getting this error as I try to download NDISwrapper to get WiFi working.  I am now on a good wired connection.  So . . .Why?
I had no trouble getting Ubuntu- Restricted-Extras and others last week?

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

---

### Post by yabbadabbadont on 2008-01-11
Can you point your browser to [http://archive.ubuntu.com](http://archive.ubuntu.com) and have it connect properly?

---

### Post by desertphotog on 2008-01-11
Yes, that link worked well. Can I download stuff from there?

---

### Post by OffAxis on 2008-01-11
yes, you could.
accessing the sub-domain directly was checking to see if you had an accessible network path to the repo (not blocked by a firewall, blacklisted, etc)
Likewise, you could click on the links in your own post, download the .deb files, navigate to the folder you downloaded them to, and then install then with
```
sudo dpkg -i [name of .deb file]
```

It also means that the problem probably is somewhere in the apt-get system.
If you haven't yet, you should
```
sudo apt-get update
```

---

### Post by desertphotog on 2008-01-11
Thank you for the reply offaxis.  I'll update and try to do a download after work today.  I am really liking this ubuntu a lot.  All thats left  is to get WiFi working-  itsabitch!

---

