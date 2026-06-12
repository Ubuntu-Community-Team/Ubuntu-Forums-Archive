---
title: "Deleting a print job in XP that was sent from Ubuntu?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by ed_d on 2005-11-20
This is a follow on to the issue that many are having in creationg a printer that is shared by XP.
How does one delete a job that has been submitted to the shared XP printer? I have no jobs present on my Ubuntu box, but there is a job that cannot be deleted on the XP box, tried to "cancel" the job, shows "deleting" but nothing happens. Tried to even power off, reboot, still the job is there.
Any help would be great.

---

### Post by apjone on 2005-11-20
man lprm

eg
do 'lpstat' to get the job number then 
lprm -p[PRINTERNAME] [jobnumber]

---

