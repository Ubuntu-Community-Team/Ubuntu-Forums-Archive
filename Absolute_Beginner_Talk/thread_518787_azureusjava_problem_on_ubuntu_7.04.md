---
title: "azureus/java problem on ubuntu 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by kmcq on 2007-08-06
hey guys i grabbed azureus from the ubuntu add/remove app and it seemed to install fine, however when i try to start it up it brings up the language selection window then crashes, so i tried running it from console and i got a java error...

```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4614172, pid=17453, tid=3084270480
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid17453.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

any ideas about what might be cuasing this, i have the java 5.0 runtime, and the 6.0 webstart, could that be the problem?


UPDATE: i decided to go back to add/remove and double check that i had the proper java materials for running azureus, i did not have the java 5.0 console and the 6.0 console, after adding and installing those, azureus seems to work!

---

### Post by Steve1961 on 2007-08-06
Try uninstalling azureus and then install using the alternative method from the edgy guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

Works fine for me

---

### Post by 1/0 on 2007-08-22
This did the trick for me:

```
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*
```

---

### Post by kieranjones on 2007-08-23
Hey,

I had the exact same problem as this with Azureus, and solved it all just fine without following any manual download stuff, I just installed from the "Add/Remove Programs" thing.

I installed the Java 5 things again (I'd removed them thinking I didn't need both) and then followed the steps by 1/0

```
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*
```

That solved it just fine, I'm back downloading 100% files via BitTorrent again (haha) :)

Thanks guys.

---

### Post by mspendlo on 2007-08-29
No joy for me the official way :

[https://help.ubuntu.com/community/AzureusHowTo](https://help.ubuntu.com/community/AzureusHowTo)

even with the mention edits here (JRE 1.6).

Had to resort to installing the tarball manually. Works a treat :

[http://ubuntuforums.org/showpost.php?p=3273714&postcount=106](http://ubuntuforums.org/showpost.php?p=3273714&postcount=106)

---

