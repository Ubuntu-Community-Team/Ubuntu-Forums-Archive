---
title: "Dovecot install/remove broken Help Please"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by drhiii on 2008-01-24
I have been trying to install a mail server onto 7.10.  Postfix installed and running nicely.  When trying to add pop3, decided to use Dovecot. The installation broke.  I have tried to apt-get remove, apt-get installed, both with the -f flag.... no go.  Output from a recent pass at it.

I cannot installed it, or remove it.  Have tried adding an empty file for dovecot.conf and dovecot-ldap.conf, adding sample files of the same name, as this seems to be where it is in part failing.  Nothing is working.  I also now cannot install anything else because it keeps stumbling over this.  Anyone offer help on how to sanatize this off the system, or, how to force an installation of Dovecot with a big hammer, or how to get past this and install pop3 to work with Postfix so I can just get a simple mail server working?

tx

Setting up dovecot-common (1:1.0.5-1ubuntu2.1) ...
Not replacing deleted config file /etc/dovecot/dovecot.conf
Not replacing deleted config file /etc/dovecot/dovecot-ldap.conf
chmod: cannot access `/etc/dovecot/dovecot-ldap.conf': No such file or directory
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.5-1ubuntu2.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-common
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wormser on 2008-01-24
I found a [thread]("http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/") that might help.

> After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

---

### Post by drhiii on 2008-01-24
Thank you SO much for responding.  I came across this a little earlier and tried it to no avail, but on your response, went back to it and tried the   apt-get -f install    and then   apt-get upgrade    back and forth.  Still, no go.  

But I appreciate your responding to this.  Am worried that I may in a loop that won't let me out.  I cringe at the thought of a reinstallation, but may be facing that... sigh.

If you have any other ideas, throw them out.  Am all ears...

---

### Post by wormser on 2008-01-24
I have never really run into this type of problem myself.  Try this.

sudo dpkg --remove packagename

Take a look at the man page for dpkg or search the forum.  Sorry I cannot remember.  There is also another command like apt-get remove -f.  I cannot remember it exactly and do not feel like searching for it.  Sorry, but it might get you in the right direction or give you something to search. -brutally honest there but I did respond. lol

---

### Post by drhiii on 2008-01-24
Rats, tried your recommendation and no joy.  Follows is the output.  But, I continue to try variations of all this.  I too do not run into this kind of problem.  Things have worked very well so far.  Have just run into a gotcha that may end up in an endless blackhole, requiring a reinstallation, sigh.  I appreciate your continued respones!



dpkg --remove dovecot-common
(Reading database ... 199880 files and directories currently installed.)
Removing dovecot-common ...
invoke-rc.d: initscript dovecot, action "stop" failed.
dpkg: error processing dovecot-common (--remove):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-common

---

