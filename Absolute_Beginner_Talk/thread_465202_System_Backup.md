---
title: "System Backup"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-05
What do you think is the best method for a system backup.

---

### Post by starcraft.man on 2007-06-05
> **jonward0690 said:**
> What do you think is the best method for a system backup.

Well, I personally image (whole partitions) all my OS installs after I do them and update when I modify things in a major way. I find its the best means, then if I mess an install I pop in my disk, access the image on my USB drive and the 20 minutes later I got my customized OS back again. [Here are a list of apps for linux]("http://linuxappfinder.com/backupandrecovery/driveimaging"), a lot of people like partition image.

If your aiming at a regular update backup of only some files, ya may [want this.]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")

---

### Post by theorem_hunter on 2007-06-06
starcraft.man, which tool exactly do you use to do the iso backup... personally i think that sounds like the best way... a dual layer re-writeable dvd... i just need to back up my root partition /home is fine (i have two main partitions, / & /home)

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             48062468   8142176  37478816  18% /

```

---

### Post by starcraft.man on 2007-06-06
> **theorem_hunter said:**
> starcraft.man, which tool exactly do you use to do the iso backup... personally i think that sounds like the best way... a dual layer re-writeable dvd... i just need to back up my root partition /home is fine (i have two main partitions, / & /home)

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             48062468   8142176  37478816  18% /

```

The application I personally use is Acronis True Image (paid proprietary product). Was using it before I switched to linux and I'm kinda stuck with em since all my backups are their proprietary format. It is a good product though. They have very good compression algorithms, I get it down to almost 40-45% of the orginal disk size in most cases, sometimes even less.

I'd recommend partition image or ghost 4 linux for you though. Heard good things about both of them.

Oh and I don't back to a DVD (I could), I have an external USB storage drive. I made a 20 GB NTFS partition and use it exclusively for back up images.

---

