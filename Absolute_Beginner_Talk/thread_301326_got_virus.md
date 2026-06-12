---
title: "got virus?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-11-16
Hey guys!
well today while runngin avast i noticed i had 1 infected file!
 WHAT DO I DO?! 
PLEASE HELP!!!!!!!

---

### Post by bodhi.zazen on 2006-11-16
In my experience Linux virus scans often return false positives.

[list=number][*]When was the last time you scanned ?
[*]What file is infected and where is it located?
[*]Details of your reported virus (name).[/list]

---

### Post by Linux&amp;Lizards on 2006-11-17
I scan at least once a day and tonight is when i got the message with avast.
How do i locate the file?

If i just reinstall ubuntu will it remove the virus?

---

### Post by slimdog360 on 2006-11-17
Id be pretty sure its not a virus, but just to be safe google the name of the file, or what ever avast recognises it as, and see what it has to say. Also could you post the name of the file here as someone may have had the same experience and knows what it is.

---

### Post by Mimsy on 2006-11-17
Are you saying Avast didn't clean or quarantine the virus? That would be a first... it has always done either of those for me.

We need a bit more information in order to be able to help you. What's the name of the virus, and where did Avast say it is? Avast keeps logs, it should be fairly easy foor you to get the information out of the log so you can copy-paste it on here. The more details you give us, the better wecan help. :)

/Mimsy

---

### Post by wieman01 on 2006-11-17
Just be cool & don't worry. :-) Linux is not vulnerable to a great number of viruses. This is likely to be a Windows virus which won't do any harm anyway. So DON'T reinstall please. You would be wasting your time.

Question: Do you happen to know the file name of the virus?

---

### Post by Linux&amp;Lizards on 2006-11-17
how do in know the name of the virus?
I think all avast says is one infected file.

im running a scan again to see what it comes up with.

---

### Post by Linux&amp;Lizards on 2006-11-17
this is what it says






# scanned files:        1613
# scanned directories:  302
# infected files:       1
# total file size:      281.4 MB
# virus database:       0630-2 26.07.2006
# test elapsed:         2m:8s 907ms
#

---

### Post by Linux&amp;Lizards on 2006-11-17
so then what do i do from here?

---

### Post by bodhi.zazen on 2006-11-17
In a terminal:

locate avast.log
locate avast.stat

Open and post contents of those 2 files please.

---

### Post by wieman01 on 2006-11-17
This is not a virus... Look at the size of the file: 281.4 MB. It's a false positive as mentioned earlier. Just cannot remember what this refers to again. I have seen a similar post before. But I doubt it's a virus at all.

---

### Post by Linux&amp;Lizards on 2006-11-17
nothing happens

---

### Post by bodhi.zazen on 2006-11-17
You will need to either upgrade to avast professional or scan with an alternate ([f-prot](http://doc.gwos.org/index.php/F-prot_gtk), [clam](http://doc.gwos.org/index.php/ClamAV)).

I have used them both. Both give false positives.

EDIT: **IF** this is a virus it is almost certainly of the windows type and no threat to your system. It is likely an attachemt to some document or file you downloaded.

Since we know the size of the file we may be able to find it with:

ls -lahR / | grep 281.4

Then scan that file here [Avast scan online](http://onlinescan.avast.com/)

---

### Post by Linux&amp;Lizards on 2006-11-17
> **bodhi.zazen said:**
> You will need to either upgrade to avast professional or scan with an alternate ([f-prot](http://doc.gwos.org/index.php/F-prot_gtk), [clam](http://doc.gwos.org/index.php/ClamAV)).

I have used them both. Both give false positives.

EDIT: **IF** this is a virus it is almost certainly of the windows type and no threat to your system. It is likely an attachemt to some document or file you downloaded.

Since we know the size of the file we may be able to find it with:

ls -lahR / | grep 281.4

Then scan that file here [Avast scan online](http://onlinescan.avast.com/)

ok i scanned with ls -lahR /
what am i looking for?
this is what happened 
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 867
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 868
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 869
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 870
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 871
-rw-r--r--   1 root root 2.4K 2006-11-14 20:21 872
-rw-r--r--   1 root root 9.2K 2006-11-14 20:21 873
-rw-r--r--   1 root root 9.5K 2006-11-14 20:21 874
-rw-r--r--   1 root root 9.2K 2006-11-14 20:21 875
-rw-r--r--   1 root root 9.5K 2006-11-14 20:21 876
-rw-r--r--   1 root root 9.2K 2006-11-14 20:21 877
-rw-r--r--   1 root root 9.3K 2006-11-14 20:22 878
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 879
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 880
-rw-r--r--   1 root root 9.0K 2006-11-14 20:22 881
-rw-r--r--   1 root root 9.4K 2006-11-14 20:22 882
-rw-r--r--   1 root root 9.0K 2006-11-14 20:22 883
-rw-r--r--   1 root root 9.1K 2006-11-14 20:22 884
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 885
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 886
-rw-r--r--   1 root root 9.6K 2006-11-14 20:22 887
-rw-r--r--   1 root root 9.4K 2006-11-14 20:22 888
-rw-r--r--   1 root root 9.1K 2006-11-14 20:22 889
-rw-r--r--   1 root root  11K 2006-11-14 20:22 890
-rw-r--r--   1 root root 9.1K 2006-11-14 20:22 891
-rw-r--r--   1 root root 9.3K 2006-11-14 20:22 892
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 893
-rw-r--r--   1 root root 9.2K 2006-11-14 20:22 894
-rw-r--r--   1 root root 8.7K 2006-11-14 20:22 895
-rw-r--r--   1 root root 9.1K 2006-11-14 20:22 896

/var/lib/scrollkeeper/tr:
total 84K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  28K 2006-11-14 20:22 scrollkeeper_cl.xml
-rw-r--r--   1 root root  46K 2006-11-14 20:22 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/ug:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/uk:
total 104K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  38K 2006-11-14 20:23 scrollkeeper_cl.xml
-rw-r--r--   1 root root  51K 2006-11-14 20:23 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/ur:
total 84K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  28K 2006-11-14 20:16 scrollkeeper_cl.xml
-rw-r--r--   1 root root  45K 2006-11-14 20:16 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/uz:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/vi:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  27K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  27K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/wa:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  27K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  27K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/wo:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/xh:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/yi:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/yo:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/zh_CN:
total 104K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  31K 2006-11-14 20:22 scrollkeeper_cl.xml
-rw-r--r--   1 root root  58K 2006-11-14 20:22 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/zh_TW:
total 100K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  31K 2006-11-14 20:22 scrollkeeper_cl.xml
-rw-r--r--   1 root root  56K 2006-11-14 20:22 scrollkeeper_extended_cl.xml

/var/lib/scrollkeeper/zu:
total 64K
drwxr-xr-x   2 root root 4.0K 2006-11-12 09:32 .
drwxr-xr-x 108 root root 4.0K 2006-11-14 20:30 ..
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_cl.xml
-rw-r--r--   1 root root  26K 2006-11-12 09:32 scrollkeeper_extended_cl.xml

/var/lib/sgml-base:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-05-30 16:52 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
ls: /var/lib/slocate: Permission denied

/var/lib/snmp:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-04-04 04:47 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..

/var/lib/synaptic:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-05-18 07:20 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..

/var/lib/ucf:
total 36K
drwxr-xr-x  3 root root 4.0K 2006-11-15 08:36 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
drwxr-xr-x  2 root root 4.0K 2006-11-15 08:36 cache
-rw-r--r--  1 root root  386 2006-11-15 08:36 hashfile
-rw-r--r--  1 root root  325 2006-11-15 08:36 hashfile.0
-rw-r--r--  1 root root  212 2006-11-15 08:36 hashfile.1
-rw-r--r--  1 root root  152 2006-11-15 08:36 hashfile.2
-rw-r--r--  1 root root  101 2006-11-15 08:36 hashfile.3
-rw-r--r--  1 root root   52 2006-11-15 08:36 hashfile.4
-rw-r--r--  1 root root    0 2006-11-15 08:36 hashfile.5

/var/lib/ucf/cache:
total 20K
drwxr-xr-x 2 root root 4.0K 2006-11-15 08:36 .
drwxr-xr-x 3 root root 4.0K 2006-11-15 08:36 ..
-rw-r--r-- 1 root root  648 2006-11-15 08:36 :etc:clamav:clamd.conf
-rw-r--r-- 1 root root  435 2006-11-15 08:36 :etc:clamav:freshclam.conf
-rw-r--r-- 1 root root 1.1K 2006-05-30 16:55 :etc:foomatic:filter.conf

/var/lib/update-manager:
total 12K
drwxr-xr-x  2 root root 4.0K 2006-11-14 18:25 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
-rw-r--r--  1 root root 1.6K 2006-11-15 07:43 meta-release

/var/lib/update-notifier:
total 12K
drwxr-xr-x  3 root root 4.0K 2006-05-30 17:01 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
-rw-r--r--  1 root root    0 2006-11-16 21:10 dpkg-run-stamp
drwxr-xr-x  2 root root 4.0K 2006-05-26 02:40 user.d

/var/lib/update-notifier/user.d:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2006-05-26 02:40 .
drwxr-xr-x 3 root root 4.0K 2006-05-30 17:01 ..

/var/lib/urandom:
total 12K
drwxr-xr-x  2 root root 4.0K 2006-11-16 07:44 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
-rw-------  1 root root 4.0K 2006-11-16 07:44 random-seed

/var/lib/x11:
total 32K
drwxr-xr-x  2 root root 4.0K 2006-05-30 16:54 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
-rw-r--r--  1 root root   36 2006-05-30 16:54 X.md5sum
-rw-r--r--  1 root root   53 2006-05-30 16:54 xorg.conf.md5sum
-rw-r--r--  1 root root   13 2006-05-30 16:54 xorg.conf.roster
-rw-r--r--  1 root root   13 2006-05-30 16:54 X.roster
-rw-r--r--  1 root root   59 2006-05-30 16:51 Xwrapper.config.md5sum
-rw-r--r--  1 root root   11 2006-05-30 16:51 Xwrapper.config.roster

/var/lib/xkb:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-11-16 07:45 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..

/var/lib/xml-core:
total 40K
drwxr-xr-x  2 root root 4.0K 2006-11-14 20:31 .
drwxr-xr-x 43 root root 4.0K 2006-11-15 08:56 ..
-rw-r--r--  1 root root 3.1K 2006-11-14 20:31 catalog
-rw-r--r--  1 root root 9.0K 2006-05-30 16:56 docbook-xml
-rw-r--r--  1 root root  152 2006-11-14 20:31 openoffice.org-common
-rw-r--r--  1 root root  157 2006-05-30 16:56 scrollkeeper
-rw-r--r--  1 root root 1.2K 2006-05-30 16:56 sgml-data
-rw-r--r--  1 root root  304 2006-05-30 16:56 xml-core

/var/local:
total 8.0K
drwxrwsr-x  2 root staff 4.0K 2006-05-22 06:00 .
drwxr-xr-x 14 root root  4.0K 2006-05-30 17:02 ..

/var/lock:
total 8.0K
drwxrwxrwt  3 root root   80 2006-11-16 07:44 .
drwxr-xr-x 14 root root 4.0K 2006-05-30 17:02 ..
-rw-r-----  1 root root   20 2006-11-16 07:44 evms-engine
drwx------  2 root root   40 2006-11-16 07:44 lvm
ls: /var/lock/lvm: Permission denied

/var/log:
total 3.7M
drwxr-xr-x  8 root   root   4.0K 2006-11-17 07:35 .
drwxr-xr-x 14 root   root   4.0K 2006-05-30 17:02 ..
-rw-r-----  1 root   adm    2.4K 2006-11-16 07:45 acpid
-rw-r-----  1 root   adm     34K 2006-11-17 07:45 auth.log
-rw-r-----  1 root   adm     235 2006-11-12 09:26 auth.log.0
-rw-r--r--  1 root   root    35K 2006-05-30 16:51 bootstrap.log
-rw-rw-r--  1 root   utmp      0 2006-05-30 16:49 btmp
drwxr-xr-x  2 clamav clamav 4.0K 2006-11-15 08:36 clamav
drwxr-xr-x  2 root   root   4.0K 2006-11-17 07:35 cups
-rw-r-----  1 root   adm    439K 2006-11-17 07:51 daemon.log
-rw-r-----  1 root   adm    1.9K 2006-11-12 09:26 daemon.log.0
-rw-r-----  1 root   adm     27K 2006-11-16 07:45 debug
-rw-r-----  1 root   adm    3.0K 2006-11-12 09:17 debug.0
-rw-r--r--  1 root   root    17K 2006-11-16 07:44 dmesg
-rw-r-----  1 root   adm    917K 2006-11-16 21:10 dpkg.log
-rw-r--r--  1 root   root    17K 2006-11-15 20:41 evms-engine.1.log
-rw-r--r--  1 root   root    17K 2006-11-15 10:17 evms-engine.2.log
-rw-r--r--  1 root   root    17K 2006-11-14 20:35 evms-engine.3.log
-rw-r--r--  1 root   root    17K 2006-11-14 18:12 evms-engine.4.log
-rw-r--r--  1 root   root    17K 2006-11-14 18:11 evms-engine.5.log
-rw-r--r--  1 root   root    17K 2006-11-13 14:19 evms-engine.6.log
-rw-r--r--  1 root   root    17K 2006-11-12 16:49 evms-engine.7.log
-rw-r--r--  1 root   root    17K 2006-11-12 14:05 evms-engine.8.log
-rw-r--r--  1 root   root    17K 2006-11-12 09:16 evms-engine.9.log
-rw-r--r--  1 root   root    17K 2006-11-16 07:44 evms-engine.log
-rw-r--r--  1 root   root    24K 2006-11-15 08:36 faillog
-rw-r--r--  1 root   root   2.5K 2006-05-30 17:01 fontconfig.log
drwxr-xr-x  2 root   root   4.0K 2006-11-16 07:45 gdm
drwxr-xr-x  2 root   root   4.0K 2006-11-12 09:14 installer
-rw-r-----  1 root   adm    377K 2006-11-16 07:45 kern.log
-rw-r-----  1 root   adm     29K 2006-11-12 09:17 kern.log.0
-rw-rw-r--  1 root   utmp   286K 2006-11-16 07:45 lastlog
-rw-r--r--  1 root   root      0 2006-11-12 09:16 lpr.log
-rw-r--r--  1 root   root      0 2006-11-12 09:16 mail.err
-rw-r--r--  1 root   root      0 2006-11-12 09:16 mail.info
-rw-r--r--  1 root   root      0 2006-11-12 09:16 mail.log
-rw-r--r--  1 root   root      0 2006-11-12 09:16 mail.warn
-rw-r-----  1 root   adm    400K 2006-11-17 07:35 messages
-rw-r-----  1 root   adm     28K 2006-11-12 09:27 messages.0
drwxr-sr-x  2 news   news   4.0K 2006-11-12 09:16 news
-rw-r--r--  1 root   root   283K 2006-11-14 20:30 scrollkeeper.log
-rw-r-----  1 root   adm    2.5K 2006-11-17 07:51 syslog
-rw-r-----  1 root   adm    180K 2006-11-17 07:35 syslog.0
-rw-r-----  1 root   adm     21K 2006-11-16 07:51 syslog.1.gz
-rw-r-----  1 root   adm     14K 2006-11-15 07:35 syslog.2.gz
-rw-r-----  1 root   adm     12K 2006-11-14 18:18 syslog.3.gz
-rw-r-----  1 root   adm     26K 2006-11-13 14:25 syslog.4.gz
-rw-r-----  1 root   adm    6.9K 2006-11-12 09:22 syslog.5.gz
-rw-r--r--  1 root   root   269K 2006-11-16 07:44 udev
drwxr-xr-x  2 root   root   4.0K 2006-05-29 03:46 unattended-upgrades
-rw-r-----  1 root   adm     44K 2006-11-16 19:43 user.log
-rw-r-----  1 root   adm    2.1K 2006-11-12 09:26 user.log.0
-rw-r--r--  1 root   root      0 2006-11-12 09:16 uucp.log
-rw-rw-r--  1 root   utmp   122K 2006-11-17 07:48 wtmp
-rw-r--r--  1 root   root    308 2006-05-30 16:55 wvdialconf.log
-rw-r--r--  1 root   root    42K 2006-11-17 07:45 Xorg.0.log
-rw-r--r--  1 root   root    42K 2006-11-15 21:45 Xorg.0.log.old

/var/log/clamav:
total 12K
drwxr-xr-x 2 clamav clamav 4.0K 2006-11-15 08:36 .
drwxr-xr-x 8 root   root   4.0K 2006-11-17 07:35 ..
-rw-r----- 1 clamav adm    1.4K 2006-11-15 08:43 freshclam.log

/var/log/cups:
total 40K
drwxr-xr-x 2 root   root    4.0K 2006-11-17 07:35 .
drwxr-xr-x 8 root   root    4.0K 2006-11-17 07:35 ..
-rw-r----- 1 cupsys lpadmin    0 2006-11-17 07:35 access_log
-rw-r--r-- 1 cupsys lp       162 2006-11-16 19:54 access_log.1.gz
-rw-r--r-- 1 cupsys lp       147 2006-11-15 10:09 access_log.2.gz
-rw-r--r-- 1 cupsys lp       125 2006-11-14 20:37 access_log.3.gz
-rw-r--r-- 1 cupsys lp       146 2006-11-12 14:32 access_log.4.gz
-rw-r----- 1 cupsys lpadmin    0 2006-11-16 07:50 error_log
-rw-r--r-- 1 cupsys lp       125 2006-11-16 07:45 error_log.1.gz
-rw-r--r-- 1 cupsys lp        96 2006-11-14 20:35 error_log.2.gz
-rw-r--r-- 1 cupsys lp        97 2006-11-14 18:12 error_log.3.gz
-rw-r--r-- 1 cupsys lp       131 2006-11-13 14:19 error_log.4.gz
-rw-r----- 1 cupsys lpadmin    0 2006-11-12 09:17 page_log

/var/log/gdm:
total 28K
drwxr-xr-x 2 root root 4.0K 2006-11-16 07:45 .
drwxr-xr-x 8 root root 4.0K 2006-11-17 07:35 ..
-rw-r--r-- 1 root root 2.0K 2006-11-17 07:45 :0.log
-rw-r--r-- 1 root root 1.7K 2006-11-15 21:45 :0.log.1
-rw-r--r-- 1 root root 1.6K 2006-11-15 10:17 :0.log.2
-rw-r--r-- 1 root root 1.8K 2006-11-15 07:56 :0.log.3
-rw-r--r-- 1 root root 1.7K 2006-11-14 20:13 :0.log.4

/var/log/installer:
total 140K
drwxr-xr-x 2 root root 4.0K 2006-11-12 09:14 .
drwxr-xr-x 8 root root 4.0K 2006-11-17 07:35 ..
-rw------- 1 root root  85K 2006-11-12 08:56 partman
-rw------- 1 root root  35K 2006-11-12 09:14 syslog
-rw------- 1 root root   16 2006-11-12 08:53 version

/var/log/news:
total 8.0K
drwxr-sr-x 2 news news 4.0K 2006-11-12 09:16 .
drwxr-xr-x 8 root root 4.0K 2006-11-17 07:35 ..
-rw-r--r-- 1 root news    0 2006-11-12 09:16 news.crit
-rw-r--r-- 1 root news    0 2006-11-12 09:16 news.err
-rw-r--r-- 1 root news    0 2006-11-12 09:16 news.notice

/var/log/unattended-upgrades:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2006-05-29 03:46 .
drwxr-xr-x 8 root root 4.0K 2006-11-17 07:35 ..

/var/mail:
total 8.0K
drwxrwsr-x  2 root mail 4.0K 2006-05-30 16:49 .
drwxr-xr-x 14 root root 4.0K 2006-05-30 17:02 ..

/var/opt:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-05-30 16:49 .
drwxr-xr-x 14 root root 4.0K 2006-05-30 17:02 ..

/var/run:
total 44K
drwxr-xr-x 11 root       root        540 2006-11-16 19:43 .
drwxr-xr-x 14 root       root       4.0K 2006-05-30 17:02 ..
srw-rw-rw-  1 root       root          0 2006-11-16 07:45 acpid.socket
-rw-r--r--  1 root       root          5 2006-11-16 07:45 atd.pid
drwxr-xr-x  2 root       mcmahon      60 2006-11-17 07:30 console
-rw-r--r--  1 root       root          5 2006-11-16 07:45 crond.pid
----------  1 root       root          0 2006-11-16 07:45 crond.reboot
drwxr-xr-x  3 cupsys     lp          100 2006-11-17 07:35 cups
drwxr-xr-x  2 messagebus messagebus   80 2006-11-16 07:45 dbus
-rw-r--r--  1 root       root          0 2006-11-16 07:44 dhclient.ath0.pid
-rw-r--r--  1 root       root          5 2006-11-16 07:44 dhclient.eth0.pid
-rw-r--r--  1 root       root          0 2006-11-16 07:44 dhclient.eth1.pid
-rw-r--r--  1 root       root          5 2006-11-16 07:45 dhclient.eth2.pid
-rw-r--r--  1 root       root          0 2006-11-16 07:44 dhclient.wlan0.pid
-rw-r--r--  1 root       root          5 2006-11-16 07:45 gdm.pid
drwxr-xr-x  2 haldaemon  haldaemon    60 2006-11-16 07:45 hal
-rw-r--r--  1 root       root       1.7K 2006-11-16 07:45 hotkey-setup
drwxr-xr-x  2 hplip      root        120 2006-11-16 07:45 hplip
drwxr-xr-x  2 klog       klog        100 2006-11-16 07:45 klogd
-rw-r--r--  1 root       root          5 2006-11-16 07:45 mdadm.pid
drwxr-xr-x  2 root       root         60 2006-11-16 07:45 network
drwxrwxr-x  2 root       utmp         40 2006-11-16 07:44 screen
srw-rw-rw-  1 root       root          0 2006-11-16 07:45 sdp
drwx------  3 root       root         60 2006-11-16 19:37 sudo
srwxr-xr-x  1 root       root          0 2006-11-16 19:43 synaptic.socket
-rw-r--r--  1 root       root          5 2006-11-17 07:35 syslogd.pid
-rw-rw-r--  1 root       utmp       4.9K 2006-11-17 07:48 utmp

/var/run/console:
total 0
drwxr-xr-x  2 root mcmahon  60 2006-11-17 07:30 .
drwxr-xr-x 11 root root    540 2006-11-16 19:43 ..
-rw-r--r--  1 root mcmahon   0 2006-11-16 07:45 mcmahon:7

/var/run/cups:
total 4.0K
drwxr-xr-x  3 cupsys lp      100 2006-11-17 07:35 .
drwxr-xr-x 11 root   root    540 2006-11-16 19:43 ..
drwx--x--x  2 cupsys lpadmin  60 2006-11-17 07:50 certs
-rw-r--r--  1 root   root      5 2006-11-17 07:35 cupsd.pid
srwxrwxrwx  1 root   root      0 2006-11-17 07:35 cups.sock
ls: /var/run/cups/certs: Permission denied

/var/run/dbus:
total 4.0K
drwxr-xr-x  2 messagebus messagebus  80 2006-11-16 07:45 .
drwxr-xr-x 11 root       root       540 2006-11-16 19:43 ..
-rw-r--r--  1 root       root         5 2006-11-16 07:45 pid
srwxrwxrwx  1 root       root         0 2006-11-16 07:45 system_bus_socket

/var/run/hal:
total 4.0K
drwxr-xr-x  2 haldaemon haldaemon  60 2006-11-16 07:45 .
drwxr-xr-x 11 root      root      540 2006-11-16 19:43 ..
-rw-r--r--  1 root      root        5 2006-11-16 07:45 hald.pid

/var/run/hplip:
total 16K
drwxr-xr-x  2 hplip root 120 2006-11-16 07:45 .
drwxr-xr-x 11 root  root 540 2006-11-16 19:43 ..
-rw-r--r--  1 hplip lp     5 2006-11-16 07:45 hpiod.pid
-rw-r--r--  1 hplip lp     6 2006-11-16 07:45 hpiod.port
-rw-r--r--  1 hplip lp     5 2006-11-16 07:45 hpssd.pid
-rw-r--r--  1 hplip lp     6 2006-11-16 07:45 hpssd.port

/var/run/klogd:
total 8.0K
drwxr-xr-x  2 klog klog 100 2006-11-16 07:45 .
drwxr-xr-x 11 root root 540 2006-11-16 19:43 ..
-rw-r--r--  1 klog klog   5 2006-11-16 07:45 klogd.pid
prwx------  1 klog klog   0 2006-11-16 07:45 kmsg
-rw-r--r--  1 root root   5 2006-11-16 07:45 kmsgpipe.pid

/var/run/network:
total 4.0K
drwxr-xr-x  2 root root  60 2006-11-16 07:45 .
drwxr-xr-x 11 root root 540 2006-11-16 19:43 ..
-rw-r--r--  1 root root  26 2006-11-16 07:45 ifstate

/var/run/screen:
total 0
drwxrwxr-x  2 root utmp  40 2006-11-16 07:44 .
drwxr-xr-x 11 root root 540 2006-11-16 19:43 ..
ls: /var/run/sudo: Permission denied

/var/spool:
total 24K
drwxr-xr-x  6 root   root   4.0K 2006-05-30 16:53 .
drwxr-xr-x 14 root   root   4.0K 2006-05-30 17:02 ..
drwxr-xr-x  2 root   root   4.0K 2006-11-12 09:17 anacron
drwxr-xr-x  5 daemon daemon 4.0K 2006-05-30 16:52 cron
drwx--x---  3 cupsys lp     4.0K 2006-05-30 16:52 cups
lrwxrwxrwx  1 root   root      7 2006-11-12 09:05 mail -> ../mail
drwxr-xr-x  3 root   root   4.0K 2006-05-30 16:53 openoffice

/var/spool/anacron:
total 20K
drwxr-xr-x 2 root root 4.0K 2006-11-12 09:17 .
drwxr-xr-x 6 root root 4.0K 2006-05-30 16:53 ..
-rw------- 1 root root    9 2006-11-17 07:35 cron.daily
-rw------- 1 root root    9 2006-11-12 09:38 cron.monthly
-rw------- 1 root root    9 2006-11-12 09:27 cron.weekly

/var/spool/cron:
total 20K
drwxr-xr-x 5 daemon daemon  4.0K 2006-05-30 16:52 .
drwxr-xr-x 6 root   root    4.0K 2006-05-30 16:53 ..
drwxrwx--T 2 daemon daemon  4.0K 2006-05-30 16:54 atjobs
drwxrwx--T 2 daemon daemon  4.0K 2006-05-08 13:44 atspool
drwx-wx--T 2 root   crontab 4.0K 2005-11-15 03:42 crontabs
ls: /var/spool/cron/atjobs: Permission denied
ls: /var/spool/cron/atspool: Permission denied
ls: /var/spool/cron/crontabs: Permission denied
ls: /var/spool/cups: Permission denied

/var/spool/openoffice:
total 12K
drwxr-xr-x 3 root root 4.0K 2006-05-30 16:53 .
drwxr-xr-x 6 root root 4.0K 2006-05-30 16:53 ..
drwxr-xr-x 3 root root 4.0K 2006-05-30 16:53 uno_packages

/var/spool/openoffice/uno_packages:
total 12K
drwxr-xr-x 3 root root 4.0K 2006-05-30 16:53 .
drwxr-xr-x 3 root root 4.0K 2006-05-30 16:53 ..
drwxr-xr-x 2 root root 4.0K 2006-05-28 12:06 cache

/var/spool/openoffice/uno_packages/cache:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2006-05-28 12:06 .
drwxr-xr-x 3 root root 4.0K 2006-05-30 16:53 ..

/var/tmp:
total 12K
drwxrwxrwt  3 root    root    4.0K 2006-11-15 09:59 .
drwxr-xr-x 14 root    root    4.0K 2006-05-30 17:02 ..
drwx------  2 mcmahon mcmahon 4.0K 2006-11-15 09:59 kdecache-mcmahon

/var/tmp/kdecache-mcmahon:
total 400K
drwx------ 2 mcmahon mcmahon 4.0K 2006-11-15 09:59 .
drwxrwxrwt 3 root    root    4.0K 2006-11-15 09:59 ..
-rw-r--r-- 1 mcmahon mcmahon 384K 2006-11-15 09:59 ksycoca
-rw-r--r-- 1 mcmahon mcmahon  626 2006-11-15 09:59 ksycocastamp
mcmahon@mcmahon-desktop:~$

---

### Post by bodhi.zazen on 2006-11-17
Looking for the "infected file". Use the "pipe" grep to filter the output:

```
ls -lahR / **| grep 281.4**
```

---

### Post by Linux&amp;Lizards on 2006-11-17
i ran avast again and this is what it came up with 
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateActiveUpdate$2.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateActiveUpdate$TransferWatcher.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateActiveUpdate.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateCore$1$1.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateCore$1$Package.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateCore$1.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateCore.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateEngine.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdatePattern.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateResources$1.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/UpdateResources.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/VerifyCurrentTicket$1.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/process/VerifyCurrentTicket.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/AbstractEngineProcessListener.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/Hex.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/HttpTransfer$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/HttpTransfer$Listener.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/HttpTransfer.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/PrepareInstall$1.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/PrepareInstall.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/ProgressTimer.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/SortedProcessChainManager$EnqueuedProcess.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/SortedProcessChainManager.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/SystemInfo.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/ThreatInformationAdapter.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingInformationHandler$1.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingInformationHandler$TicketingInformation.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingInformationHandler.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingStorageAdapter.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingVerificationHandler$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingVerificationHandler$Result.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/TicketingVerificationHandler.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/VulnerabilityPortScanProcess.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/WriteSynchronizedHashMap.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/util/ZipExtract.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/beans/AccountData.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/beans/EncryptedBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/beans/PortVulnerability.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/beans/TicketData.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/beans/Version.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/EngineUpdateException.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/PatternUpdateException.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/ProxyConfig$1.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/ProxyConfig.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/ProxyConfigImplJ4.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/ProxyConfigImplJ5.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/ProxyConfigurationException.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/UpdateCallback.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/UpdateException.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/UpdateImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/activeupdate/UpdateNotRequiredException.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/BootSectorScanProcessImpl$1.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/BootSectorScanProcessImpl.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CleanProcessImpl$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CleanProcessImpl$2.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CleanProcessImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl$2.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl$3.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl$4.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl$PatternDetailsImpl.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/CommonEngineImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/DirectoryInformation.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/FileScanProcessImpl$1.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/FileScanProcessImpl.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/MemoryScanProcessImpl$1.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/MemoryScanProcessImpl.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/PartitionScanProcessImpl$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/PartitionScanProcessImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ProcessCallback.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ProcessSystemCallback.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ProgressCounting.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/QuarantinedResourceImpl.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/Register.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/RestorableResourceCallback.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ScanProcessCallbackImpl$1.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ScanProcessCallbackImpl$ThreatPrototype.class[OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ScanProcessCallbackImpl.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/ScanResultHandler.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/SystemScanProcessImpl$1.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/SystemScanProcessImpl.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/SystemScanProcessor$1.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/SystemScanProcessor.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/VulnerabilityScanProcessImpl$1.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/VulnerabilityScanProcessImpl.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/darwin/EngineImpl.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/linux/EngineImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/solaris/EngineImpl.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/win32/EngineImpl$1.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/lib/engine/win32/EngineImpl.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/portscan/IPortScanWebServicePort.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/portscan/PortBean.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/portscan/PortScanWebService.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/portscan/PortScanWebServiceLocator.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/portscan/PortScanWebServicePort.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/EnvironmentBean.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/HouseCallThreat.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/IHouseCallThreat.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/PersonalizedReportSourceBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ReportSourceBean.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ReportSourceMetadataBean.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ScanDetailBean.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ServerReportSourceBean.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ServiceImplService.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ServiceImplServiceLocator.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ThreatBean.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ThreatInfectionBean.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ThreatInformationBean.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/ThreatRemovalFailedBean.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/VulnerabilityBean.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/threat/VulnerabilityInformationBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/HouseCallTicketing.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/IHouseCallTicketing.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/PaymentProviderBean.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/ServiceImplService.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/ServiceImplServiceLocator.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/TicketBean.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/TicketDetailsBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/TicketPurchaseProcessBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/TicketSessionBean.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/impl/ws/ticketing/TicketTypeBean.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/LocalProxy$1.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/LocalProxy$Cache$1.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/LocalProxy$Cache.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/LocalProxy$Connector.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/LocalProxy.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/util/MachineInfo.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-active.png  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-disabled.png        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-green-active-selected.png   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-green-selected.png  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-red-active-selected.png     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action-red-selected.png    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-action.png [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-clean.png  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-delete.png [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-failed-action-notify.png   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-no-action.png      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/table-open-archive.png   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/tree-contains-selected.png       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/tree-minus.png   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/tree-not-selected.png    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/tree-plus.png    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/hc/applet/icons/tree-selected.png        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/ChunkedInputStream.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPController.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPHttpURLTransport.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPProxy$1.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPProxy$iCall.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPProxy.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPProxyException.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/SOAPTransportException.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/URLConnectionTransport.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/http/ProxyConfig.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/http/SSLThrustAllProvider$1.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/http/SSLThrustAllProvider$TrustManagerFactoryImpl$1.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/http/SSLThrustAllProvider$TrustManagerFactoryImpl.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/trendmicro/soap/http/SSLThrustAllProvider.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/Call.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/Constants.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/Envelope.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/Fault.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/HeaderEntry.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/SOAPException.class    [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/a.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/Base64.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/BaseSerializer.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/BeanSerializer.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/Float.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/SerializerDeserializer.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/TypeMappingRegistry.class     [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/UntypedObject.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/encoding/WSerializable.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/transport/J2SEHTTPTransport.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/com/wingfoot/soap/transport/Transport.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/Attribute.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/PrefixMap.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/Xml.class       [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/io/ParseException.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/io/XMLWriter.class      [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/AbstractXmlParser.class  [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/ParseEvent.class [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/StartTag.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/Tag.class        [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/XmlParser$DefaultParserException.class   [OK]
Archived /home/mcmahon/.java/deployment/cache/javapi/v1.0/jar/hcImpl.jar-50174dc1-38f7425f.zip/org/kxml/parser/XmlParser.class  [OK]
/home/mcmahon/.java/deployment/cache/javapi/v1.0/file/vmchecker.class-7ac16f10-5d11cde7.idx     [OK]
/home/mcmahon/.java/deployment/cache/javapi/v1.0/file/vmchecker.class-7ac16f10-5d11cde7.class   [OK]
/home/mcmahon/.java/deployment/log/plugin150_06.trace   [OK]
/home/mcmahon/.java/deployment/security/trusted.certs   [OK]
/home/mcmahon/wget-log.1        [OK]
/home/mcmahon/.adobe/Acrobat/7.0/UserCache.bin  [OK]
/home/mcmahon/.adobe/Acrobat/7.0/Preferences/reader_prefs       [OK]
/home/mcmahon/.adobe/Acrobat/7.0/Cache/AcroFnt07.lst    [OK]
/home/mcmahon/.qt/.qt_plugins_3.3rc.lock        [OK]
/home/mcmahon/.qt/qt_plugins_3.3rc      [OK]
/home/mcmahon/Ubuntudesktopguide.pdf    [OK]
/home/mcmahon/.gnome/gnome-vfs/.trash_entry_cache       [OK]
/home/mcmahon/.housecall6.6/log/execution0.log  [OK]
/home/mcmahon/.housecall6.6/log/error0.log      [OK]
/home/mcmahon/.housecall6.6/log/engine0.log     [OK]
/home/mcmahon/.housecall6.6/Pattern/lpt$vpn.929 [OK]
/home/mcmahon/.housecall6.6/Pattern/tmaptn.431  [OK]
/home/mcmahon/.housecall6.6/libtmactupdate.so   [OK]
/home/mcmahon/.housecall6.6/AU_Log/TmuDump.txt  [OK]
/home/mcmahon/.housecall6.6/libjsapi.so [OK]
/home/mcmahon/.housecall6.6/x500.db     [OK]
/home/mcmahon/.housecall6.6/AuPatch     [OK]
/home/mcmahon/.housecall6.6/cert5.db    [OK]
/home/mcmahon/.housecall6.6/libpatch.so [OK]
/home/mcmahon/.housecall6.6/libjupdate.so       [OK]
/home/mcmahon/.housecall6.6/aucfg.ini   [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/ini_xml.zip.lock [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/ini_xml.zip      [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/ini_xml.zip.etag [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/server.ini.lock  [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/server.ini       [OK]
/home/mcmahon/.housecall6.6/Update/AU_Cache/housecall65.trendmicro.com/server.ini.etag  [OK]
/home/mcmahon/.housecall6.6/GetServer.ini       [OK]
/home/mcmahon/.housecall6.6/libvsapi.so [OK]
/home/mcmahon/.housecall6.6/local.conf  [OK]
/home/mcmahon/.mcop/random-seed [OK]
/home/mcmahon/.mcop/trader-cache/cache-data-version     [OK]
/home/mcmahon/.mcoprc   [OK]
/home/mcmahon/.wine/drive_c/windows/command/start.exe   [OK]
/home/mcmahon/.wine/drive_c/windows/inf/wine.inf        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/advapi32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/advpack.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/cmd.exe    [OK]
/home/mcmahon/.wine/drive_c/windows/system32/comctl32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/comdlg32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/control.exe        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/crypt32.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/d3d8.dll   [OK]
/home/mcmahon/.wine/drive_c/windows/system32/d3d9.dll   [OK]
/home/mcmahon/.wine/drive_c/windows/system32/dbghelp.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ddeml.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ddhelp.exe [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ddraw.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/dsound.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/dsound.vxd [OK]
/home/mcmahon/.wine/drive_c/windows/system32/explorer.exe       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/gdi32.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/hhctrl.ocx [OK]
/home/mcmahon/.wine/drive_c/windows/system32/imaadp32.acm       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/imagehlp.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/kernel32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/msadp32.acm        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/msg711.acm [OK]
/home/mcmahon/.wine/drive_c/windows/system32/msi.dll    [OK]
/home/mcmahon/.wine/drive_c/windows/system32/msiexec.exe        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/msvcrt.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/notepad.exe        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ntdll.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ole32.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/oleaut32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/olepro32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/opengl32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/progman.exe        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/regsvr32.exe       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/riched20.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/riched32.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/rpcrt4.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/shdocvw.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/shell32.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/shfolder.dll       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/shlwapi.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/urlmon.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/user32.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/version.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/wininet.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/system32/winmm.dll  [OK]
/home/mcmahon/.wine/drive_c/windows/system32/winspool.drv       [OK]
/home/mcmahon/.wine/drive_c/windows/system32/winver.exe [OK]
/home/mcmahon/.wine/drive_c/windows/system32/ws2_32.dll [OK]
/home/mcmahon/.wine/drive_c/windows/system32/wsock32.dll        [OK]
/home/mcmahon/.wine/drive_c/windows/win.ini     [OK]
/home/mcmahon/.wine/drive_c/windows/system.ini  [OK]
/home/mcmahon/.wine/drive_c/windows/notepad.exe [OK]
/home/mcmahon/.wine/drive_c/windows/regedit.exe [OK]
/home/mcmahon/.wine/drive_c/windows/rundll32.exe        [OK]
/home/mcmahon/.wine/drive_c/windows/winebrowser.exe     [OK]
/home/mcmahon/.wine/drive_c/windows/winhelp.exe [OK]
/home/mcmahon/.wine/system.reg  [OK]
/home/mcmahon/.wine/userdef.reg [OK]
/home/mcmahon/.wine/user.reg    [OK]
#
# Statistics:
#
# scanned files:        2085
# scanned directories:  325
# infected files:       1
# total file size:      944.9 MB
# virus database:       0630-2 26.07.2006
# test elapsed:         3m:6s 675ms

---

### Post by Linux&amp;Lizards on 2006-11-17
im just wondering how do i remove it?
is their a tool i can download that will search it out and remove it along with everything it is associated with?

---

### Post by Linux&amp;Lizards on 2006-11-17
Is clamav better?

---

### Post by Linux&amp;Lizards on 2006-11-17
> **bodhi.zazen said:**
> Looking for the "infected file". Use the "pipe" grep to filter the output:

```
ls -lahR / **| grep 281.4**
```

what do you mean pipe?

---

### Post by Mimsy on 2006-11-17
Did you try the command bodhi.zazen posted? If so, what did it turn up?

/Mimsy

---

### Post by Linux&amp;Lizards on 2006-11-17
well when i stuffed sudo ls -lahR / | grep 281.4    in the terminal this is what i got

mcmahon@mcmahon-desktop:~$ sudo ls -lahR / | grep 281.4
ls: cannot read symbolic link /proc/110/exe: No such file or directory
ls: cannot read symbolic link /proc/110/task/110/exe: No such file or directory
ls: cannot read symbolic link /proc/111/exe: No such file or directory
ls: cannot read symbolic link /proc/111/task/111/exe: No such file or directory
ls: cannot read symbolic link /proc/112/exe: No such file or directory
ls: cannot read symbolic link /proc/112/task/112/exe: No such file or directory
ls: cannot read symbolic link /proc/113/exe: No such file or directory
ls: cannot read symbolic link /proc/113/task/113/exe: No such file or directory
ls: cannot read symbolic link /proc/1824/exe: No such file or directory
ls: cannot read symbolic link /proc/1824/task/1824/exe: No such file or directory
ls: cannot read symbolic link /proc/1831/exe: No such file or directory
ls: cannot read symbolic link /proc/1831/task/1831/exe: No such file or directory
ls: cannot read symbolic link /proc/1839/exe: No such file or directory
ls: cannot read symbolic link /proc/1839/task/1839/exe: No such file or directory
ls: cannot read symbolic link /proc/1908/exe: No such file or directory
ls: cannot read symbolic link /proc/1908/task/1908/exe: No such file or directory
ls: cannot read symbolic link /proc/2/exe: No such file or directory
ls: cannot read symbolic link /proc/2/task/2/exe: No such file or directory
ls: cannot read symbolic link /proc/2903/exe: No such file or directory
ls: cannot read symbolic link /proc/2903/task/2903/exe: No such file or directory
ls: cannot read symbolic link /proc/3/exe: No such file or directory
ls: cannot read symbolic link /proc/3/task/3/exe: No such file or directory
ls: cannot read symbolic link /proc/3077/exe: No such file or directory
ls: cannot read symbolic link /proc/3077/task/3077/exe: No such file or directory
ls: cannot read symbolic link /proc/4/exe: No such file or directory
ls: cannot read symbolic link /proc/4/task/4/exe: No such file or directory
ls: cannot read symbolic link /proc/4624/exe: No such file or directory
ls: cannot read symbolic link /proc/4624/task/4624/exe: No such file or directory
ls: cannot read symbolic link /proc/5/exe: No such file or directory
ls: cannot read symbolic link /proc/5/task/5/exe: No such file or directory
ls: cannot read symbolic link /proc/6/exe: No such file or directory
ls: cannot read symbolic link /proc/6/task/6/exe: No such file or directory
ls: cannot read symbolic link /proc/700/exe: No such file or directory
ls: cannot read symbolic link /proc/700/task/700/exe: No such file or directory
ls: cannot read symbolic link /proc/8/exe: No such file or directory
ls: cannot read symbolic link /proc/8/task/8/exe: No such file or directory
ls: cannot read symbolic link /proc/9/exe: No such file or directory
ls: cannot read symbolic link /proc/9/task/9/exe: No such file or directory
mcmahon@mcmahon-desktop:~$

---

### Post by bodhi.zazen on 2006-11-17
What I am trying to do is to find your "infected" file based on the only information we seem to have - size.

No luck....

to answer you question a pipe takes the output of one command and feeds it to a second command.

You understand ls, no ?
l = long format (included permissions and size)
a = show .hidden or "dot" files.
h = show size in "human" format (Mb, Gb)
R = search subdirectories

| = "pipe"

grep is a "filter"

grep 281.4 = "show only those lines with the number 281.4"

All we found with this fishing expedition was ...
[indent]error messages... :( [/indent]

Try this:
```
sudo ls -lahR / | grep 281
```

Otherwise, upgrade avast or try clam.

PS: I do not know about others, but it makes your post hard to read with all that CLI output stuff :)

Consider piping the output to a file:

```
sudo ls -lahR / | grep 281 > virus_hunt
```

Now...[list=number][*]```
less virus_hunt
```
[*]Post virus_hunt as an attachment
[indent]Look down
See "manage attachments"[/indent][/list]

Just a thought.... :rolleyes:

---

### Post by gn2 on 2006-11-17
Are you booted into Ubuntu and using Avast Linux Version to scan all your drives/partitions including your NTFS Windows drive/partition?

Could be there is a virus in your Windows, and might be an idea to re-boot into Windows and use Windows version anti-virus to remedy the problem.....

Maybe it's best to keep the OS's entirely separate and avoid cross contamination?

---

### Post by Linux&amp;Lizards on 2006-11-18
I know how i got the virus.
I downloaded it with a windows keylogger i was trying to get.

---

### Post by Linux&amp;Lizards on 2006-11-18
-rwxr-xr-x   1 root root  281 2006-02-23 07:32 pppd-dns
-rw-r--r--  1 root root  26K 2006-05-23 08:56 snd-cs4281.ko
-rw-r--r--  1 root root  26K 2006-09-15 19:47 snd-cs4281.ko
-rw-r--r-- 1 root root  281 2006-04-12 06:17 anims20.gif
drwxr-xr-x  4 mcmahon mcmahon 4.0K 2006-09-14 23:31 {cf2812dc-6a7c-4402-b639-4d277dac4c36}
/opt/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}:
/opt/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/chrome:
/opt/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/components:
lrwx------ 1 mcmahon mcmahon 64 2006-11-17 22:56 29 -> socket:[12281]
lrwx------ 1 mcmahon mcmahon 64 2006-11-17 22:56 29 -> socket:[12281]
lrwx------ 1 mcmahon mcmahon 64 2006-11-17 22:56 29 -> socket:[12281]
-rw-r--r--  1 root root  281 2006-05-21 20:39 cpu.h
-rw-r--r--  1 root root  281 2006-05-21 20:39 mca.h
-rw-r--r--  1 root root  281 2006-05-21 20:39 vic.h
-rw-r--r--   1 root root 281K 2006-06-11 22:30 divxa32.acm
-rw-r--r--   1 root root 6.9K 2006-05-21 10:46 IBM281.so
-rw-r--r--  1 root root  281 2005-12-17 01:47 Tunis
-rw-r--r--  1 root root  281 2005-12-17 01:47 Samarkand
-rw-r--r-- 1 root root  281 2006-07-10 13:12 orgquest.gif
-rw-r--r--  1 root root  281 2005-12-15 23:11 ioctl.ph
-rw-r--r-- 1 root root  281 2006-05-30 16:54 getPackageDependencies.pyc
-rw-r--r-- 1 root root  281 2006-05-30 16:54 getPackageDependencies.pyo
virus_hunt

that is the output i got from the virus_hunt

---

### Post by Linux&amp;Lizards on 2006-11-18
clamav shows nothing but its not upgraded because i dont know how to lol.

---

### Post by Malta paul on 2006-11-18
I agree with GN2, had a similar problem a while back. Its best to try another anti-virus checker,why not boot into M$ windows and use a 'Free' virus scanner like AVG and scan your windows system?   good luck:)

---

### Post by kvonb on 2006-11-18
You really need to try getting over this "virus" thing, there is no need to worry about viruses under Ubuntu.

This is a throwback to Windows idealogy, let go, relax, make peace with the world and feel the freedom!

I know it's hard to let go, it took me a few months to get used to the fact that I didn't need to mess about with virus checkers/spyware checkers/ malware blockers/constant updates/firewall nightmares!

You will feel "naked" for a while, this is normal as you go "cold turkey".

Relax, smell the roses.  Welcome to Linux :)

---

### Post by gn2 on 2006-11-18
> **kvonb said:**
> You really need to try getting over this "virus" thing, there is no need to worry about viruses under Ubuntu.



And if you have a Dual-Boot Ubuntu/Windows PC with a shared partition for common file storage?

Download an infected file, unknowingly and unwarned by lack of decent real-time A-V, while booted into Ubuntu then save it to the shared partition, when you re-boot into Windows: 

Hey Presto!!! It's Virus Time!!!

This is why I no longer dual-boot.

---

### Post by Linux&amp;Lizards on 2006-11-18
so you sugest using windows to search out the virus?

---

### Post by Linux&amp;Lizards on 2006-11-18
isnt there an easier way like getting a free tool that will search it out and delete it?
kinda like ad-aware se?
or windows defender?

---

### Post by d3v1ant_0n3 on 2006-11-18
> **Linux&Lizards said:**
> I know how i got the virus.
I downloaded it with a windows keylogger i was trying to get.

You were *trying* to get a keylogger??

---

### Post by d3v1ant_0n3 on 2006-11-18
From your windows boot, try one of these:

[http://www.pandasoftware.com/products/activescan.htm](http://www.pandasoftware.com/products/activescan.htm)

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

For a free windows AV, try [ AVG ](http://free.grisoft.com/doc/1), [Avast!](http://www.avast.com/), or one of these free trials... [ Kapersky (30 day trial)](http://usa.kaspersky.com/downloads/trial-versions.php?aw=downloadspg), [ NOD32](http://www.eset.com/download/index.php).

Its worth having Adaware and another malware scanner too, I like Spybot S&D.

A decent firewall never hurts either.

Most of all, be careful where you surf, and what you download.

---

### Post by Mimsy on 2006-11-18
> **Linux&Lizards said:**
> isnt there an easier way like getting a free tool that will search it out and delete it?
kinda like ad-aware se?
or windows defender?

Those search for and deletespyware and adware. Not viruses; you need an antiv-virus for that.

/Mimsy

---

### Post by Linux&amp;Lizards on 2006-11-18
I know about adaware but i dont want to put windows back on here because our norton doesnt work with me! and we have xp but it belongs to the school!
and the reason i needed a key logger was because i have to have proof that i am actually typing on the computer!
For school reasons my mom asked me to get one because it was either that or a flippin typing program

---

### Post by Linux&amp;Lizards on 2006-11-18
so tell me, If i just use the lve cd and tell it to erase all partitions then wont that get rid of the virus?
I figure before i start downloading stuff again i will ask the guys at my lug  how to deal with removing a virus.
Guess i got in a little over my head this time,

---

### Post by Linux&amp;Lizards on 2006-11-18
SO! if i use the live cd to erase all my partitions then should that get rid of the virus?

---

### Post by bodhi.zazen on 2006-11-18
> **Linux&Lizards said:**
> SO! if i use the live cd to erase all my partitions then should that get rid of the virus?

I think you are over-reacting (sorry). IMO it looks like a false +

I presume one of those files in virus_hunt is being identified as your virus.

Do you recognize any of them as newly downloaded?
New swiftfox extensions?

-rw-r--r-- 1 root root 281 2006-04-12 06:17 anims20.gif
-rw-r--r-- 1 root root 281 2006-07-10 13:12 orgquest.gif

Otherwise, search these files one at a time at the avast site I gave you earlier.

alternately copy each of these to a directory in /home/user_name/viruses and scan the directory /home.=use_name/viruses
If + delete them from /home/user_name/viruses one at at time untill you identify the offending file.

You can then elect to delete the file, but be careful. I would like to see the virus identified, an online scan will hopefully help...

---

### Post by gn2 on 2006-11-18
> **Linux&Lizards said:**
> so you sugest using windows to search out the virus?

Yes, but if the virus is in an ext2or3 partition make sure you have a utility installed for writing to ext2or3 file systems so that if the virus is in your Ubuntu partition it can be deleted.

In any case I think it's most likely that what you have found is one of the "test" viruses in a Linux A-V package, and is a false +ve.

Sadly the A-V protection offered in Linux to the Windows part of a Dual-Boot system is sadly lacking, nothing I've tried so far seems adequate.

---

### Post by Linux&amp;Lizards on 2006-11-18
whats a good online scan i can use?

---

### Post by gn2 on 2006-11-18
> **Linux&Lizards said:**
> whats a good online scan i can use?

Trend Micro housecall is one I have used succesfully in Windows, don't know about Linux tho.....

---

### Post by Linux&amp;Lizards on 2006-11-18
same here.
I'm running it as we speak.

---

### Post by Linux&amp;Lizards on 2006-11-18
so then completely erasing all my partitions and putting suse on my desktop wont get rid of the virus?
and for those of you who think i am over reacting im really not.
its just i was thinking about going back to suse until next friday when my lug meets.

---

### Post by Linux&amp;Lizards on 2006-11-18
HEY! NOW AVAST SHOWS NO INFECTED FILES!!!!!!!
whooohoo! must have been a false positive.

---

