---
title: "Virtual Box"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bigal1932flying on 2008-01-03
Since upgrading to Gutsy I cannot open XP in Virtual Box. When I try I receive the following message:
Failed to start the virtual machine XP Pro.
PIIX3 cannot attach drive to the Secondary Master.
VBox status code:-102 ( VERR_FILE_NOT_FOUND )

Any ideas?

---

### Post by Xavieran on 2008-01-03
It looks like it deleted a virtual hardrive?:confused:

---

### Post by ryanVickers on 2008-01-03
yeah, you'll have to modify the VM settings to not use the drive in the mean time if you want to boot it, but yeah, the drive is missing, perhaps not in the folder in the right place or wrong name?

---

### Post by Ubuntwan on 2008-04-28
The post by Rytron in this thread solved this problem for me: [http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3]("http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3")
I had a cd mounted last time virtualbox was running and it was missing this cd now, and gave this error. In the settings menu I unchecked the mount cd/dvd drive checkbox and everything was fine again.

---

