---
title: "Removing BOINC - Can't"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-16
Can't remove BOINC Client  using Synaptics package manager, I also can't copy all the error messages from the error box that comes up(?), although it has things like:

BOINC Client /usr/bin/boinc_client does not exist or is not executable
Trying to recover

along with a lot of other messages.

How do I get Synaptics to "fix" itself and get rid of BOINC? I tried re-installing and uninstalling BOINC and I get nowhere.

---

### Post by mikex on 2007-08-16
I tried this:
[B]
mike@mike-desktop:~$ sudo apt-get remove boinc-app-seti

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

Any suggestions on what the problem is?

---

### Post by stevebakerj on 2007-08-16
> **mikex said:**
> I tried this:
[B]
mike@mike-desktop:~$ sudo apt-get remove boinc-app-seti

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

Any suggestions on what the problem is?

Is Boinc still running while you are trying to uninstall it?

Goto your terminal and type

```
ps aux
```  does Boinc show up, if it does make a note of its PID number and then type

```
kill 'PID number'
```

Then uninstall it with Synaptic or the terminal

---

### Post by mikex on 2007-08-16
This is a headache -
BOINC is not running.

I did what you asked, and then tried to re-install boinc from Synaptics and got -

E: boinc-client: subprocess post-installation script returned error exit status 5
E: boinc-app-seti: dependency problems - leaving unconfigured

Then I also tried a compete removal -

E: boinc-client: subprocess post-installation script returned error exit status 5

I am completely lost on this process...

---

### Post by stevebakerj on 2007-08-16
can you post the output of

```
ps aux
```

here?

---

### Post by mikex on 2007-08-16
Thanks for your help!

Here it is, I've had issues ever since I used Synaptics to try and get BOINC going.

mike@mike-desktop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2912  1844 ?        Ss   05:39   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    05:39   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   05:39   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    05:39   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   05:39   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   05:39   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   05:39   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   05:39   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   05:39   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   05:39   0:00 [kacpi_notify]
root       119  0.0  0.0      0     0 ?        S<   05:39   0:00 [kseriod]
root       140  0.0  0.0      0     0 ?        S    05:39   0:00 [pdflush]
root       141  0.0  0.0      0     0 ?        S    05:39   0:00 [pdflush]
root       142  0.0  0.0      0     0 ?        S<   05:39   0:00 [kswapd0]
root       143  0.0  0.0      0     0 ?        S<   05:39   0:00 [aio/0]
root      1946  0.0  0.0      0     0 ?        S<   05:39   0:00 [ata/0]
root      1947  0.0  0.0      0     0 ?        S<   05:39   0:00 [ata_aux]
root      1949  0.0  0.0      0     0 ?        S<   05:39   0:00 [scsi_eh_0]
root      1950  0.0  0.0      0     0 ?        S<   05:39   0:00 [scsi_eh_1]
root      1955  0.0  0.0      0     0 ?        S<   05:39   0:00 [ksuspend_usbd]
root      1956  0.0  0.0      0     0 ?        S<   05:39   0:00 [khubd]
root      2007  0.0  0.0      0     0 ?        S<   05:39   0:00 [khpsbpkt]
root      2185  0.0  0.0      0     0 ?        S<   05:39   0:00 [knodemgrd_0]
root      2319  0.0  0.0      0     0 ?        S<   05:39   0:00 [scsi_eh_2]
root      2320  0.0  0.0      0     0 ?        S<   05:39   0:00 [usb-storage]
root      2322  0.0  0.0      0     0 ?        S<   05:39   0:00 [scsi_eh_3]
root      2323  0.0  0.0      0     0 ?        S<   05:39   0:00 [usb-storage]
root      2480  0.0  0.0      0     0 ?        S<   05:39   0:00 [kjournald]
root      2678  0.0  0.1   2872  1216 ?        S<s  05:39   0:00 /sbin/udevd --daemon
root      3709  0.0  0.0      0     0 ?        S<   05:39   0:00 [kgameportd]
root      3713  0.0  0.0      0     0 ?        S<   05:39   0:00 [kpsmoused]
root      4458  0.0  0.0   1652   512 tty4     Ss+  05:39   0:00 /sbin/getty 38400 tty4
root      4459  0.0  0.0   1648   508 tty5     Ss+  05:39   0:00 /sbin/getty 38400 tty5
root      4464  0.0  0.0   1652   512 tty2     Ss+  05:39   0:00 /sbin/getty 38400 tty2
root      4465  0.0  0.0   1648   508 tty3     Ss+  05:39   0:00 /sbin/getty 38400 tty3
root      4466  0.0  0.0   1652   512 tty1     Ss+  05:39   0:00 /sbin/getty 38400 tty1
root      4467  0.0  0.0   1652   512 tty6     Ss+  05:39   0:00 /sbin/getty 38400 tty6
root      4709  0.0  0.1   2256  1172 ?        Ss   05:39   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/r
root      4817  0.0  0.0   1828   772 ?        Ss   05:39   0:00 /sbin/syslogd
root      4870  0.0  0.0   1796   524 ?        Ss   05:39   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/
klog      4872  0.0  0.1   2428  1372 ?        Ss   05:39   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4893  0.0  0.1   2844  1068 ?        Ss   05:39   0:00 /usr/bin/dbus-daemon --system
107       4909  0.0  0.8  10752  9084 ?        Ss   05:39   0:03 /usr/sbin/hald
root      4910  0.0  0.1   2876  1036 ?        S    05:39   0:00 hald-runner
107       4916  0.0  0.0   2104   888 ?        S    05:39   0:00 hald-addon-acpi: listening on acpid socket /v
root      4918  0.0  0.1   3056  1132 ?        S    05:39   0:05 hald-addon-usb-csr: listening on 'Mouse Recei
107       4929  0.0  0.0   2104   904 ?        S    05:39   0:00 hald-addon-keyboard: listening on /dev/input/
107       4934  0.0  0.0   2100   896 ?        S    05:39   0:00 hald-addon-keyboard: listening on /dev/input/
107       4937  0.0  0.0   2104   900 ?        S    05:39   0:00 hald-addon-keyboard: listening on /dev/input/
107       4940  0.0  0.0   2100   896 ?        S    05:39   0:00 hald-addon-keyboard: listening on /dev/input/
107       4952  0.0  0.0   2100   908 ?        S    05:39   0:00 hald-addon-storage: polling /dev/hdc
107       4956  0.0  0.0   2104   908 ?        S    05:39   0:00 hald-addon-storage: polling /dev/sdb
root      4969  0.0  0.0   1944   704 ?        Ss   05:39   0:00 /usr/sbin/dhcdbd --system
root      4984  0.0  0.1   4132  1844 ?        Ss   05:39   0:00 /usr/sbin/NetworkManager --pid-file /var/run/
avahi     5002  0.0  0.1   2668  1368 ?        Ss   05:39   0:00 avahi-daemon: running [mike-desktop.local]
avahi     5003  0.0  0.0   2668   460 ?        Ss   05:39   0:00 avahi-daemon: chroot helper
root      5016  0.0  0.1   3032  1148 ?        Ss   05:39   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file
root      5029  0.0  0.0   2872   804 ?        Ss   05:39   0:00 /usr/bin/system-tools-backends
root      5030  0.0  0.1   2716  1216 ?        S    05:39   0:00 dbus-daemon --session --print-address --nofor
root      5062  0.0  0.1  12220  1408 ?        Ss   05:39   0:00 /usr/sbin/gdm
root      5063  0.0  0.2  12588  2380 ?        S    05:39   0:00 /usr/sbin/gdm
root      5068  6.4  3.0  37004 31260 tty7     SLs+ 05:39  45:25 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/l
root      5137  0.0  0.0   6416   836 ?        Ss   05:39   0:00 /usr/sbin/hpiod
hplip     5140  0.0  0.4   9980  4892 ?        S    05:39   0:00 python /usr/sbin/hpssd
root      5250  0.0  0.1   2696  1056 ?        Ss   05:39   0:00 /usr/sbin/hcid -x -s
root      5263  0.0  0.0      0     0 ?        S<   05:39   0:00 [krfcommd]
daemon    5298  0.0  0.0   1912   424 ?        Ss   05:39   0:00 /usr/sbin/atd
root      5312  0.0  0.0   2284   900 ?        Ss   05:39   0:00 /usr/sbin/cron
mike      5409  0.0  1.0  30132 11028 ?        Ssl  05:39   0:00 x-session-manager
mike      5447  0.0  0.0   4252   528 ?        Ss   05:39   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exi
mike      5450  0.0  0.0   2660   640 ?        S    05:39   0:00 /usr/bin/dbus-launch --exit-with-session x-se
mike      5451  0.0  0.1   2852  1052 ?        Ss   05:39   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --p
mike      5453  0.0  0.4   6704  4204 ?        S    05:39   0:00 /usr/lib/libgconf2-4/gconfd-2 6
mike      5456  0.0  0.0   2760  1000 ?        S    05:39   0:00 /usr/bin/gnome-keyring-daemon
mike      5458  0.0  0.9  29336  9748 ?        Sl   05:39   0:01 /usr/lib/control-center/gnome-settings-daemon
mike      5470  0.0  0.0   1716   484 ?        Ss   05:39   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -
mike      5471  0.0  0.2   4692  2996 ?        S    05:39   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawn
mike      5475  0.0  0.0   1712   492 ?        S    05:39   0:00 /bin/sh /usr/bin/compiz --sm-client-id defaul
mike      5478  0.0  1.6  38368 16684 ?        S    05:39   0:06 gnome-panel --sm-client-id default1
mike      5481  0.0  1.6  58232 17576 ?        S    05:39   0:01 nautilus --no-default-window --sm-client-id d
mike      5484  0.0  0.9  17228  9708 ?        S    05:39   0:04 gtk-window-decorator
mike      5488  0.4  1.5  24024 15756 ?        SL   05:39   3:06 /usr/bin/compiz.real --no-fbo --ignore-deskto
mike      5490  0.0  0.3  39648  3112 ?        Ssl  05:39   0:00 /usr/lib/bonobo-activation/bonobo-activation-
mike      5493  0.0  0.3   8456  3416 ?        S    05:39   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
mike      5494  0.0  0.4  18908  4840 ?        Ss   05:39   0:00 gnome-volume-manager --sm-client-id default4
mike      5499  0.0  1.1  31012 11832 ?        S    05:39   0:00 update-notifier
mike      5505  0.0  0.9  67976 10024 ?        Sl   05:39   0:00 /usr/lib/evolution/2.10/evolution-alarm-notif
mike      5519  0.0  0.9  28552  9580 ?        S    05:39   0:01 nm-applet --sm-disable
mike      5520  0.0  0.7  40120  8196 ?        S    05:39   0:04 gnome-cups-icon --sm-client-id default3
mike      5521  0.0  0.6  29752  6968 ?        Ss   05:39   0:00 gnome-power-manager
mike      5537  0.0  0.8  61236  8668 ?        S    05:39   0:00 /usr/lib/gnome-applets/trashapplet --oaf-acti
mike      5539  0.0  0.9  36508  9464 ?        Sl   05:39   0:00 /usr/lib/evolution/2.10/evolution-exchange-st
mike      5551  0.0  0.0   2460   884 ?        S    05:39   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
mike      5556  0.0  0.6  65604  6476 ?        Sl   05:39   0:00 /usr/lib/evolution/evolution-data-server-1.10
mike      5560  0.0  1.1  31880 12000 ?        S    05:39   0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-ac
mike      5606  0.0  0.5  16384  5264 ?        Ss   05:40   0:04 gnome-screensaver
cupsys    5954  0.0  0.2   4988  2216 ?        SNs  05:44   0:03 /usr/sbin/cupsd
mike     22000  0.0  1.5  54720 16444 ?        Sl   16:25   0:02 gnome-terminal
mike     22002  0.0  0.0   2464   732 ?        S    16:25   0:00 gnome-pty-helper
mike     22003  0.0  0.3   5640  3176 pts/0    Ss   16:25   0:00 bash
mike     23415  1.8  4.5 148028 47628 ?        Sl   17:14   0:15 /usr/lib/firefox/firefox-bin
mike     23791  0.0  0.0   2564   992 pts/0    R+   17:28   0:00 ps aux

---

### Post by stevebakerj on 2007-08-16
Have you tried removing the BOINC client & manager?

```
sudo apt-get remove boinc-client
```

and BOINC manager

```
sudo apt-get remove boinc-manager
```

---

### Post by mikex on 2007-08-16
> **stevebakerj said:**
> Have you tried removing the BOINC client & manager?

```
sudo apt-get remove boinc-client
```

Results:

mike@mike-desktop:~$ sudo apt-get remove boinc-client
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fftw3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  boinc-client
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 881kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111903 files and directories currently installed.)
Removing boinc-client ...
 * BOINC client '/usr/bin/boinc_client' does not exist or is not  executable.
invoke-rc.d: initscript boinc-client, action "stop" failed.
dpkg: error processing boinc-client (--remove):
 subprocess pre-removal script returned error exit status 5
 * BOINC client '/usr/bin/boinc_client' does not exist or is not  executable.
invoke-rc.d: initscript boinc-client, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 boinc-client
E: Sub-process /usr/bin/dpkg returned an error code (1)


and BOINC manager

```
sudo apt-get remove boinc-manager
```

Results:

mike@mike-desktop:~$ sudo apt-get remove boinc-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package boinc-manager is not installed, so not removed
The following packages were automatically installed and are no longer required:
  fftw3 boinc-client
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up boinc-client (5.4.11-5) ...
 * BOINC client '/usr/bin/boinc_client' does not exist or is not  executable.
invoke-rc.d: initscript boinc-client, action "start" failed.
dpkg: error processing boinc-client (--configure):
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 boinc-client
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

