---
title: "hi i've been cheching with rkhunter and i came up with some &quot;irregullar warnigs&quot;...."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-07
hi I run rk hunter 
and i've been through some irregular warnigs...:
"
Checking system commands...

Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chow
    	....
    	/bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/dif
    ....
    usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ OK ]
	....
	
  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ Warning ]
    Checking for group file changes                          [ Warning ]
    Checking root account shell history files                [ None found ]
.....
  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]

...
  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]

...
System checks summary
=====================

File properties checks...
    Files checked: 122
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0
....
"

any ideas what this might be?

---

### Post by OrangeCrate on 2007-11-07
> **someoneouthere said:**
> 
any ideas what this might be?

If you search the forums for "rkhunter", you'll notice a lot of recent posts regarding warnings.

Take a look at this thread, particularly post #9 for a possible fix.

[http://ubuntuforums.org/showthread.php?t=604068&highlight=%2Fusr%2Fbin%2Fldd+rkhunter](http://ubuntuforums.org/showthread.php?t=604068&highlight=%2Fusr%2Fbin%2Fldd+rkhunter)

Worked for me.

---

