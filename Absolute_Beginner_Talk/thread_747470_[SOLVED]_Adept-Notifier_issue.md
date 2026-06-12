---
title: "[SOLVED] Adept-Notifier issue"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2008-04-06
Hi
I just installed OpenOffice 2.4.0 via the OOo download, not through the repos.

adept (notifier)  keeps wanting to  "upgrade"(downgrade)  back to 2.3, which are still  in the repos.

How can I keep it from wanting / not detecting to do this? :confused:

---

### Post by randcoop on 2008-04-06
Did you remove 2.3?  I did when I installed 2.4.  Although Adept shows Ooo as "upgradable" to 2.3, it defaults to no change in the action column.

---

### Post by baracuda68 on 2008-04-06
> **randcoop said:**
> Did you remove 2.3?  I did when I installed 2.4.  Although Adept shows Ooo as "upgradeable" to 2.3, it defaults to no change in the action column.
I did remove all of 2.3 via synaptic, prior to installing 2.4.   Even though it does not change the action, it still triggers notifier as a needed update, at system startup.
Is there a way to NOT have notifier detect OO 2.4?

---

### Post by randcoop on 2008-04-07
The only way I know is to create or edit your /etc/apt/preferences file.  There's a way to pin existing versions so that Adept ignores possible updates.  But I don't know how to do it well enough to instruct you.

Sorry.

---

### Post by baracuda68 on 2008-04-07
> **randcoop said:**
> The only way I know is to create or edit your /etc/apt/preferences file.  There's a way to pin existing versions so that Adept ignores possible updates.  But I don't know how to do it well enough to instruct you.

Sorry.
Thanks...I'll try and see...
:confused:
Anyone else?

---

### Post by baracuda68 on 2008-04-07
bump:( bump

---

### Post by randcoop on 2008-04-07
Okay, here's what works:

If you have an /apt/etc/preferences file, then edit it.  If not, you will make one.  

The appropriate lines in the file are:

Package: openoffice.org-base
Pin: version 2.4.0-12
Pin-Priority: 1001

But you will need to have such a section for each package (so the first of those three lines will change, for example, Package: openoffice.org-calc)

Each section of three lines you add will pin the 2.4 version (obviously, if your 2.4 version is not 2.4.0-12, substitute your version number there), and then they will no longer show as upgradable in adept.

---

### Post by hasinasi on 2008-04-07
Thanks for the help **randcop**!!! It worked great. 
Just one little addition: in my case each of the three-line-sections had to be separated by a blank line in order for it to work. 
Cheers, 
--hasi

---

### Post by baracuda68 on 2008-04-08
> **randcoop said:**
> Okay, here's what works:

If you have an /apt/etc/preferences file, then edit it.  If not, you will make one.  

The appropriate lines in the file are:

Package: openoffice.org-base
Pin: version 2.4.0-12
Pin-Priority: 1001

But you will need to have such a section for each package (so the first of those three lines will change, for example, Package: openoffice.org-calc)

Each section of three lines you add will pin the 2.4 version (obviously, if your 2.4 version is not 2.4.0-12, substitute your version number there), and then they will no longer show as upgradable in adept.
OMFrreakin'G!! It worked! Like a charm! You are thanked and this is marked as solved! Thanks again!:guitar:

---

### Post by randcoop on 2008-04-08
You're welcome.  

Please remember that so long as you have pinned programs in a preferences file, Adept won't see other versions.  This might matter is later on you upgrade to Hardy and want to install the Ubuntu version of 2.4.  If that happens, simply delete the relevant sections of the preferences file (there seems to be a bug that makes commenting out the lines not work).  The the next time you update, Adept will again see the possible upgrade, this time to Ubuntu's 2.4 versions.

---

