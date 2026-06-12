---
title: "No help for shared folders"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-03-25
Hi

I've got two PCs, host names: roger-old and roger-new, both running Ubuntu 6.06, and connected to the Internet over a shared wireless LAN. I'd like to be able to view the home folder on roger-old on roger-new - so that I can copy folders/files between the two machines.

As far as I can tell, there's a utility under System>Administration, Shared Folders, designed expressly for just this task - the only trouble is I can't work out how to use it, or find any help files. I've got to the point where I've installed NFS on both machines, and can added /home/roger to either machine, but what do I do next? I've tried the help button, but get the response "could not display help, unable to find help files.

Best regards

Roger D

---

### Post by lamalex on 2007-03-26
just go to that tool, add your folders, then on your other machine go to places > network servers, and maneuver yourself to the shares. hopefully that should fix your problem yes?

---

### Post by Roger D on 2007-03-26
Hi

Many thanks for the response. This is what I've done:

On roger-old, I've opened 'Shared Foders' and added /home/roger in the 'Shared foders settings' window.

On roger-new I've done Places>Network servers. This oens a window showing a 'Windows Network' icon, and there seems no way I can find /home/roger' on roger-old.

Best regards

Roger D

---

### Post by cowlip on 2007-03-26
can you try to paste

/etc/init.d/nfs-kernel-server restart

into a terminal and see if it works?

can you ping your machine's IP addresses?  find them out from 'ifconfig' in a terminal, then try 'ping IPADDRESSGOESHERE'.

you might also have better luck with samba, I'm personally not familiar with nfs.

---

### Post by Roger D on 2007-03-26
Well, I tried the first paste, and the result looks a bit dire:

roger@roger-new:~$
roger@roger-new:~$ /etc/init.d/nfs-kernel-server restart
 * Stopping rpc mountd... start-stop-daemon: warning: failed to kill 4753: Operation not permitted
                                                                                  [ ok ]
 * Stopping rpc nfsd... start-stop-daemon: warning: failed to kill 4738: Operation not permitted
start-stop-daemon: warning: failed to kill 4737: Operation not permitted
start-stop-daemon: warning: failed to kill 4736: Operation not permitted
start-stop-daemon: warning: failed to kill 4735: Operation not permitted
start-stop-daemon: warning: failed to kill 4733: Operation not permitted
start-stop-daemon: warning: failed to kill 4732: Operation not permitted
start-stop-daemon: warning: failed to kill 4731: Operation not permitted
start-stop-daemon: warning: failed to kill 4734: Operation not permitted
                                                                                  [ ok ]
 * Unexporting directories for NFS kernel daemon... exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                                  [ ok ]
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "192.168.0.0/255.255.255.0:/home/roger".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                                  [ ok ]
 * Starting rpc nfsd...                                                           [fail]
roger@roger-new:~$

---

