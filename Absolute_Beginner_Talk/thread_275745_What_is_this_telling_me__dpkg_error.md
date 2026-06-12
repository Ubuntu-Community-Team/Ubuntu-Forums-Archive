---
title: "What is this telling me ?? dpkg error"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by eisle89 on 2006-10-11
When I try to install packages I get: 
Errors were encountered while processing:
 postfix
 courier-pop
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I correct this ?? TIA

---

### Post by meng on 2006-10-11
What command did you enter to get this output?

---

### Post by eisle89 on 2006-10-11
> **meng said:**
> What command did you enter to get this output?
Anytime I try to update, whether I use Synaptic, Automatix or Update Manager at the end of the install I get this error. E: is my DVDR drive letter in Win XPx64 and where I installed ubuntu from ... any connection ?? Just a n00b clutching at straws. The installed programs seem to install and run OK though. TIA

---

### Post by paulius2003 on 2006-10-11
do you by any chance still have the ubuntu DVD in your dvd-rom?  Or did you modify anything or try to update Ubuntu?

---

### Post by meng on 2006-10-11
E: doesn't mean the same as E: in Windows! (but it's a creative thought) I suspect E is short for error.
I'm not sure how this came about, but it probably has persisted since you installed some package - I don't suppose you remember what was the last package you installed before the error occurred?

---

### Post by paulius2003 on 2006-10-11
> **meng said:**
> E: doesn't mean the same as E: in Windows! (but it's a creative thought) I suspect E is short for error.
I'm not sure how this came about, but it probably has persisted since you installed some package - I don't suppose you remember what was the last package you installed before the error occurred?

arg this is true, why didn't I think of it.  

This could have happened because he modified a package settings or something?  Maybe dpgk-reconfigure something?

---

### Post by eisle89 on 2006-10-12
No, the CD is not in the DVDR and yes i did update unbuntu after it was first installed but no changes to packages ( I don't know how ). Is Courier a font maybe that got corrupted that the installers use ??

---

### Post by Delkster on 2006-10-12
> **eisle89 said:**
> Is Courier a font maybe that got corrupted that the installers use ??

The "E:" has nothing to do with your CD-ROM drive -- Linux doesn't recognise drives by such letters. As meng said, it's short for "error".

Courier is a mail server.

Sounds like something may have gone wrong with a package installation or something. Maybe something has got only half-installed. What happens if you enter the following command in the terminal?
```
sudo dpkg --configure -a
```

---

### Post by eisle89 on 2006-10-19
Thank you guys for the quick replies. Sorry I haven't responded sooner (work)

Delkster ..... I get this:

eisle89@eisle89-desktop:~$ sudo dpkg --configure -a
Setting up postfix (2.2.10-1ubuntu0.1) ...


Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: myorigin parameter setting must not contain multiple values: John R. Dignan
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-pop:
 courier-pop depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing courier-pop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-ldap:
 postfix-ldap depends on postfix; however:
  Package postfix is not configured yet.
 postfix-ldap depends on postfix (= 2.2.10-1ubuntu0.1); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-ldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-dev:
 postfix-dev depends on postfix (>= 2.2.10-0); however:
  Package postfix is not configured yet.
 postfix-dev depends on postfix (<< 2.2.10.0-0); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 courier-pop
 courier-pop-ssl
 postfix-ldap
 postfix-dev

---

### Post by nickpaton on 2006-10-19
FWIW - This post also details the same problem (but no solution either!):

[http://www.ubuntuforums.org/showthread.php?t=280257]("http://www.ubuntuforums.org/showthread.php?t=280257")

Could be worth keeping an eye also on it.

---

