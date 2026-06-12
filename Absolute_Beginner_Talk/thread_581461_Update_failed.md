---
title: "Update failed"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-10-19
Im using gutsy and it says now this today...

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

---

### Post by mikeyphi on 2007-10-19
> **mech7 said:**
> Im using gutsy and it says now this today...

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

Had a look at that site - don't think they have anything for Gutsy yet - so perhaps that's the reason?

---

### Post by bapoumba on 2007-10-19
Which package would you like to install ?

---

### Post by mech7 on 2007-10-19
> **bapoumba said:**
> Which package would you like to install ?

I dont want to install anything only update :p

---

### Post by Dellfan on 2007-10-19
I am betting it is the Avant Window Navigator at:

http//download.tuxfamily.org/syzygy42/dists/gutsy

as I am in the same boat with the same error about the same key. Can't figure out how to import the key.

Can easily disable the repository to avoid the error for now.

---

### Post by Dellfan on 2007-10-19
Just found the fix... maintainer changed his key. The fix is:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

Can read more about Avant at:

[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by mech7 on 2007-10-20
thanks seems to work :D

---

