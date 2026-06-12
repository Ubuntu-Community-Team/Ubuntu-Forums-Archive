---
title: "Redirecting command output to a file."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-23
Hi Everybody

How do I get redirect the output of command to file. The intent being to eventually save the file on a floppy and be able to attach in my posting for the forum should there be a need in the future.

Best regards


Deepak Agarwal

---

### Post by raggamuffin on 2006-02-23
[command] > [output file]

for example...typing "ls > contents.txt" will give you a file called contents.txt that contains the output of "ls"...

---

### Post by agarwaldvk on 2006-02-23
Dear Raggamuffin

Thanks a lot - that was easy! I can do that!


Best regards


Deepak Agarwal

---

### Post by makan on 2006-02-24
also you can tee command:


Using the tee command to save stdout to tee.txt. stdout is still displayed on the screen:
# ps -ax | tee tee.txt


Using the tee command to append stdout to tee.txt. stdout is still displayed on the screen:
# ps -ax | tee -a tee.txt

\\:D/

---

### Post by dvarsam on 2006-02-24
Dear "makan",

Can you briefly explain what "ps -ax | tee tee.txt" does?

Cause I did:

ps -ax | tee /home/dimitris/Desktop/tee.txt

And I got:

  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:00 init [2]         
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S<     0:00 [events/0]
    4 ?        S<     0:00 [khelper]
    5 ?        S<     0:00 [kthread]
    7 ?        S<     0:00 [kacpid]
  101 ?        S<     0:00 [kblockd/0]
  129 ?        S      0:00 [pdflush]
  130 ?        S      0:00 [pdflush]
  132 ?        S<     0:00 [aio/0]
  131 ?        S      0:00 [kswapd0]
  717 ?        S      0:00 [kseriod]
  951 ?        S<     0:00 [ata/0]
  954 ?        S      0:00 [scsi_eh_0]
  955 ?        S      0:00 [scsi_eh_1]
 2044 ?        S      0:00 [khubd]
 2149 ?        S      0:00 [scsi_eh_2]
 2150 ?        S      0:00 [usb-storage]
 3985 ?        S      0:00 [kjournald]
 4139 ?        S<s    0:00 udevd --daemon
 6077 ?        S      0:00 [khpsbpkt]
 6722 ?        S      0:00 [shpchpd_event]
 7399 ?        S      0:00 [knodemgrd_0]
 8416 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
 8751 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 8783 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 8785 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 8798 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 8811 ?        Ss     0:00 /usr/sbin/hald
 8816 ?        S      0:00 hald-addon-acpi
 8827 ?        S      0:00 hald-addon-storage
 8829 ?        S      0:00 hald-addon-storage
 8831 ?        S      0:00 hald-addon-storage
 8833 ?        S      0:00 hald-addon-storage
 8837 ?        S      0:00 hald-addon-storage
 9233 ?        Ss     0:00 /usr/sbin/gdm
 9238 ?        S      0:00 /usr/sbin/gdm
 9289 ?        S      2:54 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 9339 ?        Ssl    0:00 /usr/sbin/hpiod
 9363 ?        S      0:00 python /usr/sbin/hpssd
 9555 ?        Ss     0:00 hcid: processing events
 9561 ?        Ss     0:00 /usr/sbin/sdpd
 9571 ?        S<     0:00 [krfcommd]
 9603 ?        Ss     0:00 /usr/sbin/atd
 9616 ?        Ss     0:00 /usr/sbin/cron
 9652 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 9653 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 9654 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 9655 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 9656 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 9657 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 9679 ?        Ss     0:00 x-session-manager
 9717 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 9720 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 9721 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 9723 ?        S      0:00 /usr/lib/gconf2/gconfd-2 5
 9726 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 9728 ?        S      0:00 /usr/bin/esd -nobeeps
 9732 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=18
 9734 ?        S      0:03 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
 9737 ?        S      0:00 /usr/lib/gamin/gam_server
 9749 ?        S      0:01 xscreensaver -nosplash
 9773 ?        Ss     0:15 /usr/bin/metacity --sm-client-id=default0
 9778 ?        Ssl    0:02 gnome-panel --sm-client-id default1
 9780 ?        Ssl    0:16 nautilus --no-default-window --sm-client-id default2
 9782 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 9788 ?        Ss     0:01 update-notifier --sm-client-id default7
 9790 ?        Ssl    0:00 gnome-cups-icon --sm-client-id default3
 9792 ?        S      0:01 /usr/lib/notification-daemon/notification-daemon
 9794 ?        S      0:10 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=29
 9797 ?        Sl     0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=32
 9806 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=31
 9808 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 9816 ?        S      0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=39
 9818 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=40
 9820 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=42
 9838 ?        Sl     3:19 /usr/lib/mozilla-firefox/firefox-bin -a firefox
10004 ?        SNs    0:00 /usr/sbin/cupsd -F
10173 ?        SNs    0:00 /sbin/syslogd -u syslog
12169 ?        S      0:00 /bin/sh /usr/lib/openoffice2/program/soffice -writer file:///fat32_files/Linux%20-%20All%20Files/Ubuntu%20Favorites%20Backup/Put%20this%20in%20-%20etc-mozillafirefox-profile/Ubuntu%20-%20How%20to%20Backup%20your%20Mozilla%20Firefox's%20Bookmarks.odt
12180 ?        Sl     0:25 /usr/lib/openoffice2/program/soffice.bin -writer file:///fat32_files/Linux%20-%20All%20Files/Ubuntu%20Favorites%20Backup/Put%20this%20in%20-%20etc-mozillafirefox-profile/Ubuntu%20-%20How%20to%20Backup%20your%20Mozilla%20Firefox's%20Bookmarks.odt
12385 ?        Rl     0:00 gnome-terminal --working-directory=
12386 ?        S      0:00 gnome-pty-helper
12387 pts/0    Ss     0:00 bash
12398 pts/0    R      0:00 -bash
12633 pts/0    R+     0:00 ps -ax


What on Earth is this?

---

### Post by MighMoS on 2006-02-24
He was using ps as an example.  ps is a process listing of everything that's running on your system.  The trick he was showing was that "foo |tee bar" will execute the program foo, and not only display the output on the screan, but also write it to the file bar.

On the original solution, > redirects to a file, overwriting to it.  >> redirects output to a file, appending to it.

---

### Post by force4 on 2007-09-23
Hi All...

I'm trying to debug a Wine problem with an app that is displaying bogus fonts.

I think the app needs a font that usually comes with windoz but isn't available in Wine...but I don't know which one...

so I thought I would WINEDEBUG=font to see what what was happening and of course there was so much output I lost the important part at the beginning.

I tried 2 ways to redirect the std out to a text file but the file always comes up empty [it is created].

$ WINEDEBUG=font > fontLog.txt wine viewer.exe (outputs what I want in the console but just gives me an empty file)

and 

$ WINEDEBUG=font | tee  fontLog.txt wine viewer.exe

does absolutely nothing.

and

 $ WINEDEBUG=font wine viewer.exe | tee fontLog.txt

returns this error:

wine: could not load L"C:\\CMap\\viewer\\viewer.exe": Bad EXE format for [email]steve@steve-laptop:~/.wine[/email]/drive_c/CMap/viewer$ 

What is the correct way to make this work?

---

### Post by asmoore82 on 2007-09-23
The problem here is very subtle.
UNIX standards give 3 standard input/output "objects" to every process by default.
They are **standard input**, **standard output**, and **standard error output**; they are often
seen abbreviated as **stdin**, **stdout** and **stderr**, respectively.

the '<' I/O redirector causes a file to become **stdin**.
the '>' I/O redirector causes a file to become **stdout**.
so, error messages will not be captured by '>'
[[it is also good programming practise to always send prompts
that require user interaction to stderr and not stdout]]

the redirector that will send stdout and stderr to a file is '&>'
if you only want stderr to go the file, you would use '2>'
and finally, if you want to use tee, you need to redirect the first
command's stderr to stdout with this cryptic token: '2>&1'
::examples follow::

```

*catch-all output, std and err*
ls -Rl &> listing.txt

*save errors in a separate file*
ls -Rl > listing.txt 2> errlog.txt

*catch-all and see it too with tee*
ls -Rl 2>&1 | tee listing.txt

```

in your case above, you probably want something like
```
~$ WINEDEBUG=font wine viewer.exe &> winelog.txt
```

---

