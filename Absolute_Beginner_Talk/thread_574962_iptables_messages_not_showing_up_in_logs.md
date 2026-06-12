---
title: "iptables messages not showing up in logs?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by chaeron on 2007-10-13
My iptables messages are not showing up in the logs.  Nothing appears in /var/log/syslog nor in /var/log/messages.

What puzzles me is that if I issue a dmesg command, I do see the iptables log messages.

Can someone explain to me why I'm not seeing my iptables messages in the log files where I would expect them to be?

I'm sure I'm missing something simple...so pointing me in the right direction would be very much appreciated!  Thanks!

I'm running Feisty and my /etc/syslog.conf file looks like this:

```
auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log
uucp.*				/var/log/uucp.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info			-/var/log/mail.info
mail.warn			-/var/log/mail.warn
mail.err			/var/log/mail.err

# Logging for INN news system
#
news.crit			/var/log/news/news.crit
news.err			/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg				*


# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
	news.crit;news.err;news.notice;\
	*.=debug;*.=info;\
	*.=notice;*.=warn	|/dev/xconsole
```

---

