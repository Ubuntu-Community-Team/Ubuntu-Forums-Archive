---
title: "i can not install updates using ubuntu 11.04"
date: 2011-06-29
forum: Any Other OS
---

### Post by dr.abady on 2011-06-29
hello everyone
im new in ubuntu. i ve just install ubuntu 11.04 and it worked very well, then when i try to check update it gives me this message
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/deb.torproject.org_torproject.org_dists_lucid_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


the second problem is that i can not install any software and when i try to open ubuntu software center 


please help

---

### Post by drs305 on 2011-06-29
The problem is most likely caused by one or more bad downloaded lists. Removing the bad list will fix the problem. The second problem is directly related to the first. When the first is solved, the second one will be as well.

See this post, which should solve your issue. It was posted earlier today and is a frequently-invoked solution:
[http://ubuntuforums.org/showpost.php?p=10995989&postcount=4]("http://ubuntuforums.org/showpost.php?p=10995989&postcount=4")

---

### Post by dr.abady on 2011-06-29
i saw the post and follwed the instruction but the problem is still
Fetched 14.0 MB in 12min 15s (19.0 kB/s)                                                                                                                     
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.torproject.org_torproject.org_dists_lucid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by drs305 on 2011-06-29
Rereading, I see you are using 11.04 and that list is for a lucid package.

Open Synapic, go to Settings, Repositories and find the tab which includes the torproject/lucid reference. It's probably in "Other Software". Untick that entry, as you shouldn't have a Lucid repository running Natty. Then Reload or run "sudo apt-get update" after closing Synaptic.

---

### Post by dr.abady on 2011-06-29
i just tried to check for update and this is appeared
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) lucid InRelease: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by drs305 on 2011-06-29
> **dr.abady said:**
> i just tried to check for update and this is appeared
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) lucid InRelease: The following signatures were invalid: NODATA 1 NODATA 2

The second one will go away when you remove the Lucid repository.

You can add the public key for the first one with this command (the code is the last 8 digits of the error code):
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
```

---

### Post by dr.abady on 2011-06-29
i can not open synaptic package manager
when i try to open this is appeared
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.torproject.org_torproject.org_dists_lucid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

and then the synaptic closed

---

### Post by drs305 on 2011-06-29
OK, try manually editing it. The entry may be in the */etc/apt/sources.list* file or a file in */etc/apt/sources.list.d* folder.

Try sources.list first. When you find the entry, place a # symbol at the start of the line and then save the file. You are looking *all* entries that include a reference to "lucid". The specific one causing the error at the moment is from *torproject.org*
```
gksu gedit /etc/apt/sources.list
```

---

### Post by dr.abady on 2011-06-29
i wrote the code in the terminal this what happened
abady@abady-Satellite-A200:~$ gksu gedit /etc/apt/sources.list

(gedit:2235): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2235): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.SWMOXV': No such file or directory

(gedit:2235): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2235): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.63XTXV': No such file or directory

(gedit:2235): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
abady@abady-Satellite-A200:~$ 


and there was a text file has been openen and i put hte # symbol in the front of the first line and saved it >

and still doesnt work

---

### Post by drs305 on 2011-06-29
> **dr.abady said:**
> i wrote the code in the terminal this what happened
and there was a text file has been openen and i put hte # symbol in the front of the first line and saved it >

and still doesnt work

Was the "first line" of the file you opened the one that contained the 'lucid' entry? It should have looked something like:

> deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
and you change it to:
> # deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

If you aren't sure you did it correctly you can post the contents of the file and we can take a look at it.

**Added:** Was the entry in /etc/apt/sources.list or was it in another file? If it was in /etc/apt/sources.list we can provide you with a 'new' default one to replace the one with the error...

---

