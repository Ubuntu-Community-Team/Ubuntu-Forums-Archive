---
title: "which nfs packages"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Tobitas on 2006-03-23
I have two linux boxes. one running suse, the other one xubuntu. For file sharing between them I would like to set up the xubuntu machine as nfs server, the suse box as nfs client. What packages do I have to install from the repositories under xubuntu to get the nfs server working? 
Thanks

---

### Post by eltaito on 2006-03-23
I have an home server running as an nfs server and a laptop running nfs as a client and its working great.  As far as I remember your going to need nfs and portmap on both machines but its more complicated than just installing the software.

Ubuntu has a wiki page on the subject here: [https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29]("https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29")

but I had better luck following sourceforge's nfs how to:

[http://nfs.sourceforge.net/nfs-howto/]("http://nfs.sourceforge.net/nfs-howto/") 

one thing to keep in mind...I followed the how-to's and still couldn't get everything to work until I realized that I hadn't started all of the daemons involved so I restarted the server then the client machines and it worked out great

---

