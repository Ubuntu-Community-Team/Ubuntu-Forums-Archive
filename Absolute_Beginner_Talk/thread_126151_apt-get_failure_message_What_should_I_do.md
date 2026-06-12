---
title: "apt-get failure message: What should I do?"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Hereford on 2006-02-05
Gaining confidence after successfully installing Adobe Acrobat Reader, I tried the same vehicle to install Mozilla Thunderbird.  The installation appeared to be progressing nicely until this final message appeared:
> Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 59161 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.0.7-0ubuntu05.10_i 386.deb) ...
Successful preinst
Setting up mozilla-thunderbird (1.0.7-0ubuntu05.10) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified  the -maxdepth option after a non-option argument -name, but options are not pos itional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argume nt -name, but options are not positional (-maxdepth affects tests specified befo re it as well as those specified after it).  Please specify options before other  arguments.

done.

What does this mean?  How/where/when do I manipulate -maxdepth and -name? 

 My terminal entry (following the "Unofficial Ubuntu 5.10 Starter Guide") was:
> sudo opt-get install mozilla-thunderbird
-Thanks-

---

### Post by yarvin on 2006-02-05
try using 'sudo apt-get isntall mozilla-thunderbird'

I've never seen or heard of 'opt-get'

try going to the Applications menu and installing thunderbird through 'Add Applications'. should be under 'Internet' as Thunderbird Mail client or something like that...

also:
if you typed 'sudo su' then your password
then typing 'passwd' and entering a new password for root
you can use root without having to type 'sudo' every time....

---

