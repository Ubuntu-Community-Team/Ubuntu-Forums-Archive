---
title: "Updating Sources List..Wierd Error?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-17
Upon updating my sources list this morning, I ran into this problem: W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181


This was when I downloaded swiftfox 3.0 V5..Should I be concerned?  I also deleted the extra (I think) W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages) from my sources list...

---

### Post by Oldsoldier2003 on 2008-03-17
> **sox fan Matt said:**
> Upon updating my sources list this morning, I ran into this problem: W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181


This was when I downloaded swiftfox 3.0 V5..Should I be concerned?  I also deleted the extra (I think) W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages) from my sources list...

it wont stop you from installing, you just don't have the functionality of verifying that the file is genuine and coming from where it says it is because they key is missing. try reinstalling the repo and key.

---

