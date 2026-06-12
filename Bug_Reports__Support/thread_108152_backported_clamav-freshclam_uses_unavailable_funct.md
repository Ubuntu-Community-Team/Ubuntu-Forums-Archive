---
title: "backported clamav-freshclam uses unavailable functions"
date: 2005-12-25
forum: Bug Reports / Support
---

### Post by at2000 on 2005-12-25
Version 0.87.1-1~breezy1 of /etc/init.d/clamav-frashclam uses the function "log_daemon_msg", which is not in /lib/lsb/init-functions in breezy.

As a result of this, I got this mail from cron.daily script:
/etc/cron.daily/logrotate:
/etc/init.d/clamav-freshclam: line 195: log_daemon_msg: command not found

---

### Post by Watcher on 2006-01-08
Yes. I got the same error, but I seen somewhere that removing clamav en clamscan and then re&#239;nstalling clamscan should do the trick ...

I can't try it myself at the moment (no internet connection to my ubuntu box atm), but I'm giving that a try in a week or 2. I'll let you know if that does the trick.

---

### Post by at2000 on 2006-01-08
Tried and it still complains about log_daemon_msg.

---

### Post by dcstar on 2006-01-08
[QUOTE=at2000]Tried and it still complains about log_daemon_msg.[/QUOTE]
I downloaded the new /lib/lsb/init-functions and did cut-and-paste of that function into my existing file!

Here is what I attached to the end of my file (seems to work ok for me):

# Sample usage:
# log_daemon_msg "Starting GNOME Login Manager" "gdm"
#
# On Debian, would output "Starting GNOME Login Manager: gdm"
# On Ubuntu, would output " * Starting GNOME Login Manager..."
#
# If the second argument is omitted, logging suitable for use with
# log_progress_msg() is used:
#
# log_daemon_msg "Starting remote filesystem services"
#
# On Debian, would output "Starting remote filesystem services:"
# On Ubuntu, would output " * Starting remote filesystem services..."

log_daemon_msg () {
    if [ -z "$1" ]; then
        return 1
    fi

    if [ -z "$2" ]; then
        echo -n "$1:"
        return
    fi
    
    echo -n "$1: $2"
}

---

### Post by at2000 on 2006-01-09
I won't challenge this workaround. However, the package still needs to be fixed. The fix is as simple as replcing all log_daemon_msg with something else, or removing them.

---

### Post by dcstar on 2006-01-09
[QUOTE=at2000]I won't challenge this workaround. However, the package still needs to be fixed. The fix is as simple as replacing all log_daemon_msg with something else, or removing them.[/QUOTE]
No, the ClamAV package is using the currently recommended functions in this lsb module, such as log_daemon_msg.

The problem is that the lsb package currently used in Breezy has not been updated to the current version - where ClamAV now needs it to be.

The ClamAV people have followed the instructions (as they should) to use the current version of lsb, Ubuntu haven't (yet).

---

### Post by Bachstudies on 2006-01-12
Where can I download the new /lib/lsb/init-functions? 

I'm having the same problems with the log_daemon_msg. I tried uninstalling clamAV and I was pleasantly surprised when freshclam informed me that clamd had been informed. However, on shutting down ubuntu, the log_daemon_msg message was present again.

---

### Post by erdesc on 2006-02-15
Hello,

Well, I went through this problem :

**1st** get the dapper source of clamav (in /usr/local/src for me), build-deps and build-essential

**2nd** get the debian package to get the init.d files that will be compliant with the breezy

```
$ cd /usr/local/src ; mkdir debian ; cd debian
$ mkdir clamd ; cd clamd; wget http://ftp2.de.debian.org/debian-volatile/pool/volatile/main/c/clamav/clamav-daemon_0.88-0volatile1_i386.deb
$ cd ..; mkdir freshclam; cd freshclam ; wget http://ftp2.de.debian.org/debian-volatile/pool/volatile/main/c/clamav/clamav-freshclam_0.88-0volatile1_i386.deb
```

**3rd** extract the packages without installing them :

_Example for freshclam_

```
$ cd freshclam
$ ar -x clamav-freshclam_0.88-0volatile1_i386.deb
$ tar xvzf data.tar.gz
```

Then change the files in the source :

```
$ cd freshclam
$ ar -x clamav-freshclam_0.88-0volatile1_i386.deb
$ tar xvzf data.tar.gz
```

**4th** copy the file at the right place

_Note_ : if you look at the files in the source directory, you'll see that the /etc/init.d/clamav-freshclam will be generated using the debian/clamav-freshclam.init.in and COMMON-FUNCTIONS from the file common-functions.

So I used to comment the line in the debian/rules that is doing this job (line 81) and did a copy of the debian init file as debian/clamav-freshclam.init (hope it is clear enough).

This is much more simple with the clamav-daemon init file, you just need to replace the debian/clamav-daemon.init with the good one.

The only thing I would need now is a way to avoid these files to be deleted at the debian/rules clean.

---

### Post by frodeseverin on 2006-03-20
Well, this is really a packaging bug, and should be treated as such. clamav-freshclam depends on new functions in /lib/lsb/init-functions, and these can be found in e.g. the lsb-base package from Debian Testing ([http://packages.debian.org/]("http://packages.debian.org/testing/misc/lsb-base")). 

I will report it as a bug.

;)Frode

---

### Post by frodeseverin on 2006-03-20
Take a look at [the Ubunt Bugs database]("https://launchpad.net/distros/ubuntu/+source/clamav/+bug/5240")

;)Frode

---

