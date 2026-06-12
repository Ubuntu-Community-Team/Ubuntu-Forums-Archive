---
title: "Would like to know more about 'chntpw'..."
date: 2013-02-22
forum: Any Other OS
---

### Post by benny7440 on 2013-02-22
My issue arrived when a person I know had a problem with his desktop: did nothing.):P

First, I found that the CRT was damaged. A feew months passed by & I found a suitable CRT for his old machine.

Then the machine started with some 'beeps'only & did nothing else. I opened the box, took out the RAMs, cleaned them well & resitted them. Problem solved: the machine tried to start but, its only Win XP Pro acct (Administrator) has a forgotten pwd.

He needs this machine for his shop due to a program there he used to use weekly. Now everything is locked out of his reach, but it's supposed to be there.

There was someone that "fixed" that machine a few years ago but his not reachable anymore; he was the one that put that pwd there.

After reading a lot about the diferent ways to deal with this & after trying the most 'at hand' method (Safe mode etc.) feel that the next step now is to try something directly from linux. chntpw is going to be.

That machine's located away from where I am & there's no internet access from there. I've a Puppy Linux 431 live cd & another Lupu live cd (which is derived from Ubuntu), also a bootable pendrive with DSL (Knopix): all these are bootable there.

My 2 questions here are:
1) How to run chntpw there if I'll be booting up PL Lupu, say?
2) Is the SAM file encoded in a special way that one needs, say, a codification table for been able to extract the position of the current pwd & substitute it with 'nothing'?

Thanks for any insights given around these issues!

---

### Post by varunendra on 2013-02-23
I'm not familiar with Lupu, but if it uses apt as package manager and uses same or similar repositories as Ubuntu, you can install it with:
```
sudo apt-get install chntpw
```
Obviously, you must be connected to internet while installation. Better create a Live (persistent) USB and install it beforehand where you have internet access.

Once installed, just take a look at its man page, it is really short and easy to follow. Main part of your interest is (example)-
> **ntfs-3g /dev/sda1 /media/win ; cd /media/win/WINDOWS/system32/config/**
Mount  the  Windows  file  system and enters the directory \WINDOWS\system32\config where Windows stores the SAM database.

**chntpw SAM system**
Opens registry hives SAM and  system  and  change  administrator account.  This will work even if the name has been changed or it has been localized (since different language versions of NT  use different administrator names).

**chntpw -l SAM**
Lists the users defined in the SAM registry file.

However, if you need even more easy to use tool, try [HBCD]("http://www.hirensbootcd.org/download/"). It contains many NT password reset tools and some of them are pre-configured to auto-detect the SAM files.
(Besides NT password changers, it has hundreds of other utilities as well)

Also, if you need to 'Recover' an NT password, you can use [Ophcrack]("http://ophcrack.sourceforge.net/") live cd. Although the recovery process can take much longer and can even fail in case of long and complex passwords, while resetting is guaranteed and is done instantly.

---

### Post by benny7440 on 2013-02-24
Thank you, varunendra, for replying!

I think I'll try your solution in this case but, before the final attempt, I'll practice right here to install chntpw in/from PL528; then, if averything works fine I'll move it to a cfcard or something else & re-check. Hope it works.

PS. I don't have a Windows installation here so can't be fully sure it will work somewhere else. Now, I'm imagining creating a dummy set of folders to test it, at least to the point of getting it somewhere...

If I try this I'm posting the results below.

Edit: I tried using your command for getting chntpw as is as well as without 'sudo' but my system doesn't recognize the command. I'll check other alternatives...

---

### Post by benny7440 on 2013-02-24
I've stumbled upon an old cfcard with an unproven Warytiny installation inside with what seems to be enough free space. Now, where & how I can get "chntpw" directly using my Firefox browser? Then I'll have to resolve the isuue of installing it in anyone from the following list: (1) DSL, (2) PL431 or (3) Lupu (think is = to PL 528).

Edit: The reported free space within the CFCard is 17 MB, hope this's enough for what's to be d/l.

PS. I'll test this Wary Tiny installation in that machine, first of all...

Thanks!

---

### Post by benny7440 on 2013-03-05
I managed to run at the faulty computer chntpw but , sadly, it never recognized the HDD or found an appropriate driver for it. Sorry, I failed to test (probe) for the specifics of the hdd; it occured to me after leaving the place.

Now I'm going to give kon-boot a chance, lets see what happens!

---

### Post by varunendra on 2013-03-05
If bandwidth is not a problem for you, I strongly recommend HBCD again ([http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)). It makes all the hard work too easy.

---

### Post by benny7440 on 2013-03-05
If it does not do the job (kon-boot) Hirens solution is going to be my next choice. Thanks for replying!

Edit: I'm still interested in the way one can extract the location of the pwd within the apropriate file within windows xp & how to reset it without damaging neihboring bytes, is it that dificult?

---

### Post by benny7440 on 2013-05-01
Last week I found an old BartPE cd & ran it at the computer with the problem & used 2 of the included tools for this purpose (unknown apps 'till now). Both seemed to run ok then but none convinced windows.

After a couple of trials, I've tried to get to a page where I can d/l either Hirens cd or UBCD but at both of the pages I can't find a d/l link for it; all there is are links for other things that I don't want nor need.

Have been reading about how to extract from a system info about the drivers used for a device (hdd). Found something for using from the Command prompt at a microsoft-based system but need also the linux counterpart.

PS. Haven't finished my sources of info on this yet but if someone has the appropriate commands at hand & share them here I'll appreciate it very much. Thanks!

---

