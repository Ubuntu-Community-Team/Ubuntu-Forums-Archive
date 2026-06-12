---
title: "Publishing my first web page using a dedicated server ubuntu 6.06"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Dee.Jarman on 2008-04-15
Hello all,

I have just rented a dedicated server with Ubuntu pre-installed, but cannot see web pages on line even though I cann access the box using ssh.  As far as I understand it, apache is running and I should therefore be able to see the contents of /var/www via the web.

I type [http://xx.xx.xx.xx/mason_example/test.html](http://xx.xx.xx.xx/mason_example/test.html), but get a 404 response.  I get the same response for any other page I try to access.  I believe apache is running - from loooking at other forums, I have typed ps -ef and get the results as below.

Can anyone please let me know what I need to do to get access to these web pages.

Thanks

Dee

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Apr09 ?        00:00:01 init [2]
root         2     0  0 Apr09 ?        00:00:00 [kthreadd]
root         3     2  0 Apr09 ?        00:00:00 [migration/0]
root         4     2  0 Apr09 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 Apr09 ?        00:00:00 [watchdog/0]
root         6     2  0 Apr09 ?        00:00:00 [events/0]
root         7     2  0 Apr09 ?        00:00:00 [khelper]
root        27     2  0 Apr09 ?        00:00:00 [kblockd/0]
root        28     2  0 Apr09 ?        00:00:00 [kacpid]
root        29     2  0 Apr09 ?        00:00:00 [kacpi_notify]
root       104     2  0 Apr09 ?        00:00:00 [kseriod]
root       128     2  0 Apr09 ?        00:00:00 [pdflush]
root       129     2  0 Apr09 ?        00:00:00 [pdflush]
root       130     2  0 Apr09 ?        00:00:00 [kswapd0]
root       182     2  0 Apr09 ?        00:00:00 [aio/0]
root       896     2  0 Apr09 ?        00:00:00 [ata/0]
root       897     2  0 Apr09 ?        00:00:00 [ata_aux]
root      1936     2  0 Apr09 ?        00:00:00 [scsi_eh_0]
root      1938     2  0 Apr09 ?        00:00:00 [scsi_eh_1]
root      1939     2  0 Apr09 ?        00:00:00 [scsi_eh_2]
root      1940     2  0 Apr09 ?        00:00:00 [scsi_eh_3]
root      2014     2  0 Apr09 ?        00:00:00 [ksuspend_usbd]
root      2015     2  0 Apr09 ?        00:00:00 [khubd]
root      2141     2  0 Apr09 ?        00:00:16 [kjournald]
root      2342     1  0 Apr09 ?        00:00:00 /sbin/udevd --daemon
root      3491     2  0 Apr09 ?        00:00:00 [kpsmoused]
root      4444     1  0 Apr09 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4446     1  0 Apr09 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
107       4492     1  0 Apr09 ?        00:02:17 /usr/sbin/clamd
107       4550     1  0 Apr09 ?        00:00:00 /usr/bin/freshclam -p /var/run/clamav/freshclam.pid -d --quiet
root      4568     1  0 Apr09 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/
root      4569  4568  0 Apr09 ?        00:00:00 /usr/lib/courier/authlib/authdaemond.mysql
root      4587     1  0 Apr09 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -stderrlogger=/usr/sbin/courierlogger -maxpr
root      4590     1  0 Apr09 ?        00:00:00 /usr/sbin/courierlogger imaplogin
root      4610     1  0 Apr09 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -stderrlogger=/usr/sbin/courierlogger -stder
root      4616     1  0 Apr09 ?        00:00:00 /usr/sbin/courierlogger imapd-ssl
root      4628     1  0 Apr09 ?        00:00:00 /usr/sbin/couriertcpd -pid=/var/run/courier/pop3d.pid -stderrlogger=/usr/sbin
root      4634     1  0 Apr09 ?        00:00:00 /usr/sbin/courierlogger courierpop3login
root      4638  4569  0 Apr09 ?        00:00:00 /usr/lib/courier/authlib/authdaemond.mysql
root      4647  4569  0 Apr09 ?        00:00:00 /usr/lib/courier/authlib/authdaemond.mysql
root      4653     1  0 Apr09 ?        00:00:00 /usr/sbin/couriertcpd -pid=/var/run/courier/pop3d-ssl.pid -stderrlogger=/usr/
root      4659     1  0 Apr09 ?        00:00:00 /usr/sbin/courierlogger pop3d-ssl
root      4674     1  0 Apr09 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4700  4674  0 Apr09 ?        00:00:05 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-f
root      4701  4674  0 Apr09 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      4780     1  0 Apr09 ?        00:00:00 /usr/sbin/ntpd
109       4781  4780  0 Apr09 ?        00:00:00 /usr/sbin/ntpd
root      4801     1  0 Apr09 ?        00:00:00 /usr/sbin/sshd
root      4835     1  0 Apr09 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      4873     1  0 Apr09 ?        00:00:02 proftpd: (accepting connections)
root      4887     1  0 Apr09 ?        00:00:00 /usr/sbin/cron
root      4935     1  0 Apr09 ?        00:00:00 /usr/sbin/apache-ssl
root      5069     1  0 Apr09 tty1     00:00:00 /sbin/getty 38400 tty1
root      5070     1  0 Apr09 tty2     00:00:00 /sbin/getty 38400 tty2
root      5071     1  0 Apr09 tty3     00:00:00 /sbin/getty 38400 tty3
root      5072     1  0 Apr09 tty4     00:00:00 /sbin/getty 38400 tty4
root      5073     1  0 Apr09 tty5     00:00:00 /sbin/getty 38400 tty5
root      5074     1  0 Apr09 tty6     00:00:00 /sbin/getty 38400 tty6
root      5075     1  0 Apr09 ?        00:00:00 /bin/sh /command/svscanboot
root      5087  5075  0 Apr09 ?        00:00:11 svscan /service
root      5088  5075  0 Apr09 ?        00:00:00 readproctitle service errors: ...............................................
root      5089  5087  0 Apr09 ?        00:00:00 supervise qmail-smtpd
root      5090  5087  0 Apr09 ?        00:00:00 supervise log
root      5091  5087  0 Apr09 ?        00:00:00 supervise qmail-send
root      5092  5087  0 Apr09 ?        00:00:00 supervise log
root      5093  5087  0 Apr09 ?        00:00:00 supervise tinydns
root      5094  5087  0 Apr09 ?        00:00:00 supervise log
root      5095  5087  0 Apr09 ?        00:00:00 supervise axfrdns
root      5096  5087  0 Apr09 ?        00:00:00 supervise log
root      5097  5087  0 Apr09 ?        00:00:00 supervise ald_sites
root      5098  5087  0 Apr09 ?        00:00:00 supervise ald_ssl
root      5099  5087  0 Apr09 ?        00:00:00 supervise qmail-qmqpd
root      5100  5087  0 Apr09 ?        00:00:00 supervise log
71        5101  5089  0 Apr09 ?        00:00:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.smtp.cdb -c 20 -u 71 -g 71 0 smtp qmai
75        5102  5090  0 Apr09 ?        00:00:00 multilog t /var/log/qmail-smtpd
75        5103  5092  0 Apr09 ?        00:00:00 multilog t /var/log/qmail-send
500       5104  5093  0 Apr09 ?        00:00:00 /usr/local/bin/tinydns
501       5105  5094  0 Apr09 ?        00:00:00 multilog t s1000000 /var/log/tinydns
root      5106  5095  0 Apr09 ?        00:00:00 tcpserver -vDRHl0 -x /usr/local/djbdns/var/axfr.access.cdb -- 0 53 /usr/local
501       5107  5096  0 Apr09 ?        00:00:00 multilog t s1000000 /var/log/axfrdns
root      5108  5097  0 Apr09 ?        00:00:00 /bin/sh ./run
root      5109  5098  0 Apr09 ?        00:00:00 /bin/sh ./run
71        5110  5099  0 Apr09 ?        00:00:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.qmqp.cdb -c 20 -u 71 -g 71 0 628 qmail
75        5111  5100  0 Apr09 ?        00:00:00 multilog t /var/log/qmail-qmqpd
72        5112  5091  0 Apr09 ?        00:00:00 qmail-send
root      5121  5112  0 Apr09 ?        00:00:00 qmail-lspawn ./Maildir/
73        5122  5112  0 Apr09 ?        00:00:00 qmail-rspawn
74        5123  5112  0 Apr09 ?        00:00:00 qmail-clean
1012      5127  5109  0 Apr09 ?        00:00:00 fghack /usr/local/ald/ssl/ald
1012      5131  5108  0 Apr09 ?        00:00:00 fghack /usr/local/ald/sites/ald
1012      5132  5127  0 Apr09 ?        00:00:00 [ald] <defunct>
1012      5133  5131  0 Apr09 ?        00:00:00 [ald] <defunct>
1012      5134     1  0 Apr09 ?        00:00:00 /usr/local/ald/ssl/ald
1012      5135     1  0 Apr09 ?        00:00:00 /usr/local/ald/sites/ald
root      5205     1  0 Apr09 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5211     1  0 Apr09 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5213     1  0 Apr09 ?        00:00:00 /usr/sbin/cron
root      5227     1  0 Apr09 ?        00:00:00 /usr/sbin/sshd
root      5245     1  0 Apr09 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5310  5245  0 Apr09 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-f
root      5311  5245  0 Apr09 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      5386     1  0 Apr09 ?        00:00:00 python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts
syslog    7890     1  0 00:05 ?        00:00:00 /sbin/syslogd -u syslog
syslog    9048     1  0 06:25 ?        00:00:00 /sbin/syslogd -u syslog
www-data 10171  4935  0 13:13 ?        00:00:00 /usr/sbin/apache-ssl
root     10201  4801  0 13:16 ?        00:00:00 sshd: root@pts/0
root     10203 10201  0 13:16 pts/0    00:00:00 -bash
root     10216 10203  0 13:16 pts/0    00:00:00 /bin/bash -i
root     10242  5227  0 13:18 ?        00:00:00 sshd: root@pts/1
root     10244 10242  0 13:18 pts/1    00:00:00 -bash
root     10402  5227  0 14:01 ?        00:00:00 sshd: root@pts/2
root     10404 10402  0 14:01 pts/2    00:00:00 -bash
root     10470  5227  0 14:24 ?        00:00:00 sshd: root@pts/3
root     10472 10470  0 14:25 pts/3    00:00:00 -bash
root     10485  5227  0 14:26 ?        00:00:01 sshd: root@notty
root     10487 10485  0 14:26 ?        00:00:00 /usr/lib/openssh/sftp-server
root     10997 10404  0 16:23 pts/2    00:00:00 ssh 62.44.83.129
root     11188     1  0 16:51 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 11189 11188  0 16:51 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
root     11190 11188  0 16:51 ?        00:00:00 /usr/bin/perl /bin/mapssl
www-data 11192 11188  0 16:51 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 11194 11188  0 16:51 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
root     11417 10472  0 17:52 pts/3    00:00:00 ps -ef
root     29182     1  0 Apr13 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
www-data 29210  4935  0 Apr13 ?        00:00:00 /usr/lib/apache-ssl/gcache 33 /var/run/gcache_port
www-data 29211  4935  0 Apr13 ?        00:00:00 /usr/sbin/apache-ssl
www-data 29212  4935  0 Apr13 ?        00:00:00 /usr/sbin/apache-ssl
www-data 31801  4935  0 Apr13 ?        00:00:00 /usr/sbin/apache-ssl

---

### Post by GCoffee on 2008-04-15
Is port 80 forwarded? If so, are you accessing it from the local address or the internet address? 

Is there A document in your document directory?  If not try inserting one under the name of index.html,index.php ETC... some webservers are setup so if there is no documents in the document root then it does not display the webserver.

---

### Post by Dee.Jarman on 2008-04-15
Hi GCoffee,

Thanks for the quick response.  I am trying to access it across the web.  Can you tell mw how to check if port 80 is forwarded?

I'm not sure what you mean by my documents directory.  I have placed a basic web page called index.html in www/var and that doesn't seem to have made any difference.

Since the original posting, I have been scanning the forums and am now concerned the /etc/apache2/sites-available/default file doesn't seem to have www/var in it.  The file is shown below (I have xx out the IP address as this is a public forum).

Thanks again

Dee

<Directory />
    Options FollowSymLinks
    AllowOverride None
</Directory>

<Directory /domains/*/*/*/public_html>
    AllowOverride All
    Options IncludesNoExec ExecCGI
</Directory>

<Directory /home/*/*/*/public_html>
    AllowOverride All
    Options IncludesNoExec ExecCGI
</Directory>

<Directory /domains/*/*/*/public_html/_vti_bin>
    AddHandler application/x-suphp-cgi .exe
    RLimitCPU 40 40
</Directory>

<Directory /fs/home/*/*/*/*/public_html>
    AllowOverride All
    Options IncludesNoExec ExecCGI
</Directory>

<VirtualHost xx.xx.xxx.xxx:80>
    ServerName ds5543.dedicated.turbodns.co.uk
    ErrorLog /var/log/apache2/error_log
    CustomLog /var/log/apache2/sites_access_log ald
    VirtualDocumentRoot /domains/%1.1/%1.2/%0/public_html

    # VirtualDocumentRoot only sets the effective document root for each site;
    # it doesn't update the DOCUMENT_ROOT environment variable to reflect that
    # (and Apache developers are adamant this is the correct behaviour).  Also
    # it isn't possible to set DOCUMENT_ROOT manually, so instead set
    # VIRTUAL_DOCUMENT_ROOT to what we want DOCUMENT_ROOT to be, then use
    # suphp-docroot to intercept calls to suPHP and move the value of
    # VIRTUAL_DOCUMENT_ROOT into DOCUMENT_ROOT:
    RewriteEngine on
    RewriteCond %{LA-U:SCRIPT_FILENAME} (.*)/[^/]+
    RewriteRule ^ - [E=VIRTUAL_DOCUMENT_ROOT:%1]
</VirtualHost>

RewriteLock "/tmp/rewrite.lock"

<VirtualHost xx.xx.xx.xx:443>
    ServerName ds5543.dedicated.turbodns.co.uk

    SSLEngine on
    SSLCertificateFile /etc/apache2/ssl/apache.pem

    RewriteEngine on
    RewriteLog "/var/log/apache2/rewrite.log"
    RewriteLogLevel 2
    RewriteMap ssl-map prg:/bin/mapssl
    RewriteRule ^/(.*)$ /${ssl-map:$1}

    CustomLog /var/log/apache2/ssl_access_log ssl

    LogLevel warn
    ErrorLog /var/log/apache2/error_log

</VirtualHost>

<VirtualHost *:81>
    ErrorLog /var/log/apache2/error_log
    CustomLog /var/log/apache2/sites_access_log ald

    RewriteEngine on
    RewriteLogLevel 0
    RewriteRule ^/((.)(.)[^/]*)(.*) /home/$2/$3/$1/public_html/$4

</VirtualHost>

---

### Post by GCoffee on 2008-04-15
try checking your error log.. 

As for checking if port 80 is forwarded, if you can access it with your public ip address (find it at [http://www.ipchicken.com/](http://www.ipchicken.com/)) then port 80 is indeed forwarded. Why do you need so many virtual hosts? Try taking some away... you could be putting your index.html file in a directory for a different virtual host.

When I say documents directory i meant Directory Root. Sorry if this confused you..

---

### Post by bsharp on 2008-04-15
Something to suggest....

If you are paying for a dedicated server, why not get the people you are renting it from to set it up for you? If they won't do it, I would start looking for somewhere else that has better support.

---

### Post by GCoffee on 2008-04-15
> **bsharp said:**
>  If they won't do it, I would start looking for somewhere else that has better support.

That is a point... Are you setting up your own dedicated server or are you using a company?

If you are and they wont help you i belive you could have the right to a full refund.

---

### Post by Dee.Jarman on 2008-04-15
I'm using 123-reg and they have been extremely unhelpful.  It took me almost a week to get SSH access, then they will only give you root access on the basis that you are no longer entitled to tech support.  I went for them as a prcing decision (£40 per month) and am regretting it.

I actually do not want any virtual hosts.  The application I plan to use doesn't work well with virual servers which is why I went for the didicated option.

Any virtual hosts that are there, were put on there by the provider.  Can you tell me how I can delete these?

Thanks again

---

