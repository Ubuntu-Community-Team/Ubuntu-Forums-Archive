---
title: "What's the best dpkg options-setup?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by n3b on 2007-05-28
*Sorry for my bad English&#8230;*
First of all, I'm an offline ubuntu feisty user, so actually I need to know how to 
handle dpkg suite effectively.

The configuration file /etc/dpkg/dpkg.cfg has by default only one option set:  
log /etc/dpkg/dpkg.cfg. What if I run dpkg at this point? Would dpkg warn and/or prompt me
for any risky circumstances(like downgrade)?
As anybody can see in the man page of dpkg, there are many other important 
options. Some of these:
I really find them convenient &#8211;- marked as # C,
while others not -&#8211; marked as # N, 
and even a few that I do not understand at all -&#8211; marked as # ?.

Please help me to understand the whole thing, also do appreciation for the 
convenient ones, if necessary.

Options listing:
**abort-after**=1 # C
**auto-deconfigure** # C
**debug 1** # C &#8211; Does this works for every dpkg <action>? How can I bind together                      
more than one value?

----things block----
**refuse-downgrade** # C
**force-configure-any** # C &#8211;- I do not grasp this too well. Is there any inconvenient?
**refuse-hold** # C
**refuse-remove-reinstreq** # C
**force-depends** # C
**refuse-depends-version** # C
**refuse-breaks** # C
**refuse-conflicts** # C
**(force or refuse?)-confmiss** # ? What if I leave this line as blank? Would dpkg warn 
me later to decide what to do?
**force-confdef** # C
**force-overwrite** # C &#8211; Once I do not accept downgrade and skip-same-version, any 
other package shall be installed, right?
**(force or refuse?)-overwrite-diverted** # ? &#8211; What is a diverted file?
**refuse-architecture** # C
**(force or refuse)-bad-path** # ? &#8211; Should I just leave blank and wait for the dpkg's 
report(if exists)? &#8211; Then I would just insert an additional path for the env. 
variable PATH&#8230;
**refuse-not-root** # C
**refuse-bad-verify** # C &#8211; is there any threatening side effect?
----End of things block----

**new | old** &#8211; The default is new. If comes out any case where the old is the only 
option, would dpkg report me that?

**R | recursive** # ? "Recursively handle all  regular  files  matching  pattern
                           *.deb  found at specified directories and all of its sub-
                            directories." &#8211; If this includes subdirectories, then there 
should be many non-interesting cases to apply this option...

**O | selected-only** # C &#8211; This is dedicated for the packages selected to 
installation, right?
**skip-same-version** # C &#8211; If the refuse-downgrade doesn't include skip-same-
version, then this is necessary.
**no-debsig** # ? Is this really needed?

Outside questions: 
**1)** Do apt and aptitude need similar configuration? Or do apt and 
aptitude provide a smart environment, which takes the best convenient decisions 
and prompts the user when is really needed? And even informs the user about 
what's going on?
**2)** Should i use GDebI instead of dpkg?

Thank you!

---

