---
title: "Add/Remove Software app not working"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by sleep furious idea on 2007-10-30
-new user.
-recently upgraded to gutsy gibbon.

Under the applications menu, the 'add/remove software' application isn't working.
I click on it to open, it opens for a second then crashes so I can't even see what is wrong.

Any ideas as to what it could be? 
Is it a known problem with gutsy gibbon?
Couldn't find it while searching if it was.

Thanks
sfi

---

### Post by skymera on 2007-10-30
ive had no problems, as faer as ive seen, no one else has.

try synaptics:

system > admin > synaptics package manager :wink:

---

### Post by AgentXSmith on 2007-10-30
I'm not trying to hijack this thread but I'm having a problem accessing the synaptics manager.  Every time I try to open it I get this message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried to cut and paste dpkg --configure -a into the terminal window but I get message back that says I need superuser priviledge, whatever that means.

BTW, this all started after I tried to download limewire software (it froze up midway through applying the updates).

---

### Post by Austin17 on 2007-10-30
> **AgentXSmith said:**
> I'm not trying to hijack this thread but I'm having a problem accessing the synaptics manager.  Every time I try to open it I get this message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried to cut and paste dpkg --configure -a into the terminal window but I get message back that says I need superuser priviledge, whatever that means.

BTW, this all started after I tried to download limewire software (it froze up midway through applying the updates).

Try putting sudo before the command, that will give you root (admin) access.

---

### Post by Maestro23 on 2007-10-30
> **AgentXSmith said:**
> I'm not trying to hijack this thread but I'm having a problem accessing the synaptics manager.  Every time I try to open it I get this message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried to cut and paste dpkg --configure -a into the terminal window but I get message back that says I need superuser priviledge, whatever that means.

BTW, this all started after I tried to download limewire software (it froze up midway through applying the updates).

In terminal:

> sudo dpkg --configure -a

sudo apt-get update


---

### Post by AgentXSmith on 2007-10-30
Thank you Austin and Maestro, the command worked and I'm able to access the synaptic package manager.  The problem was with a Java5 package.  i tried to remove but it wouldn't allow me to so I just marked and applied an upgrade.  Seems to work fine--thanks again.

---

