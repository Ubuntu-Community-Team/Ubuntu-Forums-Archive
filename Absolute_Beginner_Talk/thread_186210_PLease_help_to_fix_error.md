---
title: "PLease help to fix error"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-06-01
**E: irmp3: subprocess post-installation script returned error exit status 1**
E: irmp3: subprocess post-installation script returned error exit status 1

no matter what i try to install i get this error..please help

---

### Post by %hMa@?b&lt;C on 2006-06-01
sudo apt-get remove irmp3
what happens after running that

---

### Post by JRaz on 2007-02-19
I get the same error message and here's my output from the command you specified.

```
raz@razbuntu:~$ sudo apt-get remove irmp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required
  irmp3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  irmp3
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 410kB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 38586 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Starting irmp3: irmp3.
Errors were encountered while processing:
 irmp3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by JRaz on 2007-03-19
shameless bump, is there anyone who could help?

---

### Post by scxtt on 2007-03-19
did you try **apt-get autoremove**?

and were there problems installing that package to begin with?

---

### Post by JRaz on 2007-03-19
I dont recall any problems installing it but heres the output from autoremove

```
raz@razbuntu:~$ sudo apt-get autoremove irmp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  irmp3
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 410kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 37716 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 irmp3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by scxtt on 2007-03-19
looks to me that the uninstall script is very messed up ... i've seen similar problems when i was using, then UNusing proftpd ... to get it back in working order i found all references to it and removed them ... i'd try:

sudo slocate -u
slocate irmp3

and post what returns (or just delete it if you feel comfortable w/ that) ...

---

### Post by JRaz on 2007-03-20
heres the output, anything to worry about or shall i go ahead and remove those files? also will this remove the entry under apt-get/synaptic etc

```
raz@razbuntu:~$ sudo slocate -u
raz@razbuntu:~$ slocate irmp3
/var/lib/dpkg/info/irmp3.list
/var/lib/dpkg/info/irmp3.postinst
/var/lib/dpkg/info/irmp3.prerm
/var/lib/dpkg/info/irmp3.postrm
/var/lib/dpkg/info/irmp3.conffiles
/var/lib/dpkg/info/irmp3.md5sums
/var/log/irmp3
/etc/init.d/irmp3
/etc/irmp3d.conf
/etc/rc0.d/k20irmp3
/etc/rc1.d/K20irmp3
/etc/rc2.d/K20irmp3
/etc/rc3.d/K20irmp3
/etc/rc4.d/K20irmp3
/etc/rc5.d/K20irmp3
/etc/rc6.d/K20irmp3
/usr/bin/irmp3
/usr/sbin/irmp3d
/usr/sbin/irmp3conf
/usr/share/irmp3
/usr/share/irmp3/beep
/usr/share/irmp3/beep/lircrc.advanced
/usr/share/irmp3/beep/on.au
/usr/share/irmp3/beep/off.au
/usr/share/irmp3/beep/lircrc.browser
/usr/share/irmp3/beep/lircrc.simple
/usr/share/irmp3/scripts
/usr/share/irmp3/scripts/README
/usr/share/irmp3/scripts/FTP
/usr/share/irmp3/scripts/FTP/enable.sh
/usr/share/irmp3/scripts/FTP/disable.sh
/usr/share/irmp3/scripts/command.sh
/usr/share/irmp3/scripts/date.sh
/usr/share/irmp3/scripts/grab.sh
/usr/share/irmp3/scripts/load.sh
/usr/share/irmp3/scripts/mount.sh
/usr/share/irmp3/scripts/shutdown.sh
/usr/share/doc/irmp3
/usr/share/doc/irmp3/changelog.Debian.gz
/usr/share/doc/irmp3/changelog.gz
/usr/share/doc/irmp3/AUTHORS
/usr/share/doc/irmp3/README
/usr/share/doc/irmp3/copyright
/usr/share/man/man1/irmp3conf.1.gz
/usr/share/man/man1/irmp3.1.gz
/usr/share/man/man5/irmp3d.conf.5.gz
/usr/share/man/man7/irmp3d.7.gz
/usr/share/man/man8/irmp3d.8.gz

```

---

### Post by JRaz on 2007-03-20
I went ahead and removed the files, then opened up synaptic and removed irmp3, removal went with out a hitch. Im now irmp3 free yay :P

---

