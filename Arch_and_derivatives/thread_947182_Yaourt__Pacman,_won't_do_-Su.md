---
title: "Yaourt | Pacman, won't do -Su ?"
date: 2008-10-14
forum: Arch and derivatives
---

### Post by handy on 2008-10-14
I've been using my neglected Arch test install on my 2nd machine, it is well over a month, more like two months since it has been updated.

At this stage, when I do Yaourt -Syu, it sync's & then delivers the following error:

*error: failed to prepare transaction (could not satisfy dependencies)* 

After which it checks for package upgrades gives me a big list (due to the time since last upgrade) gives me the download & installed sizes & returns me to the prompt!?

I actually had this problem last night before I installed xfce4, today I have removed much of Gnome, some other packages & installed other packages, all without problem.

So, I'm scratching my head. :confused:

Advice welcome? :-)

---

### Post by handy on 2008-10-14
There is a new kernel going out at the moment with all of the related files, so just *maybe*, that is what is causing my problem, my server my not be in the process of being updated?

[I]**[Edit:]**

Though I will be surprised if this is the case, as I have had the problem for over 24 hours now.[/I]

---

### Post by lswest on 2008-10-14
I had a similar problem on my PC, and then I saw this news item on the arch site: [http://archlinux.org/news/411/](http://archlinux.org/news/411/)

Seems there's a file conflict that occurs when trying to install a new update.  However, you didn't mention any file conflicts (that should have occurred if this is the case).

Do you have any information on what dependency can't be satisfied? (I don't use yaourt so I don't know entirely what the error output is like)

Also, I haven't updated my PC in the last 2 days, been too busy, so I don't know if the error is shared by anyone (are there any posts similar on the Arch Forums)?

---

### Post by handy on 2008-10-14
I upgraded another machine earlier yesterday & struck the klibc problem, which was very easy to handle once you know about (like so many computer problems).  The klibc problem gives a couple of hundred lines of errors!

[I]**[Edit:]**

This machine won't accept the klibc correction either. [/Edit][/I]

The problem I am experiencing gives only the one error quoted in my first post, I have no idea what is causing it, I need more clues? lol

---

### Post by lswest on 2008-10-15
I've just tried to upgrade my Arch install on my PC and it worked without a hitch...I really don't know.  Maybe a package you have installed is no longer available/has a different name and therefore causes dependency errors?

---

### Post by handy on 2008-10-15
It is my initial Arch testing install, it is old & neglected & been given hell as I have rarely had use for it beyond testing.  

I installed xfce4 a day or two ago on it, & then ripped Gnome out from under it.  All the while this -Su problem existed.

So, I've been doing a fresh install of Arch today, & it has made me work hard for it.

First installation attempt could not find the menu.lst file at the Install Bootloader section of the installation.  So I stuck a Ubuntu LiveCD in & formated the drives, deleting the /swap & changed the /home files system to JFS.

The second install went fine, until after the initial reboot when I found I had no network, three nics & no network.  Turned off the two on the motherboard to make it easier for me.  Spent hours trying to get an error free LAN, eventually after another network restart, I could continue without errors & now am finally doing the first -Syu.

I wonder what problem is waiting for me next! :lolflag:

---

### Post by handy on 2008-10-15
Trying to bring in any individual packages is error prone & halts.

I have had enough of this install for the time being. :-(

[I]**[Edit:]**
The problem is caused by a bug in the current kernel, for a an easy workaround that allows you to still use the current kernel & not have to downgrade see this link:

***_[http://ubuntuforums.org/showthread.php?t=954112](http://ubuntuforums.org/showthread.php?t=954112)_***
[/I]

---

