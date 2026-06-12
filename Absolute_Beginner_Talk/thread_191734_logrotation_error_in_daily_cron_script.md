---
title: "logrotation error in daily cron script"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by CMKoehler on 2006-06-07
Hey guys,

Just updated to Dapper, and it was pretty flawless! Probably related to that, although I am not 100% sure, is this error I get in my mailbox about log rotation:

/etc/cron.daily/sysklogd:
mv: cannot stat `/var/log//syslog.3.gz': No such file or directory
gzip: /var/log//syslog.0.gz: File exists

I guess that means the file isn't there, but what strikes me is that there are two // in the pathname. Does anyone have any idea how to fix this?

Thanks!


Christoph

---

### Post by falcon15500 on 2006-06-22
Try having a scan through the script /etc/cron.daily.sysklogd and see if you can spot anything untoward.  The script isn't very long (if you take the comments out) so you may even like to post it here.

falc

---

### Post by CMKoehler on 2006-06-22
```
test -x /usr/sbin/syslogd-listfiles || exit 0
test -x /sbin/syslogd || exit 0
test -f /usr/share/sysklogd/dummy || exit 0

set -e

cd /var/log
for LOG in `syslogd-listfiles`
do
   if [ -s $LOG ]; then
      savelog -g adm -m 640 -u root -c 7 $LOG >/dev/null
   fi
done

for LOG in `syslogd-listfiles --auth`
do
   if [ -f $LOG ]; then
      chown root:adm $LOG
      chmod o-rwx $LOG
   fi
done

# Restart syslogd
#
/etc/init.d/sysklogd reload-or-restart > /dev/null
```

I didn't change anything in the script, but I appreciate your help!!

Christoph

---

