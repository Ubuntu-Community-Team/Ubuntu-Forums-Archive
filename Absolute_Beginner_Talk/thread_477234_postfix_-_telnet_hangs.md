---
title: "postfix - telnet hangs"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by nigelicious on 2007-06-18
Hi all, hope you can help as a search of the forum hasnt

tried setting up mail using [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) , but when I finish following the instructions I try telnet to localhost 25 and it connects and hangs, no response.

I tried to dpkg remove and purge postfix and try again using [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) , however I get the same end result

Ive tried restarting the services and making sure it is listening, but I am having no joy. Does anyone have a suggestion, or a way for me to remove all of the settings thus far to try an alternative?

---

### Post by mitch.c on 2007-06-19
> **nigelicious said:**
>  Does anyone have a suggestion, or a way for me to remove all of the settings thus far to try an alternative?

Let's start with the simple stuff... did you restart postfix after changing main.cf?
```
$ sudo /etc/init.d/postfix restart
```

Check to make sure postfix is listening:
```
$ netstat -a | grep :smtp
# output should look something like
tcp         0     0 localhost:smtp          *:*                     LISTEN
tcp6        0     0 ip6-localhost:smtp      *:*                     LISTEN
```

Just for reference, here's a copy of my /etc/postfix/main.cf. I am only configured for outbound mail. You could temporarily replace your copy with mine for testing and work your way backward to your desired configuration. You'll need to replace yourdomain.com and hostname:
```
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = yourdomain.com         # replace with your domain
myhostname = ubuntu                  # replace with your hostname
mydomain = yourdomain.com            # replace with your domain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
##mydestination = localhost, localhost.localdomain, localhost
#mydestination = localhost
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
myorigin = /etc/mailname
#append_at_myorigin = no
inet_protocols = all
```

Then to test:
```
$ telnet localhost 25
```
[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

---

