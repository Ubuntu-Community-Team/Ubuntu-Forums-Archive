---
title: "How can I tell if my Linux Box is hacked?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2007-09-17
I believe the question is clear enough.

Are there any tell-tale signs that our computers with Ubuntu OS may be hacked/Phished/whatever?

How can you tell if somebody is hacking you? What are the "symptoms"?

---

### Post by CaptainInsaneO on 2007-09-17
I'd imagine they'd be pretty much the same symptons you'd see on any other OS:

Your user password gets changed.
Other usernames/logins mysteriously appear.
File names get changed.
Files (especially personal or config) are deleted, moved, or copied.

Believe it or not, unlike the movies you won't see your cursor moving around the screen if someone has remoted into your machine. You can usually find out if someone has "hacked" (I hate using that word in a derogatory fashion) **cracked** into your machine by paying attention to your files and logs.

---

### Post by bodhi.zazen on 2007-09-17
See if this thread helps, see the section on intrusion detection :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?&t=510812)

---

### Post by SpiritIsReality on 2007-09-17
howdy
wow, good one, thanks

trails

---

### Post by asmoore82 on 2007-09-17
if a rootkit has been installed to hide intruder activity;
the cmd line apps that show processes such as 'top' and 'ps' may be shell scripts
instead of binary programs; and the hijacked scripts may not be in the right places ...

```
**asmoore@asmoore-laptop:~$** which top
/usr/bin/top
**asmoore@asmoore-laptop:~$** which ps
/bin/ps
**asmoore@asmoore-laptop:~$** file $(which top) $(which ps)
/usr/bin/top: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped
/bin/ps:      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped
**asmoore@asmoore-laptop:~$** type top
top is /usr/bin/top
```

... a long time ago when I ran Red Hat 7, I foolishly logged in to my box
from a lab computer at school over ***unencrypted* ftp as *root***.
the next day when I noticed my system was running slower than usual, I tried a 'ps -A'
and got an error message something like
"bash: ps: syntax error at line 22."
then a 'file /bin/ps' showed
/bin/ps: Bourne Again Shell script text executable.
I had caught someone in the middle of unpacking and setting up a crappy rootkit.

"Pull Eth0 Plug" -> Format -> "NEVER log in remotely unless using SSH Protocol 2"

---

### Post by irish_flu on 2007-09-17
> **gyalakias said:**
> I believe the question is clear enough.

Are there any tell-tale signs that our computers with Ubuntu OS may be hacked/Phished/whatever?

How can you tell if somebody is hacking you? What are the "symptoms"?

It might be easier to ask, what makes you think this is going on?

Also: Just for some friendly clarity, 'hacked' and 'phished' are completely different, and 'phished' happens to people, not computers.

In a (barely coherent) nutshell, for this thead's purposes anyway:
-"hacked" means somebody either controls your computer, or has somehow manipulated the data on it.

-" phished" is when a person is tricked into doing something; maybe an email says "change your bank acct password", maybe you click on a link at myspace and it sends you to a page that looks like the myspace login, etc.

---

### Post by HermanAB on 2007-09-18
If you type 'who' and there is someone else logged in, then you know!
:)

H.

---

### Post by gyalakias on 2007-09-19
My computer actually runs great, but I am a bit paranoid about security. Also, my internet connection goes slow at some times in the day, which makes me wonder...

---

### Post by PmDematagoda on 2007-09-19
> **gyalakias said:**
> My computer actually runs great, but I am a bit paranoid about security. Also, my internet connection goes slow at some times in the day, which makes me wonder...

It could be your ISP reducing download speeds for maintenance or due to a very high volume, I know it happened to my ISP, it reduced to 10Kb/s from 50Kb/s during the day time but got fixed during the night time.

---

### Post by lisati on 2007-09-19
> **PmDematagoda said:**
> It could be your ISP reducing download speeds for maintenance or due to a very high volume, I know it happened to my ISP, it reduced to 10Kb/s from 50Kb/s during the day time but got fixed during the night time.

As well as ISPs getting busy certain times of the day (especially when you'd expect busisnesses to be open and other times when you'd expect lots of users to be online), some ISPs also slow down connections after you've used a certain amount of bandwith each month.

---

### Post by PmDematagoda on 2007-09-19
> **lisati said:**
> As well as ISPs getting busy certain times of the day (especially when you'd expect busisnesses to be open and other times when you'd expect lots of users to be online), some ISPs also slow down connections after you've used a certain amount of bandwith each month.

Actually my ISP is so heartless that it allowed me to keep on downloading at the normal rate even after I went over my limit, this obviously caused a very big bill.;)

---

### Post by gfixler on 2007-10-02
> **CaptainInsaneO said:**
> Believe it or not, unlike the movies you won't see your cursor moving around the screen if someone has remoted into your machine.

Believe it or not, that was *exactly* what happened on my machine, through an exploit I didn't know of in RealVNC on Windows XP. Scared the crap out of me. Once I realized what I was seeing, I had to fight the guy. He wanted to go up to "My Computer," I desperately wanted to get down to the VNC shelf button to disable it. I'd never felt so exposed. The logs showed that he'd been logging in for a few seconds/minutes here and there (probably managing spam scripts) for over 3 months, right under my nose. I never noticed, as I was usually at work when he did it.

That was the absolute last straw. I'd had it. I switched to Ubuntu, and never looked back.

---

### Post by Circus-Killer on 2007-10-02
> **gfixler said:**
> Believe it or not, that was *exactly* what happened on my machine, through an exploit I didn't know of in RealVNC on Windows XP. Scared the crap out of me. Once I realized what I was seeing, I had to fight the guy. He wanted to go up to "My Computer," I desperately wanted to get down to the VNC shelf button to disable it. I'd never felt so exposed. The logs showed that he'd been logging in for a few seconds/minutes here and there (probably managing spam scripts) for over 3 months, right under my nose. I never noticed, as I was usually at work when he did it.

That was the absolute last straw. I'd had it. I switched to Ubuntu, and never looked back.

yeah, its true. you can do pretty much anything depending on how mcuh access said "virus/trojan" allows. a perfect example of this is symantec's pc anywhere, with which you can control the entire pc, including the mouse! its as if you were sitting right in front of the windows box, clicking away. now i know pc anywhere is not a virus/trojan, but thats only because its installed by choice. theres no reason why another program with the same functions cant be written, but install and infect machines without users knowledge.

so yeah, the statement about virus's not being like in the movies, thats onyl partially true. it is true that 99.999% of the virus's out the dont do it, they rather focus on shutting down networks, servers and individual machines, as apposed to gaining control.

(most virus's writers choose not to affect things like control over mouse pointers because it makes the user immeditiatly aware for the infection. thus making the virus do everything in the background where the user cant see is the general method for destruction)

---

