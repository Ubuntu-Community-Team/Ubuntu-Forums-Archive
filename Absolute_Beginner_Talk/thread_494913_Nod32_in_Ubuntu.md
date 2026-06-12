---
title: "Nod32 in Ubuntu"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-07-07
Can I use Nod32 in Ubuntu.
If so, what version do I dowload and how do I install it. I am using the 30-day trial Nod32 download in Windows on the same lappie.
Thanks

---

### Post by kosmic on 2007-07-07
Hi in a *nix OS like (ubuntu) you don't need antivirus and anti-spyware that is bullsh*t from Windows world ;)

---

### Post by AlexenderReez on 2007-07-07
but if you still need to cover your window system....use avg or avast or any other anti-virus(which availabe for linux)....it is seems that in official Nod32 website doesn't provide linux version :(

---

### Post by mlentink on 2007-07-07
You don't need it. 
If you want to protect Windows-users you might consider ClamAV

---

### Post by urvaksh on 2007-07-07
Thanks all,
I can't seem to install ClamAV. It says I need to install it through the root. (yes, i'm a damn newbie)
I've intsall Avast. But it keeps tellinng me I have trojan downloaders in my pagefile.sys folder. I logged into Windows and scanned the computer repeatedly with Nod32, Ad Aware, Spyware Doctor and Spybot. They all came up clean.
That's why I was trying to scan in Linux using some other AV to see if I got the same trojan downloader alerts.

---

### Post by por100pre1 on 2007-07-07
You usually don't need antivirus in Linux client but you can use avast! for Linux for on demand scanning. It has a decent GUI and it's easy to use.

EDIT: Try F-Prot for Linux with [XFPROT debian package]("http://web.tiscali.it/sharp/xfprot/").

---

### Post by kosmic on 2007-07-07
You need to run it as root user in a terminal just do

sudo clamav


and it should work

---

### Post by deepclutch on 2007-07-07
I think below articles are useful:
**[[B]Note to new Linux** users: No antivirus needed]("http://www.linux.com/articles/60208")[/B]

**[[B]Linux is NOT Windows**]("http://linux.oneandoneis2.org/LNW.htm")[/B]

and worms only exists for Linux(arguably)

---

### Post by urvaksh on 2007-07-07
I typed sudo clamav in the terminal and it said command not found

---

### Post by odiseo77 on 2007-07-07
> **urvaksh said:**
> I typed sudo clamav in the terminal and it said command not found

try ***sudo apt-get install clamav***. When prompted for a password, enter your user password. :)

---

### Post by urvaksh on 2007-07-07
I did that and it's installed. Now how do I run clamav

---

### Post by urvaksh on 2007-07-07
I ran the command in terminal and clamav is installed. Now how do I run the clamav scan?
Thanks

---

### Post by odiseo77 on 2007-07-07
the command to run clamav is ***clamscan***, if I'm not wrong... haven't used it in months, so I don't remember which are the options to run it, so you'll have to type *clamscan --help* (sorry, I'm not on linux atm).

---

### Post by urvaksh on 2007-07-07
Thanks, odisseo 
Also, the only way to scan using ClamAV is thru the terminal? Or can I do it via the GUI?

---

### Post by cprofitt on 2007-07-07
There is no client Linux version of Nod32 at this time... if you are running a mail server they do have one.

As for not needing avirus scanner -- you always do, but do to penetration Linux is far less likely to be a target so you are more safe without one.

---

### Post by deepclutch on 2007-07-07
> **PrivateVoid said:**
> There is no client Linux version of Nod32 at this time... if you are running a mail server they do have one.

As for not needing avirus scanner -- you always do, but do to penetration Linux is far less likely to be a target so you are more safe without one.
Linux AVs are actually for windows virus checking!
and Linux viruses(worms actually!) wont increase with increase in userbase.that is a FUD propagated bt\y AV companies esp Kasprsky.
and do read:
[http://linuxmafia.com/~rick/faq/index.php?page=virus]("http://linuxmafia.com/%7Erick/faq/index.php?page=virus")
> **Should I get                  anti-virus software for my Linux box?**                  The problem with answering this question is that                 those asking it know *only* OSes where                 viruses, trojan-horse programs, worms, nasty                 Javascripts, ActiveX controls with destructive                 payloads, and ordinary misbehaved applications are                 a constant threat to their computing. Therefore,                 they *refuse to believe* Linux could be                 different, no matter what they hear.
                  And yet it is.
                  Here's the short version of the answer: No. If you                 simply *never run untrusted executables while                 logged in as the root user (or equivalent)*,                 all the "virus checkers" in the world will be at                 best superfluous; at worst, downright harmful.                 "Hostile" executables (including viruses) are                 *almost unfindable* in the Linux world &#8212;                 and no real threat to it &#8212; because they lack                 root-user authority, and because Linux admins are                 seldom stupid enough to run untrusted executables                 as root, *and* because Linux users' sources                 for privileged executables enjoy paranoid-grade                 scrutiny (such that any unauthorised changes would                 be detected and remedied).
                  Here's the long version: *Still* no. Any                 program on a Linux box, viruses included, can only                 do what the user who ran it can do. Real users                 aren't allowed to hurt the system (only the root                 user can), so neither can programs they run.
                  Because of the distinction between privileged                 (root-run) processes and user-owned processes, a                 "hostile" executable that a non-root user receives                 (or creates) and then executes (runs) cannot                 "infect" or otherwise manipulate the system as a                 whole. Just as you can delete only your own files                 (i.e., those you have "write" permission to),                 executables you run cannot affect other users' (or                 root's) files. Therefore, although you can create                 (or retrieve), and then run, a virus, worm, trojan                 horse, etc., *it can't do much*. Unless you                 do so as "root". Which it's simple to avoid                 doing.
                  

---

### Post by ajgreeny on 2007-07-07
If you want a gui try clamtk or klamav, both in the repos.

---

