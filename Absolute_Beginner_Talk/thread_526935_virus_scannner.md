---
title: "virus scannner"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by watai on 2007-08-16
i'm wondering just now about virus scanner in ubuntu..so any virus scanner in this cute OS?

---

### Post by mikewhatever on 2007-08-16
There is no virus scanner preinstalled. If you'd like one, use one of the following guides
[http://ubuntuforums.org/showthread.php?t=30060](http://ubuntuforums.org/showthread.php?t=30060)
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)
[http://www.ubuntugeek.com/tag/avast-antivirus-ubuntu/](http://www.ubuntugeek.com/tag/avast-antivirus-ubuntu/)
This said, you do not need an anti-virus on Ubutnu
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by hyper_ch on 2007-08-16
Why would you want a virus scanner that only uses precious system resources, hogs down your system and doesn't really do anything on Linux?

---

### Post by Samuel E.Krewing on 2007-08-16
> **watai said:**
> i'm wondering just now about virus scanner in ubuntu..so any virus scanner in this cute OS?
I am, as probably You too, very cautious about viruses, no matter if the are any, YET. But the cooperation with Gates brings viruses, and that's a fact(see Mac...).

As I had used SimplyMEPIS-Linux, I used Klamav, and was very pleased about that. But, when there came some problems updating that scanner, I changed to Ubuntu 7.04 AMD64, and found the same scanner updated. You will too, using Synaptic; find: "clamav". Install that, and You will be even more secured. You probably don't need Klamav(with "k"), but it makes no harm at all.

Samuel

---

### Post by gn2 on 2007-08-16
> **watai said:**
> i'm wondering just now about virus scanner in ubuntu..so any virus scanner in this cute OS?

Relax, breathe deeply and repeat after me:

"Linux isn't Windows"
"I do not need anti-virus"

"Linux isn't Windows"
"I do not need anti-virus"

"Linux isn't Windows"
"I do not need anti-virus"

"Linux isn't Windows"
"I do not need anti-virus"

"Linux isn't Windows"
"I do not need anti-virus"

Ahhh that's better :)

---

### Post by Samuel E.Krewing on 2007-08-16
Do you really think your mantras help watai?

Why don't you let him search and install clamav? It makes no harm at all.
It's just too childish to rely 100% on OS, that does cooperation with the one we both hate.

Get real, and let watai install clamav.

---

### Post by proalan on 2007-08-16
Well its up to him whether he wants to install it or not. 

My only advice is for him to do some research and decide for himself. There are many threads about this subject in the forums, do a search. 
I'm in agreement with not needing antivirus myself, its redundant and wastes resources on my rig. But perhaps he has a network configuration with windows based technology in the loop in which case it might be useful.

---

### Post by Samuel E.Krewing on 2007-08-16
If he asks it he wants it. Simple as that.

It makes no harm at all, and after the scanner is installed, it is more secure to do the research you suggested.
After all that above is done, it's easy to uninstall clamav, IF he wants.

Watai, you've gotten many answers, and you are free to make your decision about them. I suggested the scanner you asked, but in case it's not good, don't install it for a try.

---

### Post by gn2 on 2007-08-16
> **Samuel E.Krewing said:**
> 
Why don't you let him search and install clamav? It makes no harm at all.


I'm not stopping him, just expressing the opinion that it is not required.

Windows PC's should look out for themselves.

---

### Post by Samuel E.Krewing on 2007-08-16
There must be a failure in our communication.
Have you not seen, how even Macintosh got a virus-boost as soon as it began cooperation with windows?
Windows does cooperation with Linux, so let me put the topic again;
is Linux more secure than Macintosh? 
The answer might be:"For a while", maybe, but how long?

Do not trust in "100% secure", as long as they're both manufactured by humen.

---

### Post by euler_fan on 2007-08-16
> **Samuel E.Krewing said:**
> There must be a failure in our communication.
Have you not seen, how even Macintosh got a virus-boost as soon as it began cooperation with windows?
Windows does cooperation with Linux, so let me put the topic again;
is Linux more secure than Macintosh? 
The answer might be:"For a while", maybe, but how long?

Do not trust in "100% secure", as soon as they're both manufactured by humen.

Thing is that even if the first part is true AV is still a reactive measure. It won't catch anything until it's too late. Moreover, by the time it would be caught, a rootkit could have already changed how it works. So even AV is not going to finish making you safe.

I still agree it has a place as part of a layered security system. Not everyone does. I use ClamAV as a late night cron job along with rkhunter, chkrootkit, OSSEC-HIDS, and IPTables. If I was running a server Fail2Ban or DenyHosts and SNORT would be on the list too. Next time I reinstall I'll probably be running AIDE too. But I'm also a pretty paranoid desktop user. I have some network statistics displayed as part of Conky (rate up, rate down, total up, total down) since unless a rootkit or worm that gets on my machine decides to fake all of my traffic totals and rates I'll suddenly see my volume of transmitted data spike when the bot on my machine starts sending spam. I go use SHIELDS UP! periodically to see how I look to a port scanner. . . Like I said, paranoid :)

Incidentally, I don't expect to find anything and if I suspected I had something then I would boot Backtrack or Knoppix as a live CD and do all the forensics that way.

Just being aware of your machine, how it works, and what's going on with it are 10x more valuable than AV IMHO. That's why I run alot of that stuff: it helps me keep and eye on what's happening. 

If it hasn't been suggested yet, [this]("http://ubuntuforums.org/showthread.php?t=510812") is a great guide to security in Ubuntu.

---

### Post by hyper_ch on 2007-08-16
[QUOTE=Samuel E.Krewing;3198445]If he asks it he wants it. Simple as that.[QUOTE]

Actually it's not as simple as that ;)
He thinks he must have an AV because that's his experience with Windows... on Windows you must have one or not be connected to the internet... however this is not Windows here and hence it's not as simple as that ;)

People want something because they have an opinion towards it. However if the base alters of what the opinion is based onto, then they may not want that any longer ;)

---

### Post by Samuel E.Krewing on 2007-08-16
> **hyper_ch said:**
> [QUOTE=Samuel E.Krewing;3198445]If he asks it he wants it. Simple as that.[QUOTE]

Actually it's not as simple as that ;)
He thinks he must have an AV because that's his experience with Windows... on Windows you must have one or not be connected to the internet... however this is not Windows here and hence it's not as simple as that ;)

People want something because they have an opinion towards it. However if the base alters of what the opinion is based onto, then they may not want that any longer ;)

Playing smart guy, huh? 

But IF you know why:"He thinks he must have an AV because that's his experience with Windows.." you either have talked wit watai, or you are overestimating your abilities. Don't be shy about that. So do many others, who have covered their eyes.

---

### Post by philinux on 2007-08-16
> **Samuel E.Krewing said:**
> There must be a failure in our communication.
Have you not seen, how even Macintosh got a virus-boost as soon as it began cooperation with windows?
Windows does cooperation with Linux, so let me put the topic again;
is Linux more secure than Macintosh? 
The answer might be:"For a while", maybe, but how long?

Do not trust in "100% secure", as long as they're both manufactured by humen.

Hi, I hear you loud and clear. I have a dual boot with win ME and I'm mostly using linux 100%. some of my files are on my old hard drive though and just to be safe I'd thought about virus software.

Installed avg but its a bit clunk in linux. So does clamav have a gui for the front end or is it cli.

---

### Post by euler_fan on 2007-08-16
> **philinux said:**
> 
Installed avg but its a bit clunk in linux. So does clamav have a gui for the front end or is it cli.

There is ClamTK, but last time I used it I found it clunky. Honestly, once the clamd.conf file is editted (not hard, man pages are very good) you can either run clamscan or clamdscan from the command line very easily. I use it command line and also as a cron job. There are some good howtos here on the forums.

Not sure about a front end for KDE.

---

### Post by hyper_ch on 2007-08-16
> **Samuel E.Krewing said:**
> you either have talked wit watai, or you are overestimating your abilities.

Or I may just make a well-educated guess with regard of my experience from windows users converting to linux and countless topics like that in this forum ;)

---

### Post by Samuel E.Krewing on 2007-08-17
> **hyper_ch said:**
> Or I may just make a well-educated guess with regard of my experience from windows users converting to linux and countless topics like that in this forum ;)
Are you just an ivory tower intelligent? step down.. there are real people down here, you see.

---

### Post by hyper_ch on 2007-08-17
Samuel

well, I use my brains to think ;) ever tried that?

Anyway, this is a beginners forum and most of them come from windows, hence they are all brainwashed that AV, firewalls, anti-spyware, ... is really necessary....

Once you've spent a few month in this forum you'll notice that 99% of the people asking about AV come from windows and have that brainwashed thinking... on windows it's a must... here it's not and it's hard for them to comprehend as they may not know otherwise.

So basically you need to ask them frist what they want an AV for... once you get the answer you can say none is needed or this or that will do the job ;)

---

### Post by Samuel E.Krewing on 2007-08-17
> **hyper_ch said:**
> Samuel

well, I use my brains to think ;) ever tried that?
Oh, I've tried, but since there are a lot more than just a self-sufficient ivory-towerist is able to think, I suggest you to see a bit more than you first think.
> **hyper_ch said:**
> 
Anyway, this is a beginners forum and most of them come from windows, hence they are all brainwashed that AV, firewalls, anti-spyware, ... is really necessary...

Once you've spent a few month in this forum you'll notice that 99% of the people asking about AV come from windows and have that brainwashed thinking... on windows it's a must... here it's not and it's hard for them to comprehend as they may not know otherwise.
Is Linux more secure than Macintosh? Mac is not windows, at least not yet, but it has a commercial virus protection... so, is it too hard for you to realize, what cooperation with windows did to Macintosh? ..or what are you trying?
> **hyper_ch said:**
> 
So basically you need to ask them frist what they want an AV for... once you get the answer you can say none is needed or this or that will do the job ;)
Oh! So you did ask watai that? If so, that's good. Otherwise...

---

### Post by hyper_ch on 2007-08-17
what does a mac a virus scanner need for? Because there are commercial applications it still doesn't mean they are necessary ;)

But since you are so convinced that a virus scanner is needed for linux, please point out a few viruses for me that can havoc a Ubuntu 6.x or later?

And besides, keep this forum friendly ;)

---

### Post by mikex on 2007-08-17
> **hyper_ch said:**
> what does a mac a virus scanner need for? Because there are commercial applications it still doesn't mean they are necessary ;)

But since you are so convinced that a virus scanner is needed for linux, please point out a few viruses for me that can havoc a Ubuntu 6.x or later?

And besides, keep this forum friendly ;)

I work for a major Aerospace company, and they require a virus scanner on our linux systems. Can you explain why viruses are not a threat to linux systems. If they aren't, I just want to understand why that's all. Why can't a person write a virus to infect linux, what is there preventing a virus without an anti-virus program. Not trying to be argumentative, I really don't understand.

---

### Post by Nekiruhs on 2007-08-17
> **Samuel E.Krewing said:**
> Do you really think your mantras help watai?

Why don't you let him search and install clamav? It makes no harm at all.
It's just too childish to rely 100% on OS, that does cooperation with the one we both hate.

Get real, and let watai install clamav.
Canonical, the company that makes Ubuntu, is not cooperating with MS. Where are you getting your news?

---

### Post by Hopeless on 2007-08-17
AVG Free linux...

or try typing in google free online scanner...

bitdefender or trend micro is good and needs no install but some java...

HTH... :popcorn:

---

### Post by Samuel E.Krewing on 2007-08-17
> **hyper_ch said:**
> what does a mac a virus scanner need for? Because there are commercial applications it still doesn't mean they are necessary ;)
Still looking at the world through one eye? That situation, you described, might be for right now, but what about tomorrow? Or day after, and after..?

Before AIDS, were there enough protection?

> **hyper_ch said:**
> 
But since you are so convinced that a virus scanner is needed for linux, please point out a few viruses for me that can havoc a Ubuntu 6.x or later?
Clamav virus-list marked 10 viruses that would be a threat to Linux. I've got too less money to hazzle with even one virus anymore. Please, open your both eyes! I'll post you a list as soon as I've got them neatly. Right now I'm downloading Mint Linux.

> **hyper_ch said:**
> 
And besides, keep this forum friendly ;)
Look who's talking... before you accuse me, take a look at your self. I don't use smiles to fool anybody.

---

### Post by hyper_ch on 2007-08-17
> **mikex said:**
> I work for a major Aerospace company, and they require a virus scanner on our linux systems. Can you explain why viruses are not a threat to linux systems. If they aren't, I just want to understand why that's all. Why can't a person write a virus to infect linux, what is there preventing a virus without an anti-virus program. Not trying to be argumentative, I really don't understand.

The nature of linux is totally different than the one from windows... to get some basic idea have a read here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

What is the virus scanner on your linux systems used for? The main reason to use AV on linux is to clean out windows viruses from emails and files that are shared or distributed...

And of course one has to add, that a AV is rather retro-active and pro-active. I can, with some exceptions, only recognize known viruses. here comes again open source into place. Once a virus is being discovered it will take only  a couple of hours or a few days until there's a fix available. On windows however you will have to wait until Redmond sees it fit to release a fix - but for most viruses Redmond does not release a fix at all...

> **Samuel E.Krewing said:**
> Still looking at the world through one eye? That situation, you described, might be for right now, but what about tomorrow? Or day after, and after..?
Well, as the nature of windows, mac and linux are totally different you cannot use the same assumptions there ;) Have a look at what I have written above.

> **Samuel E.Krewing said:**
> Clamav virus-list marked 10 viruses that would be a threat to Linux. 
You have to be more specific than "a threat to linux". Linux is actually the kernel so you say those 10 viruses are a threat to the most recent linux kernel?

> **Samuel E.Krewing said:**
> Look who's talking... before you accuse me, take a look at your self. I don't use smiles to fool anybody.
Well, your use of language makes it imperative to use such smileys ;)

---

