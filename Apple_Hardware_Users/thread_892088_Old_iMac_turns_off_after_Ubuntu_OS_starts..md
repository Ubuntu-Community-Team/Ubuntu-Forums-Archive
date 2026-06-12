---
title: "Old iMac turns off after Ubuntu OS starts."
date: 2008-08-16
forum: Apple Hardware Users
---

### Post by radi0j0hn on 2008-08-16
I've got an old iMac (all in one blue one with CRT built in) and after a clean install (whole HD) it came time to reboot.  It kicked out the CD, up came some things such as "boot:" and then it began to autoload. Thought I was ready to got and then the iMac simply powers down.

Any idea what is happening?   TIA John

---

### Post by grundygreen on 2008-08-16
Is it a g3?
If so read thru this.
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

---

### Post by rakan21 on 2008-08-18
is this immediatly after you installed Ubuntu or just a while after using it?

Remember even though Mac OS X is Virus free dosn't mean Ubuntu is!

---

### Post by grundygreen on 2008-08-18
I just did an install on a PPC gumdrop iMac.
It is doing the same thing it powered down after yaboot.
I need to find this fix as well.

---

### Post by stream303 on 2008-08-18
The most likely cause is that your video frequencies are wrong.  You'll need to go back into the system using rescue techniques, and manually change your xorg.conf with values listed here:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

---

### Post by arranmc182 on 2008-08-18
Make sure the internal battey is not dead as i have had weird problems with Mac's in the past that have had dead batteries and if it is not that as the other poster says it may be video frequencies are wrong but can be changed via the terminal

---

### Post by grundygreen on 2008-08-20
> **stream303 said:**
> The most likely cause is that your video frequencies are wrong.  You'll need to go back into the system using rescue techniques, and manually change your xorg.conf with values listed here:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

I've done that in the past myself.
That doesn't seem to fix it on Hardy.
At least not for me.
We haven't had to edit xorg since feisty either.
This something else. The unit powers down after yaboot.

---

### Post by grundygreen on 2008-08-21
I'm trying something tricky.
I installed feisty.
Did a full update and upgrade via command line.
added the ports repository for hardy to sources list.
I skipped gutsy ( I know Dicey)
sudo apt-get update 
sudo apt-get upgrade (took awhile even with a cable modem)
Sudo apt-get dist-upgrade ( still working on it)

Will report back.

---

### Post by grundygreen on 2008-08-21
> **grundygreen said:**
> I'm trying something tricky.
I installed feisty.
Did a full update and upgrade via command line.
added the ports repository for hardy to sources list.
I skipped gutsy ( I know Dicey)
sudo apt-get update 
sudo apt-get upgrade (took awhile even with a cable modem)
Sudo apt-get dist-upgrade ( still working on it)

Will report back.

Had broken depedencies that had to be fix via dpkg --configure -a

suggest feisty install.
update & upgrade
then add ports repositoriy
then do dist-upgrade
then redo update and upgrade.
That should cause less issues and do it from shell.
:lolflag:

---

