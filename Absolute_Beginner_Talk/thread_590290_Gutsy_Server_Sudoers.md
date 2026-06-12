---
title: "Gutsy Server Sudoers"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rhdinah on 2007-10-24
I freshly installed a copy of Gutsy Server ... no problem logging in ... but I've no special privileges like with the Desktop. If I try to sudo with my login and provide my password ... it says I'm not in the list of sudoers ... I can't even cat the /etc/sudoers file as I am not privileged to do so. So ... where from here ... install went flawlessly. Thanks for any suggestions! :confused:

---

### Post by taurus on 2007-10-24
If you installed the server version, then you won't have any window manager so you need to install one if you plan to run it.  And regarding sudo, what's the output of this command from a terminal?

```
id
```

---

### Post by rhdinah on 2007-10-24
> **taurus said:**
> If you installed the server version, then you won't have any window manager so you need to install one if you plan to run it.  And regarding sudo, what's the output of this command from a terminal?

```
id
```

I have a Gutsy Desktop version working well on [this] system :) ... I loaded another system with the Gutsy Server.

>> what's the output of this command from a terminal?

***myloginname*** is not in the sudoers file.  This incident will be reported.

Issuing a who from the command line reflects ***myloginname***.

Thanks!

BTW I can cat /etc/group and I am in the adm group.

---

### Post by rhdinah on 2007-10-24
I have resolved this ...

I rebooted the machine from the CD and chose to reboot in recovery mode ... giving me a root shell on / ... I then cat /etc/sudoers ... turns out it was missing the following lines at the end of the file:

[FONT="Courier New"]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/FONT]

So I added the missing lines to the file using vi ... and then rebooted ... it still did not work ... same system response ...

So obviously there was more in error than just this. Since this was a fresh install ... I did it again ... with a fewer subsystems being added to the base system ... it worked.

I rather doubt this was a hardware problem on my system ... nor did I run out of hard disk. So I can only assume that the install initially failed and stuff that was to follow was flushed down the bit bucket ... with no external alarms. Perhaps just something for Development to keep in mind for the future.

Thanks for the help though ... :)

---

### Post by derjusti on 2007-11-04
Running into the "not in sudoers" problem as well (for gutsy) now trying a re-install, but perhaps a "bigger" problem idd!

---

### Post by derjusti on 2007-11-04
re-install without mail server did the trick! thanx though

---

### Post by cjwatson on 2007-11-14
Could somebody who can reproduce this please file a bug on [https://bugs.launchpad.net/ubuntu/+source/user-setup/+filebug](https://bugs.launchpad.net/ubuntu/+source/user-setup/+filebug) and attach the /var/log/installer/syslog file? (You'll need to be root to read that file, so you will probably need to boot in recovery mode in order to extract it.)

---

