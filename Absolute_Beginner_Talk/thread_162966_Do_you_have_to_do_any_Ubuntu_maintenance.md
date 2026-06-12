---
title: "Do you have to do any Ubuntu maintenance?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Dusk2k2 on 2006-04-20
Are there things you need to do in Ubuntu, like you have to do in windows.  Examples such as defragmenting, running spyware, etc...

---

### Post by unbuntu on 2006-04-20
no...no defragment (shouldn't this be in the wiki by now :))
use clamAv for virus checking

---

### Post by bionnaki on 2006-04-20
spyware - no
viruses - you can, but you really dont need to.
rootkits - you can (sudo apt-get install chkrootkit)
defrag - no

as for "maintaince" - periodically do sudo apt-get update and sudo apt-get upgrade to receive any updates

thats all really

---

### Post by nocturn on 2006-04-20
[QUOTE=bionnaki]
as for "maintaince" - periodically do sudo apt-get update and sudo apt-get upgrade to receive any updates
[/QUOTE]

Or set up update-manager to notify you when new updates are out.

---

### Post by patrick295767 on 2006-04-20
[QUOTE=Dusk2k2]Are there things you need to do in Ubuntu, like you have to do in windows.  Examples such as defragmenting, running spyware, etc...[/QUOTE]
  
I am running daily 
apt-get upgrade 
and : e2fsck -p -f /dev/hdaxx
(unmounted disks & linux os )...

***
Greetz

---

### Post by zugu on 2006-04-20
What if I want to check my disks for filesystem errors, bad sectors etc. ? Is there any ScanDisk equivalent?

---

### Post by htinn on 2006-04-20
Every day I check my ~/arcs folder to see whether it's big enough to do a CDR/DVDR backup yet. I check out the System Logs, make sure my panel icons are still arranged properly, tweak my mouse motion settings a bit (it never quite feels right), check for a new version of Wine, let the Updater do its thing, etc.

Other than that, it's just about a hands-free system.

---

### Post by patrick295767 on 2006-04-20
[QUOTE=zugu]What if I want to check my disks for filesystem errors, bad sectors etc. ? Is there any ScanDisk equivalent?[/QUOTE]
this : e2fsck -p -f /dev/hdaxx

---

### Post by htinn on 2006-04-20
Make sure to umount those devices before you e2fsck them. :)

---

### Post by Borniet on 2006-04-20
And... if you install or upgrade some stuff regularly, you may want to do a 'sudo apt-get autoclean' to remove the downloaded packages that are no longer needed.
As for the e2fsck: every 30 boots, the system checks it itselfin the bootprocess.

---

### Post by uantuzri on 2006-04-20
if you want to clean your system try this:

[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)

---

