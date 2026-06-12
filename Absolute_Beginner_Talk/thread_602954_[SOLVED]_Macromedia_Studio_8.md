---
title: "[SOLVED] Macromedia Studio 8"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-11-04
I have tried installing this using wine, but each time I get a whole load of errors. (I'll post these shortly)

Does anyone know how I can get Studio 8 to work and with what version of wine?

Cheers :)

edit:

this is the error I get when I run wine install.exe:

> Could not load Mozilla. HTML rendering will be disabled.
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
wine: '/home/matt/.wine' created successfully.
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library NetIO.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library icuuc30.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library LIBEAY32.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library SSLEAY32.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library Workspace.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library MFC71U.DLL (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"Z:\\home\\matt\\dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\matt\\dreamweaver.exe" failed, status c0000135


IS this problem solvable?

edit x2

I copied across the dreamweaver .dll files but this didn't work. I get a message sayign I need to reinstall DW.

---

### Post by Maestro23 on 2007-11-04
> **spamzilla said:**
> I have tried installing this using wine, but each time I get a whole load of errors. (I'll post these shortly)

Does anyone know how I can get Studio 8 to work and with what version of wine?

Cheers :)

edit:

this is the error I get when I run wine install.exe:



IS this problem solvable?

You check the Wine App DB: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4318](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4318)

---

### Post by richiewrt on 2007-11-04
I had dreamweaver installed on Ubuntu 7.10 at one time for about a day. Everything seemed to work, but looked and felt horrible so I ended up just dual booting for studio 8 apps. I can't remember where I found the walkthrough to install them, but it is possible. Had to copy a bunch of files from my windows partition to get it to work.

good luck getting it installed and hopefully you will be happier with the results than I was. I went back to using it on windows just because it looked more polished but your mileage may vary.

---

### Post by spamzilla on 2007-11-04
Ah yeah it says it can't be installed. I have dreamweaver8 here, so I'll see if I can install it on wine0.9.42...earlier it wouldn't so I'm not too hopeful.

---

### Post by spamzilla on 2007-11-04
> **richiewrt said:**
> I had dreamweaver installed on Ubuntu 7.10 at one time for about a day. Everything seemed to work, but looked and felt horrible so I ended up just dual booting for studio 8 apps. I can't remember where I found the walkthrough to install them, but it is possible. Had to copy a bunch of files from my windows partition to get it to work.

good luck getting it installed and hopefully you will be happier with the results than I was. I went back to using it on windows just because it looked more polished but your mileage may vary.

I tried that file copying method earlier and I got tones of errors.

Using wine 0.9.42 got me the same results as listed above :(

---

### Post by spamzilla on 2007-11-04
I got DW working, but ya it doesn't look very good. I may have to keep my XP partition after all :/

(I used this guide ([http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)) and copied all the files inside the DW programs files into the wine system32 file.

Thanks all

---

### Post by mdpalow on 2007-11-04
Problem solved:

[http://ubuntuforums.org/showthread.php?t=596349]("http://ubuntuforums.org/showthread.php?t=596349")

Look for my (mdpalow) posts.

---

