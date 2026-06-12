---
title: "Trying to run Evolution (Feisty)"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-10-30
I am attempting to run "Evolution", but after clicking on the icon, I get the loading indicator for a few seconds and then it stops. Nothing ever comes up at all.

When I enter "evolution" in the terminal I get this message:

> ******@*****-desktop:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:8833): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:8833): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:8833): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:8833): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)
******@*****-desktop:~$ 

I haven't a clue as to what this means.

Help would be appreciated.

---

### Post by laidback on 2007-10-30
I have no idea, but if it was me I'd be tempted to uninstall Evolution completely and then reinstall in the hope of better things.

---

### Post by devilears on 2007-10-31
before you re-install, open a terminal window and rename the .evolution folder to .evolution.old like this: mv .evolution .evolution.old    then try starting evolution again.

---

### Post by crav on 2007-10-31
> **devilears said:**
> before you re-install, open a terminal window and rename the .evolution folder to .evolution.old like this: mv .evolution .evolution.old    then try starting evolution again.
And if you happen to be wondering, what this command is going to do is backup all the old data, just in case.

---

### Post by thelugnut on 2007-10-31
> before you re-install, open a terminal window and rename the .evolution folder to .evolution.old like this: mv .evolution .evolution.old then try starting evolution again.

Did that, but situation still as described in original post. 

Appreciate the reply, though.

---

### Post by soggy on 2007-11-10
Hello,
I'm running into the same problem (small icon in low tray "starting evolution mail", but then it disappears), but with 6.06 Dapper Drake.  I installed it on a PC for someone last summer, but then it sat because he preferred to buy a new windows box.  I'm looking to use it now but Evolution isn't working.  I'm not really linux savvy so the uninstall/reinstall Evolution suggestion isn't sufficient in detail on how to proceeed.  (I still need to install a network card so the PC is not currently online.  All programs/files have to be loaded on it by USB key or CD.)  Thanks.

---

### Post by mb01915 on 2007-11-10
I have found Evolution to be very difficult to use and not that good a program.

Evolution is an old email client that Novell picked up in a company acquisition and not really supported very well.

My suggestion is to use Thunderbird or get a Gmail account.

---

### Post by mivo on 2007-11-10
> **mb01915 said:**
> I have found Evolution to be very difficult to use and not that good a program. Evolution is an old email client that Novell picked up in a company acquisition and not really supported very well. My suggestion is to use Thunderbird or get a Gmail account.

Thunderbird has relatively poor IMAP support (compared to Evolution), no Exchange Server support, and no way to sync it with your PDA. It also doesn't have any PIM features out of the box, but there are some add-ons, though the ones I looked at were not mature or full-featured. I use Evolution for both for work and for personal mail, and it works really well on my machines (7.04 and 7.10). Recent versions of Evolution also had some useful features added like an automatic backup and restore option.  Evolution's quite mature and good, in my experience.

Anyway, Thunderbird is a nice email client too and I have used it in the past. It just aims at a different audience and offers a different set of features. :) It does have the plus of including a news/usenet client, which I wish Evolution also featured.

---

### Post by soggy on 2007-11-10
Some follow-up:
-sudo evolution at command line (courtesy of mavila on another thread) gets the program to start, but must keep command line window open or program closes.  have to use this each time as starting with file menu or icon still causes an aborted start.  I have Thunderbird on my laptop (windows), but coming from Outlook, I would like the integrated mail/tasks/calender that Evolution seems to offer. is uninstall/reinstall as simple as remove/add.  this computer is not yet on the net so downloads are a pain. thanks.  (10 Nov/8pm PST addition: issue appears resolved by rebooting as Evolution now opens via icon though email account settings from yesterday are nowhere to be found.  I can redo those though.  Thanks for the help.)

---

