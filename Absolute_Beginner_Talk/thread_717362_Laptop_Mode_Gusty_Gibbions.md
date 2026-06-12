---
title: "Laptop Mode Gusty Gibbions"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by abdulkaderadel on 2008-03-06
To enable laptop mode: COMPLETE INSTRUCTIONS

Logon as normal.
 System - Admin -  Users - Select ROOT - select Properties - User Priv - Select all.
-Change password for ROOT (anything)

Logoff - sign in as ROOT - System - Admin - User - select root - select properties - user priv - make sure they are still all selected.

In terminal enter                 sudo gedit /etc/default/acpi-support

Scroll down to the bottom where you will see:
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false  

Change "false" to true.

Save Exit.

---

### Post by Buffalo Soldier on 2008-03-06
why do you need to sign in as root?

---

### Post by abdulkaderadel on 2008-03-27
For me it didn't work as my created sign in. Suggested way for any admin moves is "root"

---

