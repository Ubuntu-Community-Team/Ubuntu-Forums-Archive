---
title: "crontab backup not running ???"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by petef on 2006-06-01
Ive created a cron job to backup my system to a 2nd drive i have installed. Jobs I have created under my login work fine e.g: xmms swtches on each morning at a set time and tunes into a radio station, but I want to create a backup job to running during the night. I logged in as #root tested running tar on a backup of the system which worked fine so added the same thing to cron while logged in as # but when I checked the next day nothing ran on the night ?? 

Any help appreciated.

Pete

---

### Post by Klaidas on 2006-06-01
What do you mean by logging in as root? :)
I suggest ```
sudo crontab -e
```, which should open root's cron file.
Aslso, could you post the content of the crontab?

---

### Post by petef on 2006-06-01
I logged in sudo su and then ran crontab -e

also any idea what these messages mean in the logs ?

May 28 18:40:15 localhost -- MARK --
May 28 19:00:15 localhost -- MARK --
May 28 19:20:15 localhost -- MARK --
May 28 19:40:15 localhost -- MARK --
May 28 20:00:15 localhost -- MARK --
May 28 20:20:15 localhost -- MARK --
May 28 20:40:15 localhost -- MARK --
May 28 21:00:15 localhost -- MARK --
May 28 21:20:15 localhost -- MARK --
May 28 21:40:15 localhost -- MARK --
May 28 22:00:15 localhost -- MARK --
May 28 22:20:15 localhost -- MARK --
May 28 22:40:15 localhost -- MARK --
May 28 23:00:15 localhost -- MARK --
May 28 23:20:15 localhost -- MARK --
May 28 23:40:16 localhost -- MARK --
May 29 00:00:17 localhost -- MARK --
May 29 00:20:17 localhost -- MARK --

---

### Post by petef on 2006-06-02
Anyone ????

---

### Post by tkjacobsen on 2006-06-02
What is the output form ```
sudo crontab -l
```

---

### Post by petef on 2006-06-02
Im at work at the moment so unfortunately don't have access to my machine. I can run it later. I basically copied the command I ran at the prompt using tar

Thanks for the reply

Pete

---

