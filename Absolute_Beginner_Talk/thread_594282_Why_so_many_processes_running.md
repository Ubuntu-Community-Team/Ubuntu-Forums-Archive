---
title: "Why so many processes running?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Boondock5 on 2007-10-27
Apparently when I had the little "too many open files"  problem, all I did was make it so the problem could kind of run it's course. Because now I have over 100 processes running in the back ground, slowing up everything.

How do I shut down this problem so I can have my old quick computer back? this is why I left windows, to get away from all the running processes...

boondock5@boondock5:~$ ps -x
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
  PID TTY      STAT   TIME COMMAND
 4921 ?        SL     0:00 /usr/bin/gnome-keyring-daemon -d
 4924 ?        Ssl    0:00 x-session-manager
 4961 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 4963 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 6
 4967 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19
 4969 ?        Sl     0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
 4975 ?        S      0:00 /usr/bin/metacity --sm-client-id=default0
 4977 ?        S      0:02 gnome-panel --sm-client-id default1
 4979 ?        S      0:01 nautilus --no-default-window --sm-client-id default2
 4994 ?        Ss     0:00 gnome-screensaver
 5380 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5381 ?        S      0:00 vino-session --sm-client-id default5
 5382 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5383 ?        S      0:00 bluetooth-applet
 5385 ?        S      0:00 update-notifier
 5390 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5395 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-alarm-notify
 5400 ?        SNl    0:01 trackerd
 5403 ?        S      0:00 nm-applet --sm-disable
 5405 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 5406 ?        S      0:00 gnome-cups-icon --sm-client-id default3
 5421 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5424 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5437 ?        Ss     0:00 gnome-power-manager
 5449 ?        S      0:00 /usr/lib/gnome-applets/battstat-applet-2 --oaf-activa
 5451 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-exchange-storage --
 5466 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-a
 5487 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5551 ?        S      0:00 /bin/sh /usr/bin/firefox
 5563 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/fire
 5567 ?        Sl     0:34 /usr/lib/firefox/firefox-bin
 5742 ?        Rl     0:00 gnome-terminal
 5748 ?        S      0:00 gnome-pty-helper
 5749 pts/1    Ss     0:00 bash
 5788 pts/1    R+     0:00 ps -x



wth happened?

---

### Post by llamakc on 2007-10-27
That's not 100 processes.

---

### Post by Boondock5 on 2007-10-27
well duh!

thats just what showed up now, when i looked at the system analyzer a bit ago it showed 107 processes running

---

### Post by w7kmc on 2007-10-27
In a fresh Ubuntu install you usually start out with around 95 to 100 processes...your ps llis tlooks perfectly normal to me.

You can go to System--->Administration--->Services and trim out the services you feel you do not need.

For me, I dropped:
Bluetooth,TrackerD,,automated Crash reporting.

You can also trim getty processes by four by using these commands:

sudo rm /etc/event.d/tty3
sudo rm /etc/event.d/tty4
sudo rm /etc/event.d/tty4

These are for <cntrl><alt>(function-Key) terminals.  Ubuntu gives you 6 in case X crashes or if you want to do something in the background.  I found that you only need two though.

---

### Post by llamakc on 2007-10-27
Okay. I have 133 processes running in total. What's your point? Before your other issues these processes were already running.

What sort of system are you on? Low memory? What's the size of your swap?

Didn't you leave Windows because of how sluggish it was? Don't equate running or listening processes in Linux with processes in Windows. It's a different animal.

So you've rebooted or logged out/in after the other issue?

---

### Post by Boondock5 on 2007-10-27
> **w7kmc said:**
> In a fresh Ubuntu install you usually start out with around 95 to 100 processes...your ps llis tlooks perfectly normal to me.

You can go to System--->Administration--->Services and trim out the services you feel you do not need.

For me, I dropped:
Bluetooth,TrackerD,,automated Crash reporting.

You can also trim getty processes by four by using these commands:

sudo rm /etc/event.d/tty3
sudo rm /etc/event.d/tty4
sudo rm /etc/event.d/tty4

These are for <cntrl><alt>(function-Key) terminals.  Ubuntu gives you 6 in case X crashes or if you want to do something in the background.  I found that you only need two though.


well if thats not the problem then whats happening here?  This laptop was lightning fast until I threw the "too many open files" fit.

---

### Post by llamakc on 2007-10-27
So you've looked at the logs?

---

### Post by Boondock5 on 2007-10-27
Probably not, how do I get there?

---

### Post by Boondock5 on 2007-10-27
bump

---

### Post by w7kmc on 2007-10-27
It could be caused by some application you are trying to run.

What kind of output does the ' sudo lsof' command give.  This commands provides a list of open files.

You will get a HUGE listing so...

sudo  lsof | less 

would be better a better command  and you can scroll through to perhaps track down what is causing the open files to occur.  Also llamakc is right...systems will run happily with 100 or more processes....and there  is no correlation that can be made with Windows process count and Linux process count...

---

### Post by Boondock5 on 2007-10-27
COMMAND    PID       USER   FD      TYPE     DEVICE    SIZE    NODE NAME
init         1       root  cwd   unknown                            /proc/1/cwd (readlink: Permission denied)
init         1       root  rtd   unknown                            /proc/1/root (readlink: Permission denied)
init         1       root  txt   unknown                            /proc/1/exe (readlink: Permission denied)
init         1       root NOFD                                      /proc/1/fd (opendir: Permission denied)
kthreadd     2       root  cwd   unknown                            /proc/2/cwd (readlink: Permission denied)
kthreadd     2       root  rtd   unknown                            /proc/2/root (readlink: Permission denied)
kthreadd     2       root  txt   unknown                            /proc/2/exe (readlink: Permission denied)
kthreadd     2       root NOFD                                      /proc/2/fd (opendir: Permission denied)
migration    3       root  cwd   unknown                            /proc/3/cwd (readlink: Permission denied)
migration    3       root  rtd   unknown                            /proc/3/root (readlink: Permission denied)
migration    3       root  txt   unknown                            /proc/3/exe (readlink: Permission denied)
:
this is what came up, did I do it wrong?

---

### Post by Boondock5 on 2007-10-27
bumpers

---

### Post by w7kmc on 2007-10-27
It is right....

If you do:

sudo lsof |  less

Then that will get rid of the "perm denied" error....sorry

Anyway...the running process is listed first....the the file is listed that it is accessing.  If you are interested in seeing which processes are accessing which files...then scroll on down....if there is something gobbling up files then that application  is your culprit;

Processes can have a lot of files open...like gnome-vfs, x-session, etc can have a 100 or more files open.  This is normal.  If you are still getting that error...then there is likely some application...a bittorent or filesharing program  perhaps? that is causing the problem.

---

