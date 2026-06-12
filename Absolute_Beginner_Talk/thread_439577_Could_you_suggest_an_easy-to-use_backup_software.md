---
title: "Could you suggest an easy-to-use backup software?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-05-10
Something along the lines of Simple Backup (which I have just tried out) but with compression / archiving capability.
I want to set up target and destination directories, and then be able to just hit the button and end up with a backup archive file.
Ta!

---

### Post by fakie_flip on 2007-05-10
Write a bash script to do what you want. In your script, you can use the mv (move) command, the tar (make archive) command, gzip (for compression) command, scp (short for secure copy, it lets you send files over a network through an encrypted ssh tunnel) command. If you want the script to run on automatically at certain times for example, every night at midnight, 2x a day, once a week, only on the weekends, use cron to run your script. You can add your script to /etc/cron.daily or use the crontab -e command. I'm not going to teach you those here because there are already plenty of well written guides on the internet.

---

### Post by fakie_flip on 2007-05-10
If you want to "just hit a button". Then make the script I described above, and make a launcher for your script instead of using the cron daemon to run the script automatically. Right click your desktop to make a launcher.

---

