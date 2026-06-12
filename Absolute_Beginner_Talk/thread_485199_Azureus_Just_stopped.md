---
title: "Azureus Just stopped"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-06-26
hello,
I just wanted to try azuerus and it didn't work. I didn't upgrade anything and frostwire still works and both used to work before. here's my terminal output

wale@wale-linux-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0639d02, pid=11814, tid=3085424304
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid11814.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
wale@wale-linux-desktop:~$ 

Thanks i use christmas edition 6.10

---

### Post by Rocket2DMn on 2007-06-26
in your home folder, show hidden files (ctrl+h) and open the .azureus folder.  Delete your logs - this seems to solve a lot of problems.

---

### Post by adewale on 2007-06-26
fixed just ran it as super user and quickly changed the languauge and its working hope someone find it useful

---

