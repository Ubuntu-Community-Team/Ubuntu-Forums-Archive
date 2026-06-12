---
title: "Possible trojan(gatecrasher)"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by jsvidyad on 2005-08-03
Hi!!

     I noticed on my firewall (firestarter) a policy to let gatecrasher use port 6969 for outbound traffic. I did not make the policy and it was not there before. Does this mean my computer has been hacked. I found out that gatecrasher was a trojan, but from what I found out, it seems to affect only windows. Can it affect linux too?? Also, how can I find out if someone has installed something on my computer or not??

---

### Post by heimo on 2005-08-04
Boot from some Live CD and run chkrootkit. Don't trust your computer if you think it may have been compromised, you can't trust output of any of the binaries if those have been replaced. Port number doesn't indicate which program was used (if any) to open backport to your computer. Hopefully you can find some other reason for this, but take it seriously. (I know I would.)

If you're uncertain and can't investigate very well what has happened - if possible, make a backup of whole system and then reinstall - do not restore any binaries, be sure to apply all upgrades. Any server software (outbound listening services) running on your system?

Check this (do you use bittorrent?):
[http://ubuntuforums.org/showthread.php?t=26337&highlight=6969+firestarter]("http://ubuntuforums.org/showthread.php?t=26337&highlight=6969+firestarter")

---

### Post by jsvidyad on 2005-08-04
Thank you!!!

   What sort of output does chkrootkit give??? So, I just have to boot from the ubuntu live cd???

---

### Post by heimo on 2005-08-04
[QUOTE=jsvidyad]Thank you!!!

   What sort of output does chkrootkit give??? So, I just have to boot from the ubuntu live cd???[/QUOTE]

You run chkrootkit on terminal and when everything's fine, you get output like this:
 ```

Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not infected
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... nothing found
Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5253])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

``` 

This line:
```
eth0: PACKET SNIFFER(/sbin/dhclient3[5253])

```
... is a false positive AFAIK*.

EDIT: *) Some other people think so too:
[http://ubuntuforums.org/showthread.php?t=8220](http://ubuntuforums.org/showthread.php?t=8220)

---

### Post by jsvidyad on 2005-08-04
I was unable to run chkrootkit from live cd as I had not installed it. So, I removed the live CD and rebooted and installed chkrootkit. It gave a result similar to what you had given. The output is given here.

Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not infected
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while...
/usr/lib/blender/.Blanguages /usr/lib/blender/.bfont.ttf

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... nothing found
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
ra0: PACKET SNIFFER(/sbin/dhclient3[5636])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

Also, about bittorrent, i do use it, but when I checked the policy for outbound connections, it mentioned specifically that the program which is going to use it is GateCrasher and it is going to use port 6969. i checked on the web and found that gatecrasher is a trojan which uses ports 6969 and 6970. Right now, I have blocked  those two ports for gatecrasher. There are some variants which use some other ports and I have blocked those ports too for those programs.

   Is there anything else that I have to do???  if absolutely necessary, I can reinstall ubuntu. Any guidance would be greatly appreciated.

---

### Post by heimo on 2005-08-04
What's strange, is why the change in firestarted rules? I don't know firestarter, but I haven't heart about any automatic rules and if you didn't put that in there, something put. I would not trust running chkrootkit on that computer - it's just meaningless, as if the computer is compromised, you can not trust it. There's just no way - you need to boot a known clean system to check the suspected system. You can't trust negative / clean result, you only could trust if chkrootkit would say your system has rootkit installed on it (which has failed to hide itself)*.

I have a good hunch that this is nothing. It's a mistake of some kind, but you will never trust that system if you haven't made it clear to yourself what caused the extra rule on your firewall. It will haunt.

Other pointless (in case of your system was "rooted") test, which (in case your system was not "rooted") can show what's causing this is to run netstat -ltp and watch if anything is hooked to port 6969. Run ethereal or tcpdump - launch bittorrent. Of course, analyzing the results requires knowledge of network protocols / some kind of feeling of what should be going on and what is not supposed to happen.

Take this as an oppotunity to learn about your system. Don't panic - be patient and don't do anything stupid (rush into conclusions, in this world nothing is what is looks like). You have time to investigate and make your mind if reinstall is needed or not. Do not base your decision on the amount of work you would have to do to reinstall the system. But if you eventually decide to reinstall, make sure that this doesn't happen again - or at least keep eye on it - maybe you'll find out harmless reason which caused this in the first place.

Oh, and did I mention: do not panic.


*) And in that case, cleaning the system with reinstall would be the only option, no other way around it.

---

### Post by jsvidyad on 2005-08-04
Thank you very much!!!

   I have decided to reinstall the OS. Right now, I do not have too much data on my computer and if I find later on that my system has been compromised, it will be a headache to backup all data.

   Thanks again.

              - Jyothish

---

