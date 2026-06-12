---
title: "Linux Viruses"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-08-04
SO I was reading an article on maximum pc's website the other day that stated not running virus software with Linux was like closing you're eyes while driving through an intersection with no traffic. Basically saying yeah it's harder to get infected with Linux but you still run the risk. What does everyone else think? Also, is it worth downloading and installing AVG Linux edition??? DIscuss!! :)

---

### Post by Brunellus on 2007-08-04
> **Tumpster said:**
> SO I was reading an article on maximum pc's website the other day that stated not running virus software with Linux was like closing you're eyes while driving through an intersection with no traffic. Basically saying yeah it's harder to get infected with Linux but you still run the risk. What does everyone else think? Also, is it worth downloading and installing AVG Linux edition??? DIscuss!! :)
**F**ear, **U**ncertainty, and **D**oubt.  

Proper user permissions takes care of most of your problems.  You are asking for trouble, however, if you routinely run as root, sudo unnecessarily, or install untrusted packages.  

Most Windows virus and crapware problems come from user error, not hacker malice.  Users are just conditionted mindlessly to click NIFTY.EXE, which carries a nasty payload.

---

### Post by Malibu Illusion on 2007-08-04
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by Tumpster on 2007-08-04
See, and thats my thought. I don't just install everything like most people do, I actually read through and try to figure out what something would do before I even touch it. It's my understanding, like everything else, that this should be the norm where it unfortunatly is not.

---

### Post by benx009 on 2007-08-04
> **Tumpster said:**
> SO I was reading an article on maximum pc's website the other day that stated not running virus software with Linux was like closing you're eyes while driving through an intersection with no traffic. Basically saying yeah it's harder to get infected with Linux but you still run the risk. What does everyone else think? Also, is it worth downloading and installing AVG Linux edition??? DIscuss!! :)

i had problems running AVG on linux in the past, so i'm not all too anxious to take it up now...

---

### Post by p_quarles on 2007-08-04
> **Tumpster said:**
> SO I was reading an article on maximum pc's website the other day that stated not running virus software with Linux was like closing you're eyes while driving through an intersection with no traffic. Basically saying yeah it's harder to get infected with Linux but you still run the risk. What does everyone else think? Also, is it worth downloading and installing AVG Linux edition??? DIscuss!! :)
I'd say the analogy is flawed. If my computer is a car, and the internet is an intersection, wouldn't the other cars be computers? Other computers and their users are, after all, the main security risk on Linux and any OS. 

A better analogy: running Linux with an anti-virus scanner is like getting yourself vaccinated against smallpox. There are no known Linux viruses in the wild. If there are unknown viruses, AVs wouldn't offer any protection.

---

### Post by Tumpster on 2007-08-04
Thats also my though as I wasn't going to go through the trouble of downloading and installing until I really hear a need for it. Of course I'm all for education before overacting I feel now after listening to everyone that the antivirus is not needed. Thanks to everyone!!

---

### Post by Nezing on 2007-08-04
As far as I understand it,you would have to be always logged in as **root **to infect your pc.Open Office,can "open files" written for MS Office,but unless you do something stupid....very very stupid....most people should be okey.

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by euler_fan on 2007-08-04
I think the following two points lend a small amount of reasonableness to running AV on a Linux machine.

1) You do lots of business with windows people. E.g. lots of file sharing, emailing versions of documents back and forth, etc. Say you don't always trust their intelligence about not running things or forwarding things they shouldn't. Then at least there is a shot that if they caught something and it went your way, while it shouldn't hurt you you may (a) find it (b) let them know about it, (c) not send it to someone else who does use windows and expects anything you send them to be clean.

2) Between ClamAV's hourly updates on busy days and how big a deal a wild Linux virus would be, while it is still a reactive measure against a virus that might exist for a while before we all caught onto its existence, at least once we did you would already have a system in place to provide additional assurance against your having it. It tends to be easier to plug a workable solution into a system already designed to handle it than build a new one from scratch (even as easy as it is to install ClamAV)

Like I said, small. There is certainly no reason to go for all of this "on access" and automated active monitoring stuff, but something about having that smallpox vaccine (ClamAV cron-job)  still makes me sleep a little better at night :)

---

### Post by p_quarles on 2007-08-04
I agree with #1 in the above message. It is courteous, in some circumstances, to scan files that you don't trust before sending them to Win users. If you're not running a mail server, though, this boils down to scanning individual files or directories. It's a courtesy, though, and not something that you do to protect yourself from harm, which the Maximum PC article was trying to claim.

I disagree on point #2, though. First, because ClamAV gives you a lot of false positives, and second I've heard that active virus scanners have been targeted in buffer overrun attacks on Linux systems. I'm definitely not an expert on this stuff, but my understanding from what I've read is that regular use of a virus scanner in Linux can actually cause more problems than it prevents (much in the same way that a smallpox inoculation carries more risk of negative reactions than it does of protecting you from a virus that exists only in a few highly-secure research facilities).

---

### Post by Paulmd on 2007-08-04
> **Tumpster said:**
> SO I was reading an article on maximum pc's website the other day that stated not running virus software with Linux was like closing you're eyes while driving through an intersection with no traffic. Basically saying yeah it's harder to get infected with Linux but you still run the risk. What does everyone else think? Also, is it worth downloading and installing AVG Linux edition??? DIscuss!! :)

There are a FEW linux viruses. Mostly obsolete.

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by bodhi.zazen on 2007-08-04
> **euler_fan said:**
> I think the following two points lend a small amount of reasonableness to running AV on a Linux machine.

1) You do lots of business with windows people. E.g. lots of file sharing, emailing versions of documents back and forth, etc. Say you don't always trust their intelligence about not running things or forwarding things they shouldn't. Then at least there is a shot that if they caught something and it went your way, while it shouldn't hurt you you may (a) find it (b) let them know about it, (c) not send it to someone else who does use windows and expects anything you send them to be clean.

I disagree. It is up to windows users to protect themselves. A properly set up Windows box is much better protected then you can offer with Linux antivirus and an improperly set up Windows box is not significantly improved with Linux antivirus.

There *may* be a role for antivirus if you are running a large mail server to windows clients.

> 2) Between ClamAV's hourly updates on busy days and how big a deal a wild Linux virus would be, while it is still a reactive measure against a virus that might exist for a while before we all caught onto its existence, at least once we did you would already have a system in place to provide additional assurance against your having it. It tends to be easier to plug a workable solution into a system already designed to handle it than build a new one from scratch (even as easy as it is to install ClamAV)

Like I said, small. There is certainly no reason to go for all of this "on access" and automated active monitoring stuff, but something about having that smallpox vaccine (ClamAV cron-job)  still makes me sleep a little better at night :)

No.

Linux != Windows.

As has been mentioned there are no significant know Linux viruses, so there is nothing to find. Antivirus can not protect against unknown viruses (Antivirus is reactive not proactive).

Don't forget that viruses take advantage of flaws or holes in the code. So the real solution is to update the code. So keep your box up to date, especially the security updates and you are better protected then any antivirus program can offer.

If you would like to learn about Ubuntu Security : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

he he he ...

I would say that taking advice on Linux security form an expert on Windows Security and applying it to Linux is "like closing you're eyes while driving through an intersection with no traffic."

---

### Post by euler_fan on 2007-08-04
> **bodhi.zazen said:**
> I disagree. It is up to windows users to protect themselves. A properly set up Windows box is much better protected then you can offer with Linux antivirus and an improperly set up Windows box is not significantly improved with Linux antivirus.

There *may* be a role for antivirus if you are running a large mail server to windows clients.



No.

Linux != Windows.

As has been mentioned there are no significant know Linux viruses, so there is nothing to find. Antivirus can not protect against unknown viruses (Antivirus is reactive not proactive).

Don't forget that viruses take advantage of flaws or holes in the code. So the real solution is to update the code. So keep your box up to date, especially the security updates and you are better protected then any antivirus program can offer.

If you would like to learn about Ubuntu Security : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Please allow me to explain myself:

I'm not trying to start a flame war here on this issue--I know it's touchy. I completely agree at at this time there is not benefit to the Linux user from AV with the possible exception you mentioned. And I completely agree that in insecure box is still insecure no matter what all the machines around it are running, that AV is reactive not proactive, it is the responsibility of the individual user to secure their machine, patches are critical, and the whole bit. Ergo, I offered it as a pair of _small_ reasons to run it.

If I might summarize this as simply as I can:

(1) I consider it polite to scan for viruses before passing on a file--more or less the source of my first reason
(2) I like and tend to advocate defense in depth--more or less the source of my second reason.

I simply consider it polite to have a small assurance that my machine is not a carrier of a disease it is immune to but can infect others with. I personally scan periodically (every two-three weeks) for this reason. I don't expect to find anything. If I did I would scan more frequently.

Perhaps I should have been more clear about this point: that is why I suggest use of something like ClamAV as a periodic cron job. I'm really not worried about it catching a threat to me, but something that might be passed through me to others. If that's not possible, I would be happy to examine the evidence and recant if necessary. I apologize if I was insufficiently explicit on this point.

In the interest of not posting flame bait beyond what I may already have done, I will leave my response to your response to my second position this way: I like defense in depth. Is it necessary? No. But I like it and I want to make sure that what amounts to a minority perspective is heard on this issue.

If defense in depth were a distraction from the major security priorities like patches, et al, then I would not mention it without a clear and explicit disclaimer. I don't think it is. If there is a consensus such a disclaimer is necessary, I am willing to listen to that position and make such a disclaimer--especially in the Absolute Beginner's Forum. IMHO it is merely worth mentioning that there are options for people who are either (1) a little paranoid or (2) agree with defense in depth.  I mean no disrespect to all the experts out there who say it isn't needed. I don't mean to spread FUD. I'm sorry if it came off that way.

---

### Post by bodhi.zazen on 2007-08-04
> **euler_fan said:**
> 

I simply consider it polite to have a small assurance that my machine is not a carrier of a disease it is immune to but can infect others with. I personally scan periodically (every two-three weeks) for this reason. I don't expect to find anything. If I did I would scan more frequently..

LOL, well said euler_fan.

---

### Post by euler_fan on 2007-08-05
> **bodhi.zazen said:**
> LOL, well said euler_fan.

Thank you. I mean that most sincerely.

---

