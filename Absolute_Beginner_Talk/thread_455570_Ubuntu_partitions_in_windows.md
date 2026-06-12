---
title: "Ubuntu partitions in windows"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-05-26
Hi, is it possible, and if how do i read ubuntu partitions in windows vista?

---

### Post by taurus on 2007-05-26
You can try using [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by ajmannen on 2007-05-26
Didn't work :(

---

### Post by taurus on 2007-05-26
Do you need to transfer something from Windows to Ubuntu?  You can do that with the LiveCD.

---

### Post by ajmannen on 2007-05-26
I need to transfer loads of things from Ubuntu to Windows

---

### Post by Znupi on 2007-05-26
I think Vista uses something else than NTFS. Correct me if I'm wrong.

---

### Post by taurus on 2007-05-26
> **ajmannen said:**
> I need to transfer loads of things from Ubuntu to Windows

In that case, install ntfs-3g (and ntfs-config) and you can write to ntfs filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by ajmannen on 2007-05-26
the first one didn't work and the second one just stops at HTTP request sent, awaiting respons

[[img]http://bildr.no/thumb/69611.jpeg[/img]](http://bildr.no/view/69611)

---

### Post by taurus on 2007-05-26
You don't need to run both, just one.

```

wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
#   **[COLOR="Blue"]or[/COLOR]**
wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -

```

---

### Post by ajmannen on 2007-05-26
Ok, now it works :D Thanks!

---

