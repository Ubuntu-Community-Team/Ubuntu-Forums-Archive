---
title: "FreeNX Setup"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by thelarster on 2006-09-21
I have searched the forums and Google and cannot figure out what I am doing wrong here. I'm trying to set up FreeNX and get the errors below - any ideas?

Side note: I can SSH fine using Putty from my Windows machine so I think that part is set up.



----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

----> Testing your nxserver connection ...
/etc/ssh/ssh_config: line 42: Bad configuration option: ListenAddress
/etc/ssh/ssh_config: line 43: Bad configuration option: HostKey
/etc/ssh/ssh_config: line 44: Bad configuration option: ServerKeyBits
/etc/ssh/ssh_config: line 45: Bad configuration option: LoginGraceTime
/etc/ssh/ssh_config: line 46: Bad configuration option: KeyRegenerationInterval
/etc/ssh/ssh_config: line 47: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: line 48: Bad configuration option: IgnoreRhosts
/etc/ssh/ssh_config: line 49: Bad configuration option: IgnoreUserKnownHosts
/etc/ssh/ssh_config: line 50: Bad configuration option: StrictModes
/etc/ssh/ssh_config: line 51: Bad configuration option: X11Forwarding
/etc/ssh/ssh_config: line 52: Bad configuration option: PrintMotd
/etc/ssh/ssh_config: line 53: Bad configuration option: SyslogFacility
/etc/ssh/ssh_config: line 59: Bad configuration option: PermitEmptyPasswords
/etc/ssh/ssh_config: line 60: Bad configuration option: AllowUsers
/etc/ssh/ssh_config: terminating, 14 bad configuration options
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to

---

### Post by Marsolin on 2006-09-21
There may be some missing dependencies.  Did you install [FreeNX]("http://linuxappfinder.com/package/freenx") using a deb file or another method?

Have you run nxsetup?

cd /usr/NX/bin
./nxsetup --install

---

### Post by thelarster on 2006-09-21
Yes I installed it via deb file. I've also run the set up - when checking the status it says the freenx server is running.

---

