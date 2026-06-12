---
title: "vmware-server problem,"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by b0bby on 2006-10-20
Hi,
I just installed ubuntu 6.06 server on a IBM eServer xSeries 100,
and downloaded VMware-server, installed it, and it went just fine, didnt complain about anything. Then I installed WMware-server-MUI, it went fine too, and after the config-files were run, i can connect via the browser interface, but the vmware-server-console that is running on my client (ubuntu 6.06) cant connect.

**Unable to connect to the remote host: Cannot connect to host 192.168.1.12: Connection refused.** it says.

anyone have any tips or tricks to solve my problem?


from 'ps aux' regarding vmware-processes on the server-side.

[B]root      5455  0.0  0.0   1412   160 pts/0    S    19:51   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      5461  1.1  2.6  16236 13656 ?        Ss   19:51   0:00 /usr/sbin/vmware-serverd -s -d
root      5572  0.0  0.9  33136  4964 ?        Ss   19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache
www-data  5575  0.2  0.8  32964  4504 ?        S    19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache
www-data  5579  0.0  0.7  33136  3832 ?        S    19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache
www-data  5580  0.7  2.0  38812 10628 ?        S    19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache
www-data  5581  0.9  2.7  42208 14036 ?        S    19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache
www-data  5582  0.0  0.6  33136  3512 ?        S    19:51   0:00 /usr/lib/vmware-mui/apache/bin/httpd.vmware -DSSL -DSSL_ONLY -DGSX -d /usr/lib/vmware-mui/apache[/B]

---

### Post by happynix on 2006-10-21
Check that you are connecting to he right port with your client

Try
   more /etc/xinetd.d/vmware-authd
to see the port number (mine runs out of xinetd YMMV)

Then make sure your connect to other server says something like this:
server001:992

replace :992 with :<whateverportyouarelisteningon>

---

