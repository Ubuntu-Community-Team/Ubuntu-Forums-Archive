---
title: "GNOME Desktop No Longer Starts"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mikedavi on 2007-09-09
I was attempting to upgrade Thunderbird.  The PC froze, and I had to manually turn it off.  Now it no longer loads GNOME desktop.  I can only get in command line mode.  

Here are the errors I get when booting.  Any ideas on how to fix this?  Could there be an error on the hard drive?

I can boot and access the hard drive using the Live CD.

Doing wacom setup   [OK]
Starting kernel log    [OK]
usr/bin/dbus-uuidgen:  error while loading shared libraries: libdbus-1.so.3:  cannot open shared object file:  No such file or directory
perl: warning: Setting locale failed:
perl: warning: Please check that you locale settings
LANGUAGE=(unset)
LC_ALL=(unset)
LANG="en_UI.UTF-8"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C")
Starting GNOME Display Manager   [Failed]

---

### Post by nonewmsgs on 2007-09-09
```

sudo dpkg-reconfigure xserver-xorg

```

do that in your commandline after loging in and that should fix things up.

---

### Post by mikedavi on 2007-09-09
Thanks for the reply.

That did not work.  Here's what I get after running that:

perl: warning: Setting locale failed:
perl: warning: Please check that you locale settings
LANGUAGE=(unset)
LC_ALL=(unset)
LANG="en_US.UTF-8"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C")
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl15 /usr/share/perl5 /usr/lib/perl5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
BEGIN failed-compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.

This continues with similar compilation errors for these files Question.pm, Config.pm, Log.pm,Db.pm, dpkg-reconfigure

---

