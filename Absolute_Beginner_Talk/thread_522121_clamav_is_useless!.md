---
title: "clamav is useless!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-08-10
So I have the following packages from Synaptic installed - 
clamav
clamav-base
clamav-docs
clamav-freshclam
clamtk
libclamav2
Every time I start it from *Applications-->Accessories-->Virus Scanner*, I get the following message: > Unable to view ClamAV's information file. This will affect how ClamTk views the number of viruses and version information.
And when I click on **Scan a file/ directory**, I get a message saying: > You do not appear to have virus definitions! Running "freshclam -v" as root may fix the problem. 
BUT when I run freshclam - v as root, this happens:
> Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Fri Aug 10 15:55:06 2007
Querying current.cvd.clamav.net
TTL: 300
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 3908
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Fri Aug 10 15:58:33 2007
Querying current.cvd.clamav.net
TTL: 93
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 3908
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Fri Aug 10 16:01:56 2007
Querying current.cvd.clamav.net
TTL: 300
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 3908
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-3865.cdiff](http://db.local.clamav.net/daily-3865.cdiff)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host db.local.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host db.local.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
Restoring incremental directory daily.inc from backup
Giving up on db.local.clamav.net...
ClamAV update process started at Fri Aug 10 16:05:03 2007
Querying current.cvd.clamav.net
TTL: 114
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 3908
Retrieving [http://database.clamav.net/daily-3865.cdiff](http://database.clamav.net/daily-3865.cdiff)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host database.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host database.clamav.net (IP: 58.221.222.66)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-3865.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-3865.cdiff](http://database.clamav.net/daily-3865.cdiff)
Ignoring mirror 61.205.61.201 (too often connections with outdated version)
Ignoring mirror 193.140.100.10 (too often connections with outdated version)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host database.clamav.net (58.221.222.66)...
nonblock_connect: connect timing out (30 secs)
Can't connect to port 80 of host database.clamav.net (IP: 58.221.222.66)
ERROR: getpatch: Can't download daily-3865.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-3865.cdiff](http://database.clamav.net/daily-3865.cdiff)
Ignoring mirror 202.71.97.92 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.178.137.175 (too often connections with outdated version)
Ignoring mirror 211.10.155.48 (too often connections with outdated version)
Ignoring mirror 211.12.214.131 (too often connections with outdated version)
Ignoring mirror 211.239.150.206 (too often connections with outdated version)
Ignoring mirror 218.44.253.75 (too often connections with outdated version)
Ignoring mirror 219.106.242.51 (too often connections with outdated version)
Ignoring mirror 219.117.246.122 (too often connections with outdated version)
Ignoring mirror 222.124.18.201 (too often connections with outdated version)
Trying host database.clamav.net (58.221.222.66)...



And keeps happening. What do I do?

---

### Post by kleo skywalker on 2007-08-10
So many views and not one reply?

---

### Post by asmoore82 on 2007-08-10
> clamav is useless!

DUH!!

*av for Linux is Useless!

Purge Man!

---

### Post by wieman01 on 2007-08-10
Try AVG instead. There is a Debian/Ubuntu package available here:

[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl")

---

### Post by kleo skywalker on 2007-08-10
> **asmoore82 said:**
> DUH!!

*av for Linux is Useless!

Purge Man!

Yes I know a lot of people are of that opinion; and given how little I know about that kind of stuff I'm sure they're right. However, I'm a bit paranoid so I'd like to have a functioning AV. Also, it is possible for me to give infected stuff (harmless to me) to Windows users, isn't it? Better safe than sorry.

---

### Post by wieman01 on 2007-08-10
> **kleo skywalker said:**
> Yes I know a lot of people are of that opinion; and given how little I know about that kind of stuff I'm sure they're right. However, I'm a bit paranoid so I'd like to have a functioning AV. Also, it is possible for me to give infected stuff (harmless to me) to Windows users, isn't it? Better safe than sorry.
Install one if that makes you feel more comfortable. That's actually a good reason to get one if you ask me although it might not be strictly necessary in a Linux/Unix environment. 

I can recommend AVG as pointed out above. Works pretty much like the Windows version.

---

### Post by kleo skywalker on 2007-08-10
> **wieman01 said:**
> Install one if that makes you feel more comfortable. That's actually a good reason to get one if you ask me although it might not be strictly necessary in a Linux/Unix environment. 

I can recomment AVG as pointed out above. Works pretty much like the Windows version.

Thanks, I'll give it a try.

---

### Post by euler_fan on 2007-08-10
I usually install ClamAV from source, not the repos. Works better that way.

The following guide should get you going just fine, but is for an older version of Clam. Ergo you will have to change a few details (such as the exact filenames and folder names) in a few places. All of the stuff about festival is completely optional, just make sure you leave out all references to it.

[ClamAV install Guide]("http://ubuntuforums.org/showthread.php?t=318091&highlight=install+clamav")

Good Luck.

---

### Post by bodhi.zazen on 2007-08-10
Yes, AV on Linux is essentially useless.

There are no know linux viruses "in the wild" so there is nothing to scan for.

In addition Antivirus is reactive not proactive meaning it can not protect you from the next Linux virus until AFTER it is released, not before.

The only potential use of linux antivirus is to "protect" windows or if you are running a mail server, and even then, IMO, Windows antivirus is better then Linux antivirus.

If you would like to learn a little about Ubuntu  security, see this link :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

