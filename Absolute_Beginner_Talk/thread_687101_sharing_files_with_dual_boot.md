---
title: "sharing files with dual boot"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by tophue on 2008-02-03
Basically I want to dual boot XP and ubuntustudio on my laptop. I want to be able to have my music and other files accessible to both OSs. How should I go about setting this up with out screwing p my computer?

---

### Post by charding on 2008-02-04
Mount your ntfs partition on linux when using linux to listen to music.

I think there are windows programs that will mount ext2/3 fs but not sure, I guess it all depends on the fs that you're using. An alternative to that is the ntfs kernel drivers that 'may' let you write to ntfs (windows) drives through linux although I'm not sure if this is possible yet.

I would say use linux and read/write from linux on a ntfs drive (if you can do what I mentioned above)

---

### Post by oedha on 2008-02-04
sudo apt-get update
go to applications - Add/Remove
search for NTFS on all available applications
mark and install it then activate it...

your NTFS partition can be shared for both
~E~

---

### Post by Michl on 2008-02-04
There is a good set of directions under Mount Windows on
[www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

It's a great resource.

---

