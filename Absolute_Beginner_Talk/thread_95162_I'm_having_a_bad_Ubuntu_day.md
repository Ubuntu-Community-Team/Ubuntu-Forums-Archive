---
title: "I'm having a bad Ubuntu day"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-11-25
It all started when my GPS receiver was no longer seeing ttyS1. After fiddling for a few hours with this, I started updating and upgrading everything, including Hoary to Breezy. During the configuration of Breezy, one of the steps gave me the option to install the fresh configuration file, use my old one, or choose 'D' so it would show me the differences. Of course I did not understand the differences, and at the bottom of the terminal there was an (END) highlighted. I've been here before, I don't know how to get out of this, so I star hitting 'Enter', spacebar, Ctrl, Alt, Esc, nothing gets me back into the suspended process. Anyhow, I had to kill the terminal, and started apt-get dist-upgrade again, but now I get all kinds of error messages:
```

:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libpt-plugins-alsa libpt-plugins-v4l2 mplayer-386 xfce4-mixer xine-ui
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.2.4-1ubuntu2) ...
Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.
Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                        [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server-4.1:
 mysql-server-4.1 depends on mailx; however:
  Package mailx is not configured yet.
dpkg: error processing mysql-server-4.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 mysql-server-4.1
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I also get an error at first login, I forget the text, It had some stern language in it, and It ordered me to configure I don't know what because it needed I don't remember how many 100's of permissions. I'll post the text of it in another posting.
As you can see, I am in dire need of help.
Can someone please clue me in?

E_M

---

### Post by Brunellus on 2005-11-25
yuk.  have you tried

```
sudo apt-get -f install 
```

yet?  the -f argument will attempt to fix the dependency proglems.  I had a similar experience upgrading from hoary to breezy, and that fixed it for me.

---

