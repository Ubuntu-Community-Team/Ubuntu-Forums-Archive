---
title: "Using the list command"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-08-04
Hi everyone,
if I use the ls -ail command I get files with '.' preceding
and at the top there is only '.' in the first line and
'..' in the second.

what do these mean?
Ta in advance

---

### Post by 5-HT on 2006-08-04
. is the directory
.. is the parent directory

For a demo, from your home directory try
```
 ls 
```
```
 ls . 
```
```
 ls .. 
```
and compare the results.

---

### Post by carverj on 2006-08-04
So if the filename has a dot in front such as 
'.FILENAME' does that mean that the file is hidden?

aaaand

What is the sftp command to upload multiple files
and what is the sftp command to download multiple files?

Thanks for such a quick response, considering I was posting to demonstrate to a new linux user how quick these forums are!!

---

### Post by it.henrik on 2006-08-04
from man sftp

 put [-P] local-path [remote-path]
             Upload local-path and store it on the remote machine.  If the
             remote path name is not specified, it is given the same name it
             has on the local machine.  local-path may contain glob(3) charac&#8208;
             ters and may match multiple files.  If it does and remote-path is
             specified, then remote-path must specify a directory.  If the -P
             flag is specified, then the file’s full permission and access
             time are copied too.

if you want a good gui tool I would recommend you to take a look at filezilla.

---

