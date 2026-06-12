---
title: "Problem with yaboot in 7.10 on iBook G4 ?"
date: 2007-11-10
forum: Apple PPC Users
---

### Post by carac on 2007-11-10
Clean install of Gutsy on an external Firewire HDD - at some point near the very end the install (from the live cd) gives an error with the result that yaboot is not installed; trying to manually fix it with yabootconfig gives a rather unusual error - has anyone seen the same problem ? (it seems very much that it can not convert from the Linux device name to the open firmware name ...) Is it a known bug ?

---

### Post by pxwpxw on 2007-11-10
> **carac said:**
> Clean install of Gutsy on an external Firewire HDD - at some point near the very end the install (from the live cd) gives an error with the result that yaboot is not installed; trying to manually fix it with yabootconfig gives a rather unusual error - has anyone seen the same problem ? (it seems very much that it can not convert from the Linux device name to the open firmware name ...) Is it a known bug ?

Yes there is a problem with open firmware paths for some external hdd, but also with incorrect partitioning for the bootstrap partition, and depending on system partitions and specs and OS.
Post full info if you want more.

---

