---
title: "Workspaces Corrupted"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-14
I beleive there is something wrong with my workspaces, as I can't add more to them. I tried doing this:

tim@tim-desktoplinux:~$ gconftool-2 --direct \
> config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
> set /apps/metacitiy/gerneral/num_workspaces 3
You must specify a config source with --config-source when using --direct
tim@tim-desktoplinux:~$ gconftool-2 --direct \
> --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
> --type int \
> --set /apps/metacity/general/num_workspaces 3
Resolved address "xml:readwrite:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
Error setting value: Unable to store a value at key '/apps/metacity/general/num_workspaces', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf
tim@tim-desktoplinux:~$ 

as you can see it didn't work. Is there a way to add more? 

ts51

---

### Post by diatribe on 2007-06-14
I'm pretty sure gnome has a gui to do this in system->preferences

---

### Post by ts51 on 2007-06-14
Got them back, but when I switch everything disappears except my wallpaper.

---

