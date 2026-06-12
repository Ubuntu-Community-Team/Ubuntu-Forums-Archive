---
title: "no ubuntu session after changing yaboot.conf"
date: 2005-09-23
forum: Apple PPC Users
---

### Post by ubuntubrian on 2005-09-23
I posted this on the Breezy development forum also-
This is somewhat involved: I upgraded to Breezy with no problems and everything worked perfectly other than this strange result when typing "l" (for Linux) to boot:
"loading kernel
/pci@f2000000/mac -io@17ata 4@ 1f000/disk:8, \\macosx: no such file or directory"

I typed "help" and "tab" to find the os's to boot and got:
"Linux Old"
I typed in either and Ubuntu booted fine, again perfect.
I though that I'd check my /etc/yaboot.conf file and after reading the man page changed the default os to Linux from macosx. I saved the file and with much trepidation rebooted. I got the ubuntu log-in screen but after entering my Username and password I got a dialog that stated that my session lasted less than 10 seconds so I should log in failsafe. Gnome failsafe session wouldn't start but terminal failsafe would. The details of the dialog are:
/etc/gdm/PreSession/Default: Registering your session with wtmp and ump
/etc/gdm/PreSession/Default: running:/usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0.Xservers" "-l ":0" "brianokeefe
/etc/gdm/Xsession:Beginning session setup...
/etc/X11/XSession.d/30 xorg-common_xresources:line16:XRDBOPTS:command not found
/etc/X11/XSession.d/30 xorg-common_xresources:line16:XRDBOPTS:command not found
_IceTransTransNoListen: unable to find transport tcp
_IceTransmkdir: ERROR: euid! =0, directory /dev/x will not be created
_IceTransmkdir: ERROR:cannot create /dev/X
_IceTransPTSOpenServer: mkdir (/dev/x) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu
_IceTransMakeALLCOTSServerListeners" failed to open listener for pts
_IceTransISCOpenServer: protocol is not supported by an ISC connection
_IceTransOpen: transport open failed for isc/ubuntu
_IceTransMakeALLCOTSServerListeners" failed to open listener for isc
_IceTransISCOOpenServer: protocol is not supported by an SCO connection
_IceTransOpen: transport open failed for sco/ubuntu
_IceTransMakeALLCOTSServerListeners" failed to open listener for sco


(I typed the message in as I could not copy it so may be typos)

I started the terminal failsafe session and changed the default os in yaboot.conf back to "macosx" but get all the same errors.

Any help??

Many thanks
 ](*,)

---

### Post by ubuntubrian on 2005-09-23
A little more info: I had started Kate in Konsole yesterday as root in order to make the change from macosx to Linux as the default OS. Although Kate opened it was after I got several error messages in the Konsole session first. they mostly referred to incorrect EUID being 0. I didn't copy them as Kate started and I went on to edit yaboot.conf file.
It's almost as if there is some error that has been cumulative and now has become fatal regarding my log-in settings.
Help?

---

### Post by ubuntubrian on 2005-09-23
I was able to boot into command line mode with ctrl+alt+F2 and then move my .ICEauthority file out of the way and all is back to normal.

---

