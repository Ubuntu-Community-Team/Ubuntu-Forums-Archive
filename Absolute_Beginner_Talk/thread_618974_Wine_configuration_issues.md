---
title: "Wine configuration issues"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by manij on 2007-11-21
Hi,

I'm running Dapper. Looks like wine is installed with the package. I'm able to run Tytools and process files and all that. 

[B][I]XXXX@XXXX-desktop:~$ wine /home/XXX/Desktop/C_drive/TyTool10r4/Tytool10r4.ex e
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.[/I][/B]

See error message, but the program starts up just fine!


However, I'm not able to install any other programs like itunes. 

[B][I]xxxx@xxxx-desktop:~$ wine /home/xxxx/Desktop/C_drive/iTunes743Setup.exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Command Line:
Information on cabinet file 'C:\iTunes743Setup.exe'
   Total length of cabinet file : 51218315
   Number of folders in cabinet : 1
   Number of files in cabinet   : 5
   Cabinet set ID               : 0
   Cabinet number in set        : 0
   RESERVE area in cabinet?     : no
   Chained to prev cabinet?     : no
   Chained to next cabinet?     : no

fdintCABINET_INFO
  next cabinet     =
  next disk        =
  cabinet path     = C:\
  cabinet set ID   = 0
  cabinet # in set = 0 (zero based)

fdintCOPY_FILE
  file name in cabinet = iTunes.msi
  uncompressed file size = 23440384

FDICopy() failed: code 11 [User aborted] [/I][/B]

I have tried going thro the documentation. didn't help much.

Help

Mani

---

