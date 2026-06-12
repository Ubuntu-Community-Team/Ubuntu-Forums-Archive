---
title: "Backup Script"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Pigsflew on 2008-04-02
> 1) If a file gets deleted from the server then delete it from the external drive.
2) If a file is updated on the server then update on the external drive.
3) If possible perhaps alter the script to run something that ONLY updates the external (delete files or update them)as to what ever changes have been made to the server.

This will be a somewhat complicated script.

It will need to first untar the files in /mnt/backup or /mnt/backup1, if they exist

It will require a loop to check through every file within /data, /u, /var/www, /d2a, /etc, /home, and var/lib/mysql, checking MAC (Modified/Accessed/Created) times between matching files (e.g. /data/file to /mnt/backup/file, /u/file to /mnt/backup/backup/u/file), and then for each file, copy them if newer, deleting if gone.

Then it will need to re-tar the folders corresponding to /u, /var/www, /d2a, /etc, /home, and var/lib/mysql.

I'm not sure this will save you very much time; what you may want to do is try Google's [Flyback]("http://code.google.com/p/flyback/") instead, or simply write your script to use rsync. A great place to find info about rsync is [here]("http://blog.interlinked.org/tutorials/rsync_time_machine.html").


Good luck!

---

