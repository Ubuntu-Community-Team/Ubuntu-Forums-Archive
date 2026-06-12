---
title: "E: tzdata: error 127 when Updating"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2008-04-04
Hi, I've got some updates coming into my computer, but they can't install, returning the error: 
E: tzdata: subprocess post-installation script returned error exit status 127

I've looked about on the forum, and have found people with error 1, but nobody with 127. Is there a way I can sort this and install my updates without full reinstallation of Ubuntu? I'm on Gustsy.
Thank you

---

### Post by spydon on 2008-04-04
Try this in a terminal ```
sudo dpkg --configure -a
``` or this ```
sudo apt-get -f install
```

---

### Post by D_D_T on 2008-04-04
sudo dpkg --configure -a
came back with:

Setting up tzdata (2008a-0ubuntu0.7.10) ...
/var/lib/dpkg/info/tzdata.config: 319: head: not found
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata

sudo apt-get -f install
came back with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevent1 libboost-thread1.34.1 tsocks libboost-date-time1.34.1
  armagetronad-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2008a-0ubuntu0.7.10) ...
/var/lib/dpkg/info/tzdata.config: 319: head: not found
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

pants! :)

---

### Post by spydon on 2008-04-04
Try to create this file then maybe... /var/lib/dpkg/info/tzdata.config

---

### Post by D_D_T on 2008-04-04
Thanks for the help. The file /var/lib/dpkg/info/tzdata.config actually exists though, and I can read it in text editor too, so I don't know if making another file would help.

---

### Post by spydon on 2008-04-04
```
sudo apt-get remove --purge tzdata
``` and then ```
sudo apt-get install tzdata
``` and then try to update again

---

### Post by D_D_T on 2008-04-07
This came back with 

After unpacking 6283kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
/tmp/tzdata.config.64831: 319: head: not found
tzdata failed to preconfigure, with exit status 127
Selecting previously deselected package tzdata.
(Reading database ... 94393 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2008a-0ubuntu0.7.10_all.deb) ...
Setting up tzdata (2008a-0ubuntu0.7.10) ...
/var/lib/dpkg/info/tzdata.config: 319: head: not found
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

when I tried to reinstall tzdata. I'm a little worried now!

---

### Post by D_D_T on 2008-04-07
just tried marking tzdata for reinstallation in Synaptic, but came back with error 127 and wouldn't do it. 
Weirdly though, it said that the package was there. What's going on?

---

### Post by spydon on 2008-04-08
This is really weird! 
Was ```
sudo apt-get remove --purge tzdata
``` successful?
Try this after that command if it works:
```
sudo cat /var/lib/dpkg/info/tzdata.config
```

---

### Post by D_D_T on 2008-04-08
Yeah this is really strange.

The purge seemed to have worked.

sudo cat /var/lib/dpkg/info/tzdata.config came back with: 

cat: /var/lib/dpkg/info/tzdata.config: No such file or directory

Thank you for sticking with this spydon. Your help is much appreciated.

---

### Post by D_D_T on 2008-04-09
Boo! Actually, it's still not working. It seems that the purge worked, but when I try and update, I get hit with the same error 127 once again.
:(

---

### Post by spydon on 2008-04-10
Do you have wine installed, because I found a bug filed for that error.
can you try these:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade
```

---

