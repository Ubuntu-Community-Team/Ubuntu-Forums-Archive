---
title: "Nofify if exit &gt; 0 of script run at shutdown"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by ulriks on 2006-09-03
Hello All,

I run rdiff-backup at shutdown on my home computer, after following the instructions on [kudos.berlinos.de]("http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#zzboot").

Is there a way to be notified as normal user, if the rdiff-backup exited with anything different that 0? Is there a 'notify user' flag that can be set somewhere?

Thanks for any help and suggestions
Ulrik

---

### Post by mssever on 2006-09-03
I'm not familiar with rdiff-backup, but it appear that you're running it from an init script--if you're following the link you gave. In that case, you could insert something like this into your script immediately after the call to rdiff-backup:
```
exitstatus="$?"
if [ $exitstatus -ne 0 ]; then
    echo "rdiff-backup exited with status ${exitstatus}." | sendmail root@localhost
fi
``` 

This will mail you (actually the user created during install) when there's a problem. If you properly set up sendmail, you can also send mail to an external email address. You can use mutt to read mail.

---

### Post by mssever on 2006-09-03
Just thought of something: If you only want to have messages similar to the other init scripts, put this before the call to rdiff-backup: ```
log_begin_msg "Running rdiff-backup..."
```
and put this immediately after the call:
```
status=$?
log_end_msg $status
exit $status
```

---

### Post by ulriks on 2006-09-09
Thanks for the reply!

IO just want to know if something went wrong with the backup. My computer is not always online, so sending an e-mail was not so hot. Also I figured that checking e-mails with pine would be the same as checking the log :-D

What I do is leaving a file on my desktop if something went wrong:

```
  # Back up the whole home-dir, excluding the directories in the rdiff_exclude-files.txt list
  rdiff-backup -v 5 --exclude-filelist $homedir/rdiff_exclude-files.txt --exclude-symbolic-links $homedir $target
  # Notify me if something went wrong.
exitstatus="$?"
if [ $exitstatus -ne 0 ]; then
   echo "rdiff-backup exited with status ${exitstatus}." > $homedir$backupErrorFile
   # Set the owner to me
   chown me.me $homedir$backupErrorFile
   chmod 644 $homedir$backupErrorFile
fi
```

It looks like it is working just fine!

Thanks!
Ulrik

---

