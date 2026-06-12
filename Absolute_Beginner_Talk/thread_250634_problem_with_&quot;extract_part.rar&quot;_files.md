---
title: "problem with &quot;extract part.rar&quot; files"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by kolobaki on 2006-09-04
WELL,I HAVE DOWNLOAD A FILM AND IT IS SEPARATED IN parts.
WHEN I TRY TO MAKE EXTRACT OR TO OPEN ONE OF THEM WITH ARK IT SAYS THAT WAS CREATED FAULT AND IT NEEDS PASS. I HAVE THE PASS BUT I DO NOT KNOW HOW I ADD IT.
Can help me anyone?
thx

---

### Post by Turgon on 2006-09-04
Hm, I had this problem once and its solable. 

You need to have the rar-nonfree package installed.

Then you need to open a terminal:

unrar -p<password> <path to filename>

good luck!

---

### Post by kolobaki on 2006-09-04
CAn you give me an accidental example?
when i try it it says:


> UNRAR 3.51 freeware      Copyright (c) 1993-2005 Alexander Roshal

Cannot open Folder.rar
Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  e             Extract files to current directory
  l[t,b]        List archive [technical, bare]
  p             Print file to stdout
  t             Test archive files
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ap<path>      Set path inside archive
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  dh            Open shared files
  ep            Exclude paths from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  inul          Disable all messages
  kb            Keep broken extracted files
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files in specified list file
  o+            Overwrite existing files
  o-            Do not overwrite existing files
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             List all volumes
  ver[n]        File version control
  vp            Pause before each volume
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries


---

