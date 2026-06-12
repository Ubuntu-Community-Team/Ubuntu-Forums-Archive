---
title: "Clam AV?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-26
I use Eset Nod32 for XP, but I dont have a clue as to what I should use for Linux. Ive thought about using Clam AV, which seems a good open source product, but is it only for servers or what? Im not trying to start a "whats the best AV" war, but at this point SOME antivirus protection is better than none, especially since im new to this OS. Any advice would be awesome...

---

### Post by moore.bryan on 2007-03-26
[I]do regularly take files from your ubuntu computer to your xp one?  the only reason i ask is so many users will tell you that's the only reason to use an av program.

clamav is probably the best; in fact, i don't even know of another for linux.  it's windows counter-part clamwin is also excellent.
[/I]

---

### Post by GSF1200S on 2007-03-26
> **moore.bryan said:**
> [I]do regularly take files from your ubuntu computer to your xp one?  the only reason i ask is so many users will tell you that's the only reason to use an av program.

clamav is probably the best; in fact, i don't even know of another for linux.  it's windows counter-part clamwin is also excellent.
[/I]

I dual boot Ubuntu and WinXP... I use NTSF3g to use Win files in Ubuntu. It seems to me like ClamAV is only a server AV, but then Im a noob. Im still having problems installing stuff on Linux, but I figured if everyone in the Ubuntu community thought it was important Id struggle with getting AV on here... Of course, installing an AV is #1 priority on Windows (Nod32 is what I use), so I thought Id ask...

---

### Post by MrKlean on 2007-03-26
There's also an Avast version for windows.  The only reason for an AV now in Linux, I hear.. is if you transfer files from Linux to windows... to run !  Most viri won't run on Linux itsself.

---

### Post by MrKlean on 2007-03-26
Grrrrrr.. I meant Linux LOL!!

---

### Post by euler_fan on 2007-03-26
[This]("http://ubuntuforums.org/showthread.php?t=318091&highlight=install+clamav") is a pretty good guide to installing clamAV. Clamtk is the GUI for clam under Linux, and can be installed from synaptic (assuming you're running gnome or xfce).

I don't know if you want to do all of it, but it is the easy way if you are not interested in the most recent version. If you are, that will require installing from source. Unfortunately, Ubuntu does note have a "volatile" repository for things like the latest versions of ClamAV that tend to update alot, etc.

To install from source, go [here]("http://www.clamav.net/") and download the latest stable release.

From here I would look at both the documentation [here]("http://www.clamav.net/doc/latest/clamdoc.pdf") is really pretty good and also [this thread]("http://ubuntuforums.org/showthread.php?t=318091&highlight=install+clamav") which is decent as well. Bouncing back and forth should let you set it up.

Hope that helps.

---

### Post by moore.bryan on 2007-03-26
*excellent suggestions from euler_fan.  i used avast years ago on a windows 2000 machine, but found clamwin/clamav caught so much more.*

---

### Post by bodhi.zazen on 2007-03-26
Antivirus on Linux is always an interesting topic.

The link to the how-to is a good one.

I think the bottom line though, at least IMO, is that at this time there are no viruses that run on Linux, even running windows viruses on Wine fail.

So ....

[list=number][*]Running antivirus programs most often results in false positives. This is problematic in that you will spend time tracking these down, and after a while, may not run or not trust you antivirus, which is the same as not running antivirus, so why bother ?


[*]If you run Windows you need an antivirus program **TO RUN IN WINDOWS**. Do not transfer files directly from Linux -> Windows (via ntfs-3g or otherwise) as this will compromise security on the WINDOWS side.


[*]IMO the only reason to run antiviurs on Linux it to "protect" other windows computers. for example, if you run linux as a gateway or mail server for windows clients. Thus most Linux antivirus seems server (and for that matter E-mail) based. I do not feel obligated to police windows viruses on my Linux desktop.[/list]

Links :

	[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

	[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) 

HTH

---

### Post by juantovarm on 2007-03-26
There's really no need to run an AV under Linux. If you are worried about infecting a Windows system, use an AV under Windows. Linux is such a secure OS that you would have to intentionally infect your machine, assuming you knew how to and assuming you had root privileges. On the other hand, all you need to do is double click on an executable file to get infected under Windows. My opinion, do not waste system resources on an AV under Linux, and forget about the virus paranoia.

---

