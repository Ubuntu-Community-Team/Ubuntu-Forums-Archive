---
title: "rc.d no such file or directory"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-17
hi im trying to start the nfserver. I typed the command in blue and then it said "No such file or directory"

then I typed the command in red without rc.d and then the nfs starter failed!!!

obviously i will need to install it but can someone pls explain to me if it is really necessay. pls could url explain it in laymans terms.

[COLOR="DarkOrchid"]Thank u in advance[/COLOR]
 
bulletproof@Bulletproof:~$ [COLOR="Blue"]/etc/rc.d/init.d/nfs-kernel-server start[/COLOR]
bash: /etc/rc.d/init.d/nfs-kernel-server: No such file or directory
bulletproof@Bulletproof:~$ [COLOR="Red"]/etc/init.d/nfs-kernel-server start[/COLOR]
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "*:/nfsshare".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                         [ ok ]
 * Starting [COLOR="Orange"]rpc nfsd...                                                  [fail][/COLOR]
bulletproof@Bulletproof:~$

---

### Post by ubuntuuser on 2006-10-17
You need root privileges to start this service. Try ```
sudo /etc/init.d/nfs-kernel-server start
``` instead.

---

### Post by cinderella on 2006-10-17
> **ubuntuuser said:**
> You need root privileges to start this service. Try ```
sudo /etc/init.d/nfs-kernel-server start
``` instead.

thanks for a quick reply but is it imperative to install rc.d

---

### Post by cinderella on 2006-10-17
this is the error it gives me now :its highlighted in red and the command is in blue

bulletproof@Bulletproof:~$ [COLOR="Blue"]sudo /etc/init.d/nfs-kernel-server start[/COLOR]
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "146.230.192.49:/nfsshare".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
                                                                         [ ok ]
 * Starting rpc nfsd...                                                  [ ok ]
 [COLOR="Red"]* Starting rpc mountd...                                                [fail][/COLOR]
bulletproof@Bulletproof:~$

---

### Post by bsussman on 2006-10-17
> **cinderella said:**
> thanks for a quick reply but is it imperative to install rc.d

Why?  There are not a lot of [k,ed]ubuntu systems that use rc.d - the debian organization is init.d for all scripts, and rcX.d for run levels where X is the runlevel (1 through 6 standard) where scripts are softlinked iinto the proper runlevel directories.

---

### Post by cinderella on 2006-10-17
> **bsussman said:**
> Why?  There are not a lot of [k,ed]ubuntu systems that use rc.d - the debian organization is init.d for all scripts, and rcX.d for run levels where X is the runlevel (1 through 6 standard) where scripts are softlinked iinto the proper runlevel directories.

so do u suggest i use it???

---

### Post by bsussman on 2006-10-17
Sorry - my apologies - I got the word order wrong when I read your question.

No I do not suggest you use the directory.  There are distributions that do use it - BSD I believe is one but a directory called rc.d does not normally play any role in an ubuntu system. 

I think it is important but not absolutely necessary, if you are going to mess around with, use or otherwise interact with the init scripts to understand their structure and purpose.  Try [http://www.debian.org/doc/debian-policy/ch-opersys.html](http://www.debian.org/doc/debian-policy/ch-opersys.html) section 9.3. 

Generally, one does not operate directly on these scripts unless one needs to reinitialize some subsystem (networking, nfs, dhcp, whatever) which is easy to do since the convention for these scripts is a standard set of operations (start/stop/restart/reload config and so on).  For instance, I type 'sudo /etc/init.d/networking restart' when I reconfigure my network at the commandline.

I doubt your mountd problem is connected with init.d issues.  More likely to be your mountd config.  Is there anything in your logs?

---

### Post by cinderella on 2006-10-18
> **bsussman said:**
> Sorry - my apologies - I got the word order wrong when I read your question.

No I do not suggest you use the directory.  There are distributions that do use it - BSD I believe is one but a directory called rc.d does not normally play any role in an ubuntu system. 

I think it is important but not absolutely necessary, if you are going to mess around with, use or otherwise interact with the init scripts to understand their structure and purpose.  Try [http://www.debian.org/doc/debian-policy/ch-opersys.html](http://www.debian.org/doc/debian-policy/ch-opersys.html) section 9.3. 

Generally, one does not operate directly on these scripts unless one needs to reinitialize some subsystem (networking, nfs, dhcp, whatever) which is easy to do since the convention for these scripts is a standard set of operations (start/stop/restart/reload config and so on).  For instance, I type 'sudo /etc/init.d/networking restart' when I reconfigure my network at the commandline.

I doubt your mountd problem is connected with init.d issues.  More likely to be your mountd config.  Is there anything in your [COLOR="Red"]logs[/COLOR]?


Thank u again for replying. I would like to get my rc.d working but just dont know how to get this done. 
Im completely new to this OS so pls explain to me  what u mean by logs? Pls help me because i need to get this working by tonight!!!!

Another qusetion I have is relatedt to shared folders. I'm currently working with a fingerprint board and to design applications for the board i require nfs to talk to it. Anyway this board came with an installation cd wihch contained various cross compilers, library files, environment variables, and two working directories: /nfsshare and /mnt/ramdisk
I found /nfsshare under Admistration--->Shared Folders but when I typed the following command in the terminal it gave me an error:

```
bulletproof@Bulletproof:~$ ls -l /nfsshare
ls: /nfsshare: No such file or directory
```

Pls how do I list the files from my pc running ubuntu i.e my host


im begging u to help....pls](*,)

---

