---
title: "Cron Help"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by edgy123 on 2007-05-03
Hi this is my first post so bare with me.  I'm using Server edition 7.04 and have installed some drupal CMS software.  I have followed instructions found in the server guide for adding a cron job.  I'm trying issue a wget command hourly to update my RSS feeds.  I've put a file with the wget command in the /etc/cron.hourly directory and it doesn't seem to run.  If I issue the same command at the console it works fine.  I've made a file with a .sh extension and with no extension and placed it into the /etc/cron.hourly directory.  Any help or ideas are appreciated.  Thanks.

---

### Post by Bachstelze on 2007-05-03
Is your sh file executable ?

---

### Post by edgy123 on 2007-05-03
Hi,  yes, i've assigned 775 to both files.

---

### Post by edgy123 on 2007-05-08
Anymore ideas, I still cannot make the script run.  Thanks.

---

### Post by hyper_ch on 2007-05-08
what happens if you run the file manually?

---

