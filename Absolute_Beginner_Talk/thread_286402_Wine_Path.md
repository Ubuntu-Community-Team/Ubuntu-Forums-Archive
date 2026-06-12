---
title: "Wine Path??"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by klgsx on 2006-10-27
:-(

going to try to keep it short.

whenever i run:
[email]anthony@KLGSX:~/.wine[/email]/drive_c/Program Files/THQ/Company of Heroes$ wine RelicCOH.exe

i get the following errors:

err:module:import_dll Library faultrep.DLL (which is needed by L"C:\\Program Files\\THQ\\Company of Heroes\\Debug.dll") not found

err:module:import_dll Library Debug.dll (which is needed by L"C:\\Program Files\\THQ\\Company of Heroes\\STLPort.dll") not found
all the files are in that directory.

game installed ok..and i know those files are there..

HELP.

thanks

---

### Post by bodhi.zazen on 2006-10-27
Try:```
wine ~/.wine/drive_c/Program\ Files/THQ/Company\ of\ Heroes$\ wine\ RelicCOH.exe
```

or 

```
wine "~/.wine/drive_c/Program Files/THQ/Company of Heroes$ wine RelicCOH.exe"
```

---

