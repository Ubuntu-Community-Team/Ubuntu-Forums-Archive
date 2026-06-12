---
title: "Thunderbird will not what-so-ever configure properly???"
date: 2005-09-11
forum: Bug Reports / Support
---

### Post by AgentMayland on 2005-09-11
I've been trying for days to configure thunderbird to run, if I install and run the icon it just kills.

When I use the:

System->Administration->Add Application
System->Administration->Synaptic Package Manager
or when I install with "apt-get" through term

I get:
```

seth@InsoBox:~$ mozilla-thunderbird
selected locale: en-US
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159: 10909 Segmentation fault      "$prog" ${1+"$@"}
seth@InsoBox:~$

```

or some other similar error always a segmentation fault.

Under term I get this when installing with "apt-get"

```

seth@InsoBox:~$ sudo apt-get install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mozilla-thunderbird-offline mozilla-thunderbird-typeaheadfind
  mozilla-thunderbird-inspector mozilla-thunderbird-enigmail
Recommended packages:
  xprt-xprintorg
The following NEW packages will be installed:
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.9MB of archives.
After unpacking 31.9MB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 67254 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.0.6-0ubuntu05.04_i386.deb) ...
Successful preinst
Setting up mozilla-thunderbird (1.0.6-0ubuntu05.04) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

done.

```

---

### Post by josir on 2005-09-14
Hi, I got the same error but I didn't get segmentation fault.
Did you find what's wrong ?

---

### Post by AgentMayland on 2005-09-15
[QUOTE=josir]Hi, I got the same error but I didn't get segmentation fault.
Did you find what's wrong ?[/QUOTE]

Yeah I went and removed everything completely and reinstalled and went to the Thunderbird Profile Manager setup my profile then went to run Thunderbird and got it fixed. works great@!

---

### Post by tbc on 2005-10-03
By "remove everything" I assume you mean ~/.mozilla-thunderbird/. I just renamed it to get it out of the way, uninstalled via synaptic and then ran 'dpkg -i mozilla-thunderbird'. No joy. I'm stumped by the same problem as josir.

---

### Post by tbc on 2005-10-04
FWIW, I uninstalled mozilla-thunderbird via synaptic, then I installed thunderbird 1.0.7 manually in /opt/thunderbird/. Now it's working fine.

---

### Post by nix4me on 2005-10-14
i had problems trying to use my old thunderbird settings from hoary.  I tried to keep the dir from /home and install thunderbird  and everything broke.

I removed it all, and re-installed and all is fine now.

nix

---

