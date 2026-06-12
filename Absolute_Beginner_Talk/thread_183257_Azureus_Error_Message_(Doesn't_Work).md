---
title: "Azureus Error Message (Doesn't Work)"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by michaeljb2005 on 2006-05-27
Azureus dies if I try to use certain menu options or try to select a default language in the configuration wizard.  It leaves me with this error message.  Any thoughts?  By the way I am using java 1.5.

mike@mike-laptop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
# SIGSEGV (0xb) at pc=0xb0700e1c, pid=7514, tid=3084867264
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C [libgtkjni-2.8.so+0x81e1c]
#
# An error report file with more information is saved as hs_err_pid7514.log
#
# If you would like to submit a bug report, please visit:
# [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted

---

### Post by michaeljb2005 on 2006-05-27
The problem is the OSX theme I'm using.  I switched themes and it seemed to be ok.  

Thanks

---

