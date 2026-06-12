---
title: "Redirecting IPTABLES messsages to certain tty?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-17
I've got no idea to what forum I should post this question, but

How do I redirect messages that IPTABLES or some other module is constantly
printing on my other terminal windows (Ctrl+Alt+F1 - F6) to certain terminal only?
Say, only on tty6?

I recall SuSE had environmet set this way, and it would be really nice if those
messages wouldn't appear when I'm in middle of editing some file.

---

### Post by Pragmatist on 2006-03-17
The iptables man page says:
> Various  error  messages  are  printed  to  standard  error.  The exit code is 0 for correct functioning. Errors which appear to be caused by invalid or abused command line parameters cause an exit  code  of  2, and other errors cause an exit code of 1.

This means you can use the general approach to redirecting error messages as explained here:
[http://www.tldp.org/LDP/intro-linux/html/sect_05_02.html](http://www.tldp.org/LDP/intro-linux/html/sect_05_02.html)

See section 5.2.2.2 
> "Seperating standard output from standard error"
Constructs like these are often used by programmers, so that output is displayed in one terminal window, and errors in another. Find out which pseudo terminal you are using issuing the **tty** command first:
[COLOR=#000000]andy:~/newsoft> **make all 2> /dev/pts/7**[/COLOR][COLOR=#000000] [/COLOR]

---

### Post by mlind on 2006-04-24
I finally firgured how to get this working.

I uncomment this block from /etc/syslog.conf. Messages are now only published
on /dev/tty8 ( Ctrl+Alt+F8 )
```

daemon,mail.*;\
        news.=crit;news.=err;news.=notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       /dev/tty8

```

and commented out the default (published messages on every tty)
```

#daemon.*;mail.*;\
#       news.crit;news.err;news.notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       |/dev/xconsole

```

then I tuned down the verbosity by modifying /etc/init.d/klogd 
```

KLOGD="**-c 4** -P $kmsgpipe"

```

then restarted both syslogd and klogd daemons
```

sudo /etc/init.d/klogd restart
sudo /etc/init.d/syslogd restart

```

Messages now appear on /dev/tty 8 only, and to /var/log/messages.

---

