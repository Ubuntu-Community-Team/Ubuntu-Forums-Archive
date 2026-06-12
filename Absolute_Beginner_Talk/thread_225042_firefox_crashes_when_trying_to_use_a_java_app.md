---
title: "firefox crashes when trying to use a java app"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-28
i've followed numerous guides on this forum and this is the output in  command shell window when i try to launch a java app


john@ubuntu:~$ firefox
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1a7ed03, pid=10454, tid=2971171760
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid10454.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success

---

