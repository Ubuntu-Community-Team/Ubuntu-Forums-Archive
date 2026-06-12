---
title: "SCSI cd Rom blues"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Brigrat on 2006-01-06
Here is the complete history as best as I can remember it.

The box is an intergraph series 600 server.  Intel pent pro 200 (x2) processors.  6 slot hot swap SCSI raid array
mega raid power console running the SCSI Raid array.
SCSi cd rom utilizing the aspi8 driver group.

First tried to load win 95 then 98.  neither would load as they could not see the cdrom.

tried UBUNTU at first no luck there, same issue could not see the cdrom.

First attmept to load Contrib.org's SME 6.5 server.  Would not see the cdrom.  Then used the rawrite program to make the SME 6.5 boot disk and the OS loaded with out a hitch.  this floppy appears to only work with the SME server os only as I tried to use tha floppy with UBUNTU.  It did not like that very well.

Again tried to load the UBUNTU OS, after learning a few things but have yet to get the right mix of files to start the OS load process.

Barts custom MODBOOT disk seems to be the most effective boot disk as I can modify the files to fit different equipment, not OS's.

The UBUNTU smbootmgr method can not see the SCSi CDROM.  

This is the current delimma :

A.  I can see the CDROM and the files but the OS does not start installing.

B.  I can not see the CDROM at all.

Questions are:

1.	Can the OS install be started from from a command line if I can see the files, and if so how.  Are there any extra files necessary to do this.

2.	SME's boot disk worked for that OS what would be needed to do that for UBUNTU?

Can someone-anyone help me out here.  Is there a command that I can use from the command line to start the install when all I can get to is the cdrom and see the files???????

---

