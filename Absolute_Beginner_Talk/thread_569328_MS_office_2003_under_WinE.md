---
title: "MS office 2003 under WinE"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by xprinceps on 2007-10-06
I am on my dozenth or so attempt to get MS office running under WinE. I was getting the now-infamous "not installed for this user" error, so I uninstalled everything. Several people on the forum suggested downgrading WinE, so I did this too (from 0.9.46 to 0.9.33). I also installed ies4linux, since many people suggested this would help. Now when I try to install Office, I get as far as "Writing system registry values" before the installer quits with the (not very helpful) error message "Installation ended prematurely because of an error." 
("Because of an error." Really? Can you be a little less specific?) :-s
If anyone has advice on solving this problem, I would really appreciate hearing it. I will drop the $40 on crossover office if I have to, but I'd rather not.

Note to purists: I see many inquiries similar to this one answered with something like "don't use Office". Maybe in the future I will move over to OO, but right now I need 100% compatibility, so my options are to get this fixed, to run Office in Windows, or to quit grad school. I am all for fighting the good fight, but my advisor uses Word, so for the time being I have to use Word.

---

### Post by ryanVickers on 2007-10-06
You know, OO can open and save office formats...

---

### Post by ~chinook~ on 2007-10-06
OO can save pretty much any format. I really don't get. You can save all the way down to word 97 compatibility.

---

### Post by PmDematagoda on 2007-10-06
If you want to use Office 2003 you have to use something similar to Wine called Crossover Office. The thing is that it is not free and I've also heard that MS Office 2003 is supported but only barely, which means that you will have to expect problems while using it.

You can try Office 2003 using Wine as well but you will have to do a lot of configuring and changing the core of Wine to fit the necessities of Office 2003.

---

### Post by ryanVickers on 2007-10-06
Yeah, you could use:
-wine
-crossover
-VirtualBox (run windows as a VM)
at least one of those always works for me ;)

---

### Post by Frak on 2007-10-06
Office 2007 runs under Wine, but only very barely, and that only until it tries to start up.

2003 runs under Crossover Office just fine exept Outlook. But Evolution is supposed to be a complete drop-in replacement for it.

---

### Post by xprinceps on 2007-10-06
Okay, I guess my post had too many tangents. The problem I am trying to solve is that I can't get Office 2003 running in WinE. The solution I'm looking for is one that gets Office 2003 running in WinE. 
Please don't take this to be unappreciative; I love that people take time to help out newbies like me. That said, OO is NOT 100% compatible with MS Office. When I open Word docs in OO, it often fails to keep the same formatting, slaughters field codes, and completely ignores citations from my reference management software. When I am sending endless versions of a manuscript back and forth to my advisor (who uses Word) I can't have this. I'm not looking to get into a discussion about the merits of OO vs MS. What I'm trying to do is get Office running in Ubuntu, which would allow me to quit booting into Windows, a big step toward eventual Microsoftlessness. :D
I would like to keep crossover office as a last resort. I know that other people have gotten Office to run under WinE, and that is what I would like to do. If anyone has advice on _how to get Office running in WinE_, I would love to hear it.
Thanks for the help.

---

### Post by MrFSL on 2007-10-06
> If anyone has advice on how to get Office running in WinE, I would love to hear it.

Well put.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214)

From the linked page:
> imply install with Wine 0.9.46. When you launch any program, it will say that the program isn't installed for the current user. Don't panic. Remove Wine ("sudo aptitude remove wine" for me). Install Wine 0.9.37. Launch any program. It will work. Now update your Wine version to 0.9.46, relaunch the programs, and.... Magic! It works. Simply PowerPoint is slow, and I've not tested Excel very much, but it seems to work!!

Cheers!

P.S. I haven't tried this myself.

---

### Post by perce on 2007-10-07
You can try this: 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2735](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2735)

or this:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

which is not free, neither as freedom, nor as beer. I have no experience with either, so I don't know how they work.

In an ideal world the solution would be to switch your advisor to LaTeX, but I know it's impossible.

---

### Post by trippinnik on 2007-10-07
You could try this as well.  Sorry it's not Office 2003 in Wine, but i've read that the Office compatibility is 100%.

---

### Post by ryanVickers on 2007-10-07
Try what as well? :p

---

### Post by VinylPusher on 2007-10-28
I switched to Ubuntu because I thought Office compatability was quite good. I'm an amateur Excel developer and I need to be able to use Excel 2003 for work.

Am I going to have to use a VM to get it working?

---

### Post by Frak on 2007-10-28
Use Crossover, runs fine.

---

