---
title: "Problems with Apt"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Morrghan on 2007-02-04
Ok, I got this message as I was trying to open the package manager to install firefox. I had previously tried to run Automatix, but it took forever and did some rather strange things. Ie: Taking forever to install something (3 hours) to the point where I had to restart to get anything to work right again. This is the message I got as I tried to install firefox.

"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

Now, unless there is something running that I cannot see...there is nothing going on. Help?:confused:

---

### Post by riven0 on 2007-02-04
Do you happen to have Synaptic Package Manager or a terminal with sudo access open?

---

### Post by Morrghan on 2007-02-04
Not that I can tell, there is no terminal window open, and I have not opened synaptic. I've rebooted as well as completely shut down and restarted as well.

---

### Post by seshomaru samma on 2007-02-05
Try 
```
sudo apt-get update
```
and then
```
sudo apt-get install -f
```
if you still get the same results post the output of
```
sudo ps ax
```

---

### Post by raul_ on 2007-02-05
It's generally not a good idea interrupting a package management system while it's working. When they crash these sort of things happen. Sucks. You can also try 

```

dpkg -configure -a

```

I don't think a apt-get update will work...it will give you the same error. 

And the command in the post above is

```

ps aux

```

---

### Post by closetpirate on 2007-02-05
if all else fails kill the package managers and finish one task before another

---

### Post by Morrghan on 2007-02-05
Ok I did the things you said, seshomaru samma and was told what was wrong. Here is the output of that

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
lilah@Cameo:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege"

Also, Raul_ I did as you said and here is the output of that. 

lilah@Cameo:~$ sudo ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1564   524 ?        S    Feb04   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   Feb04   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    Feb04   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   Feb04   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   Feb04   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kacpid]
root       119  0.0  0.0      0     0 ?        S    Feb04   0:00 [pdflush]
root       120  0.0  0.0      0     0 ?        S    Feb04   0:00 [pdflush]
root       122  0.0  0.0      0     0 ?        S<   Feb04   0:00 [aio/0]
root       121  0.0  0.0      0     0 ?        S    Feb04   0:00 [kswapd0]
root       709  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kseriod]
root      1796  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ata/0]
root      1797  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ata_hotplug/0]
root      1800  0.0  0.0      0     0 ?        S<   Feb04   0:00 [scsi_eh_0]
root      1801  0.0  0.0      0     0 ?        S<   Feb04   0:00 [scsi_eh_1]
root      1853  0.0  0.0      0     0 ?        S<   Feb04   0:00 [khubd]
root      1869  0.0  0.0      0     0 ?        S    Feb04   0:00 [khpsbpkt]
root      1898  0.0  0.0      0     0 ?        S    Feb04   0:00 [knodemgrd_0]
root      1984  0.0  0.0      0     0 ?        S    Feb04   0:00 [kjournald]
root      2216  0.0  0.1   2436   920 ?        S<s  Feb04   0:00 /sbin/udevd --d
root      3084  0.0  0.0      0     0 ?        S    Feb04   0:00 [shpchpd_event]
dhcp      3591  0.0  0.1   2336   596 ?        S<s  Feb04   0:00 dhclient3 -pf /
root      3937  0.0  0.2   2152  1192 ?        Ss   Feb04   0:00 /usr/sbin/acpid
root      4056  0.0  0.0   1684   500 ?        Ss   Feb04   0:00 /bin/dd bs 1 if
klog      4058  0.0  0.2   2424  1352 ?        Ss   Feb04   0:00 /sbin/klogd -P
104       4077  0.0  0.1   2192   816 ?        Ss   Feb04   0:00 /usr/bin/dbus-d
108       4092  0.0  1.0   6876  5468 ?        Ss   Feb04   0:01 /usr/sbin/hald
root      4093  0.0  0.1   2720   976 ?        S    Feb04   0:00 hald-runner
108       4098  0.0  0.1   2008   796 ?        S    Feb04   0:00 /usr/lib/hal/ha
root      4100  0.0  0.2   2900  1104 ?        S    Feb04   0:00 /usr/lib/hal/ha
108       4153  0.0  0.1   2008   796 ?        S    Feb04   0:00 /usr/lib/hal/ha
108       4161  0.0  0.1   2008   820 ?        S    Feb04   0:00 /usr/lib/hal/ha
108       4162  0.0  0.1   2008   820 ?        S    Feb04   0:00 /usr/lib/hal/ha
hplip     4192  0.0  0.1  12876   920 ?        Ssl  Feb04   0:00 /usr/sbin/hpiod
hplip     4195  0.0  0.9   9408  4672 ?        S    Feb04   0:00 python /usr/sbi
root      4316  0.0  0.1   1968   708 ?        Ss   Feb04   0:00 hcid: processin
root      4322  0.0  0.0   1620   460 ?        Ss   Feb04   0:00 /usr/sbin/sdpd
root      4331  0.0  0.0      0     0 ?        S<   Feb04   0:00 [krfcommd]
root      4344  0.0  0.0   1628   300 ?        Ss   Feb04   0:00 /sbin/mdadm -F
daemon    4378  0.0  0.0   1800   396 ?        Ss   Feb04   0:00 /usr/sbin/atd
root      4391  0.0  0.1   2116   840 ?        Ss   Feb04   0:00 /usr/sbin/cron
root      4738  0.0  0.1   2744   628 ?        Ss   Feb04   0:00 /usr/bin/kdm
root      4788  0.0  0.0   1564   496 tty1     Ss+  Feb04   0:00 /sbin/getty 384
root      4789  0.0  0.0   1560   492 tty2     Ss+  Feb04   0:00 /sbin/getty 384
root      4790  0.0  0.0   1564   492 tty3     Ss+  Feb04   0:00 /sbin/getty 384
root      4791  0.0  0.0   1564   492 tty4     Ss+  Feb04   0:00 /sbin/getty 384
root      4795  0.2  4.1  26956 21268 tty7     Ss+  Feb04   1:34 /usr/bin/X -br
root      4792  0.0  0.0   1564   496 tty5     Ss+  Feb04   0:00 /sbin/getty 384
root      4796  0.0  0.0   1560   492 tty6     Ss+  Feb04   0:00 /sbin/getty 384
root      4807  0.0  0.2   3676  1360 ?        S    Feb04   0:00 -:0
lilah     4836  0.0  0.3   4180  1684 ?        Ss   Feb04   0:00 /bin/sh /usr/bi
lilah     4873  0.0  0.1   4336   688 ?        Ss   Feb04   0:00 /usr/bin/ssh-ag
lilah     4876  0.0  0.1   2716   652 ?        S    Feb04   0:00 /usr/bin/dbus-l
lilah     4877  0.0  0.0   2080   428 ?        Ss   Feb04   0:00 dbus-daemon --f
lilah     4905  0.0  0.8  25128  4132 ?        Ss   Feb04   0:00 kdeinit Running
lilah     4908  0.0  0.6  24584  3068 ?        S    Feb04   0:01 dcopserver [kde
lilah     4910  0.0  1.7  25916  8908 ?        S    Feb04   0:00 klauncher [kdei
lilah     4912  0.0  3.5  33696 17868 ?        S    Feb04   0:05 kded [kdeinit]
lilah     4914  0.0  0.2   2744  1484 ?        S    Feb04   0:00 /usr/lib/gamin/
lilah     4922  0.0  1.9  23604 10144 ?        S    Feb04   0:10 /usr/bin/artsd
lilah     4924  0.0  1.9  25836  9780 ?        S    Feb04   0:00 kaccess [kdeini
lilah     4927  0.0  0.0   1548   340 ?        S    Feb04   0:00 kwrapper ksmser
lilah     4929  0.0  1.9  25920 10148 ?        S    Feb04   0:00 ksmserver [kdei
lilah     4931  0.0  2.6  28740 13236 ?        S    Feb04   0:03 kwin [kdeinit]
lilah     4933  0.0  3.1  30104 16068 ?        S    Feb04   0:02 kdesktop [kdein
lilah     4935  0.0  3.4  32420 17628 ?        S    Feb04   0:08 kicker [kdeinit
lilah     4938  0.0  2.3  27160 12024 ?        S    Feb04   0:00 kbluetoothd --d
lilah     4940  0.0  2.2  26704 11524 ?        S    Feb04   0:00 klipper [kdeini
lilah     4942  0.0  2.7  29716 13880 ?        S    Feb04   0:05 adept_notifier
lilah     4946  0.0  2.9  30888 14960 ?        S    Feb04   0:00 kio_uiserver [k
lilah     4953  0.0  2.9  29992 14908 ?        S    Feb04   0:00 kmix [kdeinit]
lilah     4954  0.0  3.0  28836 15324 ?        S    Feb04   0:00 katapult -sessi
lilah     4957  0.0  2.5  27056 12988 ?        S    Feb04   0:00 kwalletmanager
lilah     4963  0.0  2.6  33468 13220 ?        S    Feb04   0:00 knotify [kdeini
lilah     4967  0.0  0.6  16640  3124 ?        S    Feb04   0:00 /usr/bin/kdesud
lilah     4999  0.0  6.5  82788 33424 ?        S    Feb04   0:15 kopete -caption
root      5184  0.0  1.5  21292  7828 ?        S    Feb04   0:00 /usr/bin/artsd
lilah     5522  0.0  1.5  26368  8128 ?        S    Feb04   0:00 kio_file [kdein
cupsys    6407  0.0  0.3   4324  1764 ?        SNs  07:37   0:00 /usr/sbin/cupsd
syslog    6890  0.0  0.1   1764   708 ?        SNs  07:37   0:00 /sbin/syslogd -
lilah     6901  3.1  6.1  45848 31076 ?        S    08:25   0:06 konqueror [kdei
lilah     6902  0.0  1.5  26368  8020 ?        S    08:25   0:00 kio_file [kdein
lilah     6903  0.0  1.5  26368  8020 ?        S    08:25   0:00 kio_file [kdein
lilah     6904  0.0  1.5  26368  8016 ?        S    08:25   0:00 kio_file [kdein
lilah     6905  0.0  1.5  26368  8016 ?        S    08:25   0:00 kio_file [kdein
lilah     6906  0.0  1.8  52040  9580 ?        S    08:25   0:00 kio_http [kdein
lilah     6911  0.0  2.2  54064 11184 ?        S    08:25   0:00 kio_http [kdein
lilah     6922  0.0  1.8  51948  9464 ?        S    08:25   0:00 kio_http [kdein
lilah     6923  0.0  1.8  51948  9472 ?        S    08:25   0:00 kio_http [kdein
lilah     6924  0.0  1.8  51948  9424 ?        S    08:25   0:00 kio_http [kdein
lilah     6940  0.0  1.8  51948  9420 ?        S    08:26   0:00 kio_http [kdein
lilah     6986  0.0  1.8  51948  9404 ?        S    08:26   0:00 kio_http [kdein
lilah     6987  0.0  1.8  51948  9404 ?        S    08:26   0:00 kio_http [kdein
lilah     6989  0.0  1.7  27312  8960 ?        S    08:26   0:00 kio_http [kdein
lilah     6995  0.8  3.0  31664 15508 ?        S    08:27   0:00 konsole [kdeini
lilah     6996  0.1  0.6   5612  3300 pts/1    Ss   08:27   0:00 /bin/bash
root      7032  0.0  0.2   2396  1020 pts/1    R+   08:28   0:00 ps aux
lilah@Cameo:~$

I wish the damned thing hadn't crashed. Even with these issues though....still 1 million times better than windows.

---

### Post by jvc26 on 2007-02-05
To run the dpkg --configure -a command properly you need to enter:
```

sudo dpkg --configure -a

```
Il

---

### Post by Morrghan on 2007-02-05
Ok, I re-ran Automatix and deselected the Nvidia drivers and it went though just fine. It freed up the issue and was able to work.

---

