---
title: "Need Help Removing Mint4Win"
date: 2011-12-01
forum: Any Other OS
---

### Post by michaeljwjr on 2011-12-01
Every time I try to uninstall mint4win I get an error telling me It can't find bcdedit.exe 

A copy of my log:

> Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 560, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 744, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {3d105d81-583d-11df-a6cb-f73c2d996182} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.

I Would like to run mint through windows until I am comfortable enough to set up a dual boot, but if I can't even get this working I won't be moving to the next. 

Any help would be greatly appreciated, thank you for even reading this far.

---

### Post by bcbc on 2011-12-02
See this thread for a solution: [http://ubuntuforums.org/showthread.php?t=1871823](http://ubuntuforums.org/showthread.php?t=1871823)

Edit... actually I don't think that's your issue. I believe that for whatever reason the Mint4Win entry has already been removed from the BCD store and so the uninstaller is failing. You should follow the instructions to manually uninstall in this case:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

