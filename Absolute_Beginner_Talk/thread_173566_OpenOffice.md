---
title: "OpenOffice"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-10
When I first installed Ubuntu OpenOffice worked fine.
After a week of not using OpenOffice for anything I tried to use it and none of it will open.
I try to open and the taskbar icon will show with a waiting mouse pointer and then it just disappears.

This is true for Calc, Writer, Base, Math...

Any ideas?

---

### Post by kingmonkey on 2006-05-10
type oowriter2 in console and paste the output here

---

### Post by GaFFy on 2006-05-10
[QUOTE=kingmonkey]type oowriter2 in console and paste the output here[/QUOTE]

oowriter2 doesnt do anything but ooffice Calc does:

[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav aldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeExce ption'
/usr/lib/openoffice/program/soffice: line 233: 12340 Aborted                 "$s d_prog/$sd_binary" "$@"

** (process:12327): WARNING **: Unknown error forking main binary / abnormal ear ly exit ...
gaffy@gafserv:~$ ooffice Calc
[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
/usr/lib/openoffice/program/soffice: line 233: 12366 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:12353): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by GaFFy on 2006-05-10
[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav aldx failed!

Nevermind I figured it out.
Somehow /home/<user>/.openoffice.org2 became owned by root

fix:
sudo chown -vR <user>:<group> /home/<user>/.openoffice.org2

Thanks for leading me in the right direction! 8)

---

