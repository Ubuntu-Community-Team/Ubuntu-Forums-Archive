---
title: "DVD drive (2. drive), can read audio cd's but not DVD's, and ain't mounted"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-02-10
Hello

Just inserted a second cd(DVD) drive into my machine, and i thought i'd have to mount it and add it for the fstab, but for my own curiosity, I tried to insert a audio disk in the drive, and it asked i I'd like to play/rip the cd, with data from CDDB. Then i thought, "hey.. it works", and tried to insert a DVD...... Nothing happened...

I have VLC, and i installed the extra DVD region things.... Can remember what, but it said so on their site...

For now I'd like to see matrix (region 2), so i hope you guys can help me...

Thanks :-)

---

### Post by mikewhatever on 2007-02-10
If you have Edgy installed, try System->Preferences->Removable Drives and Media, and make sure an application is selected to in the DVD disk section.

---

### Post by cmol on 2007-02-10
> **mikewhatever said:**
> If you have Edgy installed, try System->Preferences->Removable Drives and Media, and make sure an application is selected to in the DVD disk section.

There is.. Totem is set to run it..
Not sure how to make vlc do it..
vlc %m    ?????

---

### Post by cmol on 2007-02-10
Maybe i should say that, when i look at the "Computer"-folder,  without dvd disk, the drive is visible as CD-ROM/DVD-ROM Drive, but when i insert a DVD, it disappears from the list...

---

### Post by stimpsonjcat on 2007-02-12
> **cmol said:**
> Maybe i should say that, when i look at the "Computer"-folder,  without dvd disk, the drive is visible as CD-ROM/DVD-ROM Drive, but when i insert a DVD, it disappears from the list...
I reported [a bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/41458")very similar to your issue some time ago. If you confirm that bug perhaps we can persuade the devs to up its priority?

---

