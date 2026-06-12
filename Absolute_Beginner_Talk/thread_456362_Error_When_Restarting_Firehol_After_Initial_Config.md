---
title: "Error When Restarting Firehol After Initial Configuration"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by NuttBoxer on 2007-05-27
I am attempting to install dansguardian with tinyproxy and firehol onto Feisty using the following howto- [http://ubuntuforums.org/showthread.p...t=dansguardian](http://ubuntuforums.org/showthread.p...t=dansguardian). As it specifies, I'm using Gedit. This is my conf settings for Firehol:

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept


When I restart Firehol, this is the error that I get:

ERROR : # 1.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 2.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 3.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c1 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 4.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c2 -p tcp --sport 32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 5.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c2 -p tcp --sport 6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 6.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 7.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 8.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 9.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 10.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 11.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 12.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 13.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 14.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 15.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 16.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 17.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 18.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 19.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 20.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 21.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 22.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 23.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 24.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT
OUTPUT :


[fail]
Thank you in advance for your help.

---

### Post by xexeo on 2007-05-31
The Firehol project  has (just) solved problems with the new kernel and with bash 3.2, but R5 1.255 is not yet in Ubuntu Feisty.

You can try [https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22) .
That solution worked for me.

---

