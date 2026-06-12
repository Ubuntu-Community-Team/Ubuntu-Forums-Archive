---
title: "[SOLVED] azureus crashes on startup in kubuntu gusty amd64"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by malathion on 2008-02-19
After a search of the forums it seems that I am not the only person with this problem, however I did not have much luck trying the other suggestions. As you can see from the log Azureus is still using IcedTea although I have installed the sun-java6 plugin.

ryan@ryan-desktop:/media$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Tue Feb 19 16:45:10 EST 2008  Data Missing /tmp/azupdater_1.8.3.zip
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b8dda911e11, pid=22364, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/ryan/.azureus/hs_err_pid22364.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

Since some suggestions included installing sun java, yet I have already done this, is there anything I have to do to make sure azureus runs in sun java and not iced tea?

---

### Post by mattismyname on 2008-02-20
Maybe it's this issue?  [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/187421](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/187421)

There's a workaround posted on that page.

---

### Post by malathion on 2008-02-20
Hmm... I tried

$ export LIBXCB_ALLOW_SLOPPY_LOCK=1

and got the same error. No dice. :confused:

---

### Post by cozmicharlie on 2008-02-20
You can configure which version of Java to use:
```
sudo update-alternatives --config java

```
I would recommend uninstalling java iced tea and make sure the system is using Sun Java6-jre

---

### Post by malathion on 2008-02-20
Yeah I had set it to use sun java, but it looks like uninstalling icedtea got the job done. Thanks.

---

