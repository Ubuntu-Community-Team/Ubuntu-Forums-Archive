---
title: "MSSQL Wine and a New user"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Hunnicutt on 2007-10-11
I am trying to get mssql working with wine on my fiesty box. I am trying to connect a VB app with it. I am very new to Linux and feeling my way around. I have tried this help file I found. 

  >  Native ODBC drivers have been reported to work for many types of databases including MSSQL and Oracle. In fact, some like MSSQL can only be accessed on Linux through a Winelib app. Rather than just copying DLL files, most ODBC drivers require a Windows-based installer to run to properly configure things such as registry keys.

In order to set up MSSQL support you will first need to download and run the mdac_typ.exe installer from microsoft.com. In order to configure your ODBC connections you must then run CLICONFG.EXE and ODBCAD32.EXE under Wine. You can find them in the windows\system directory after mdac_typ runs. Compare the output of these programs with the output on a native Windows machine. Some things, such as protocols, may be missing because they rely on being installed along with the operating system. If so, you may be able to copy missing functionality from an existing Windows installation as well as any registry values required. A native Windows installation configured to be used by Wine should work the same way it did when run natively.

Types successfully tested under wine:

DB Type	Usefulness
MS SQL	100%

But when I try to run mdac_typ.exe I get an error about Missing Dependancies. It is claiming I need Interent Explorer 4.01 SP1 or higher. Can anyone advise me on my next step (and the others). Thanks in advance for any help.

If this is the wrong place for this I am also sorry and feel free to move it.

---

### Post by Hunnicutt on 2007-10-11
Anyone?

---

### Post by onegreenparker on 2008-01-17
I know it's and old post but here is an answer anyway.....

I had a similar problem with an MDAC and the only way I got around it was to install IE6.

Now if anyone knows how I can connect to a MSSQL database let me know, at this stage I get the following output on the console:

```

err:ole:CoGetClassObject class {ecabb0c0-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c0-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1

```

and an error:

```

OLE error 80004005

```

:confused::confused::confused:

---

