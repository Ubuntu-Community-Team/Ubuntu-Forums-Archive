---
title: "Sudo / root"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by WelshChris on 2006-08-24
I can understand the reasoning behind encouraging the use of sudo, but could I suggest a note to this effect somewhere in the installation?

I've come back to Linux after a break of a few years, so I've tried a few distros this time around, but I must admit, I was a bit confused when I installed 6.06 and wasn't asked for a root password!

Again, I can understand the reasoning, safety and security, but previously if I wanted root in X I'd start up a terminal and su to root.

Maybe just a little note at some point during the installation?  I had to boot into Win and Google.

---

### Post by aysiu on 2006-08-24
Mac OS X never tells its users it uses *sudo* instead of a traditional root/user model, and it seems to do just fine.

I don't think you'll ever convince the developers to put in little notes like that. If anything, they're taking *out* notes. Breezy (and the Dapper Alternate CD) ask you where to install Grub. The new Dapper Desktop CD just installs it automatically to the MBR.

---

### Post by Turgon on 2006-08-24
Shuch note will only be for people who have tried linux before, and quite offen they will figure it out. But it could perhaps been mentioned in a kind of splash that displays some ubuntu features under the install (like the one in widnwos xp).

---

### Post by VirtuAlex on 2006-08-24
Horrible practice by the way. On certain systems Grub installs on IDE drive while master boot drive is SATA. And I agree that note is needed. I've already discussed this:
[http://ubuntuforums.org/showthread.php?t=222923]("http://ubuntuforums.org/showthread.php?t=222923")

---

### Post by WelshChris on 2006-08-25
I guess the assumption is that root priviledges would not be required that often.  However, for myself, since I know a bit of shell, and prefer vi as my editor, having a root terminal available is vastly more preferable than having to sudo everything.

While I applaud using Ubuntu as a user's Linux, there for the usual home computing tasks, I've seen quite a few posts on these forums along the lines of 'how do I amend this file' or 'how do I copy this file'.  Linux users have always had to tweak their systems to some degree, and removing (or at least depreciating) the root account is simply making things more difficult for the new user and the old.

However, having said that, it took me only a few seconds to get over the nasty surprise and get used to sudo, and finding a way to get a root terminal if I need it.  I guess it was my fault for not knowing more about the command in the first place!

By the way - Fedora doesn't do this..

---

### Post by aysiu on 2006-08-25
Ubuntu's target audience right now is a dream world.

Theoretically, it's targeted to "ordinary" users who wouldn't want to be bothered with things like root v. user or Grub.

In reality, though, the people who actually use Ubuntu really care about customizing their systems to exactly how they want it and do not want control taken away from them. I've heard many people complain that this lack of choice/information reminds them of Windows "thinking for [them]."

In the dream Ubuntu world, the installation itself is simple enough--you pop the disk in, you see how you like it, click on the "install" button on your desktop, answer a few simple questions, reboot and start being productive right away. From [the Ubuntu website](http://www.ubuntu.com/ubuntu): > When you finish your Ubuntu installation your system is immediately usable. On the desktop you have a full set of business productivity applications, internet applications, drawing and graphics applications, and games. Does that really happen, though? Are there beginners who would be confused by things like "root" and "Grub" who would be installing Ubuntu and then finding it "immediately useful"? I highly doubt it.

The only people who find Ubuntu immediately useful are people who have been using Linux long enough to be dedicated to free software already (and I assure you these people know what Grub and root are): they have all their music in Ogg, all their documents in .odt, they don't watch commercial DVDs on their computer, and they don't use Flash on the internet.

And the people who would be confused by terms like "Grub" and "root" would not find Ubuntu immediately useful. They have their music in MP3 format, watch commercial DVDs, have Word documents (.doc), and need Flash for the internet.

That said, I have to say I really like the *sudo* model a lot better than root/user, and if you want to use root instead, you can enable it, and ```
sudo -s
``` allows you to not have to keep typing *sudo* a million times.

Maybe it'd be good for Ubuntu to have two sets of tutorials--for new Ubuntu users who are old Linux users and new Ubuntu users who've never used Linux?

---

### Post by Metacarpal on 2006-08-25
I've been using Linux for a couple of years now, and I actually really like Ubuntu's use of sudo.  It makes system administration tasks a lot simpler for me.  No more starting a new session as root just to setup something that I wanted to use under my regular user account...

---

### Post by uberg on 2006-08-25
i remember when i first used breezy badger i had to have root!  Couldn't get along without.  By the time i updated to dapper drake, well, i have no need.  Am entirely used to the concept.  My roommate just recently got a laptop and i helped him install dapper drake (easy) and he was momentarly confused as there was no root.  Had to explain to him how it's done.

---

### Post by WelshChris on 2006-08-25
Might I suggest a forked installation method - basic and advanced?  Being able to specify whether I want runlevel 3 or 5 as default, a root account, more GRUB options (I've had to rip LILO out of my soul recently, sigh) and more control over package installations.

Ubuntu isn't alone in 'simplifying' installation, however, if Linux is to encroach on MS's territory with the average user, this is the way to go.  After a little experimentation with a couple of distros recently, I've come to the conclusion that we're not at the level of configuration automation that can be said of some OSs.  Yum with Fedora just isn't there yet - an update broke my wireless badly, and Synaptic on Ubuntu needed a bit of tweaking for a few packages, too - ask an ordinary user how to add a repository.

So, I think we are moving towards install and go, but I think all flavours of Linux require a bit of knowhow at the moment.


(Are there *really* people out there with all their music collections as ogg files?  Do they stare at you with an unblinking fixed gaze?

---

### Post by aysiu on 2006-08-25
My point is simply that, in a lot of respects, Ubuntu developers are designing Ubuntu as if Bug #1 is already fixed, but not in such a way as to actually fix Bug #1.

It's sort of like the DMV getting rid of the queue rope because it *should* not have long lines. That doesn't get rid of long lines... it's just operating as if long lines *shouldn't* exist (even though they do).

Ubuntu also operates as if free software is already dominant and that new users do not need to configure their systems after installing Ubuntu (no graphical root login, no *gksudo nautilus* launcher icons).

---

### Post by Metacarpal on 2006-08-28
> **aysiu said:**
> My point is simply that, in a lot of respects, Ubuntu developers are designing Ubuntu as if Bug #1 is already fixed, but not in such a way as to actually fix Bug #1.

It's sort of like the DMV getting rid of the queue rope because it *should* not have long lines. That doesn't get rid of long lines... it's just operating as if long lines *shouldn't* exist (even though they do).

Ubuntu also operates as if free software is already dominant and that new users do not need to configure their systems after installing Ubuntu (no graphical root login, no *gksudo nautilus* launcher icons).

That's funny - I just created a gksudo nautilus launcher for my panel yesterday, not having read this.

---

### Post by creaturex on 2006-11-29
Do you people read documentation? The root account is ***disabled by default***, this is a security issue because any script kiddie will guess the root username, but they can't guess your username so easily. There are simple ways to enable root if you want, and there are about 50 tutorials on it. Also, sudo -i or sudo -s -H makes it a root terminal. I agree with Ubuntu's decision to disable root by default, only invoking it's powers when necessary to prevent misuse.

---

