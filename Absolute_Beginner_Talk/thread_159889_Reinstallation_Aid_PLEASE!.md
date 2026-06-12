---
title: "Reinstallation Aid PLEASE?!"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by livinlinkin on 2006-04-13
Hi,

I've really enjoyed Ubuntu, but my enjoyment might have caused me to negatively alter system files. I was wondering if anybody could help this inexperienced person in reinstalling/repairing/restoring Ubuntu to its default installation state. Thanks. ;)

---

### Post by taurus on 2006-04-13
If you need to restore or repair your system, you first need to describe what you did to it and what's wrong with it!  The only time you can screw up your system if you log in as root or use the sudo command without regarding the consequences.  But if you screw up your home account, just create another one and delete the screw up one...  ;)

---

### Post by Mustard on 2006-04-13
There are a lot of tips I could give you if you are an incurable tinkerer (as I am), and simply can't go a day without breaking something on a perfectly working system. :)

1. Make backups of your system when you get it to a state that you think is 'perfect', then start tinkering. :)  (Use tools like mondo, partimage, sbackup etc. to make backups)

2. Keep your /home folder on a separate partition, so that when you do reinstall, you can choose to mount that partition without formatting during the install, and you will retain all your user settings from one install to the next.

3. Run two installs of Ubuntu, a 'testing' installation and a 'working' installation.  One that you play with and one that you never do anything to, until you are sure of what you are doing.  You can break the 'testing' installation as much as you want, and the lessons learned on the 'testing' installation can then be transferred to the 'working' installation.

What are the specifics of your problem that you are having currently?

---

### Post by livinlinkin on 2006-04-13
I'm going to go insane, honestly. I've tried for a week to install Bon Echo, and then FF 1.5. I think I've sufficiently screwed up the program files. Here are among the error messages I've gotten, or are currently getting.

/opt/firefox/run-mozilla.sh: line 131: 9326 Segmentation fault "$prog" ${1+"$@"}

(type "firefox" in the terminal")

XML Parsing Error: xml processing instruction not at start of external entity
Location:chrome://global/content/commonDialog.xul
Line Number 1, Column 1:

(manually execute FF application)

E: firefox: subprocess post_installation script returned error exit status 1

(reinstall firefox from synaptic package manager)

Sorry if this is just plain weird. I don't understand software too well.](*,)

---

