---
title: "syslogd-listfiles and cron.daily"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ruy_lopez on 2007-05-21
Hello,

The sylogd file in /etc/cron.daily suggests that syslogd-listfiles can be used in conjunction with grep to filter which logfiles will be rotated. I run a mail server and want to rotate mail.log and mail.err etc. on a daily basis. However when I included the following:

```
for LOG in `syslogd-listfiles -all | grep mail`
do
      if [ -s $LOG]; then  /* line 47 */
          savelog -g adm -m 640 -u root -c 7 $LOG
      fi
done
```

cron was mailing me this:

```

/etc/cron.daily/sysklogd:
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
```

I don't really understand what's happening here. The logs aren't empty, or anything. When I run "syslogd-listfiles -all | grep mail" on the command line it generates the absolute pathnames for my mail.* logs. The fact that there are four [: missing `]' errors for the four mail.* logs suggests that the correct files are being filtered by the script. So why are they posted missing?

I'm sure I've done this before on an old system and never encountered this problem. It can't be anything to do with the pathnames, because including this:

```
savelog -g adm -m 640 -u root -c 7 /var/log/mail.log
...
```

manually for each of the mail logs, seems to fix the problem. Also, (and my memory might be foxing me here), didn't there used to be a way to specify which files are grouped using syslogd-listfiles? I can't find anything in the manpages.

---

### Post by mitch.c on 2007-05-21
> **ruy_lopez said:**
> 

```
for LOG in `syslogd-listfiles -all | grep mail`
do
      if [ -s $LOG]; then  /* line 47 */
          savelog -g adm -m 640 -u root -c 7 $LOG
      fi
done
```

cron was mailing me this:

```

/etc/cron.daily/sysklogd:
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
/etc/cron.daily/sysklogd: line 47: [: missing `]'
```

If you look closely at the error, it's telling you exactly what's wrong... missing ']'. The missing ']' character is because you have no whitespace between $LOG and the ']; in the test expression. The line should read like this:
```
          if [ -s $LOG ]; then  /* line 47 */
```
Add the space, and you should be OK.

-- 
Mitch

---

### Post by ruy_lopez on 2007-05-21
> If you look closely at the error, it's telling you exactly what's wrong... missing ']'. The missing ']' character is because you have no whitespace between $LOG and the ']; in the test expression.

Just the ticket, cheers.

---

