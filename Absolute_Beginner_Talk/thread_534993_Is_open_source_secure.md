---
title: "Is open source secure?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by dr_pressure on 2007-08-25
Just wondering...

Theoretically speaking, how likely is it that someone could hi-jack the backports repo.

What I mean by that is, someone volunteers to compile a program for the backports, they insert a hidden logic bomb or backdoor, upload the binary to the backports, and suddenly they own a substantial number of ubuntu boxes.

I know that I could always use the repos which have been reviewed by the ubuntu security team, but there is a lot of software which I absolutely can't live without which is not reviewed by them. For example, if I'm not mistaken, VLC media player.

Are these concerns justified?

---

### Post by nonewmsgs on 2007-08-25
it is much safer then trying to download software in the wild internet for windows.

AFAIK before it goes into any of the major repos, it's checked.

---

### Post by Dark Star on 2007-08-25
LMA starnge ques.. Look when I was usin WIndwos I installed every AV and Firewall at interval but still I got caught by Malicious s/w but now am free , am open cause no Virus threat here in Linux :D so happy and free open txing :D

---

### Post by SeanBlader on 2007-08-26
Target audience, and lowest common denominator. These are what makes windows the most vulnerable. 

Say you're a black hat hacker, and you want to make a big name for yourself and become world renown as the guy who brought down millions of computers around the world. Well you can't get there by trying to hack Linux, there just aren't millions of Linux boxes. And you can't go hacking Solaris, or the Mac, it really won't get you anywhere. Sure if you hack the Mac you'll infect a few graphic artists computers and maybe some video editors, schools and the occasional home computer, but you won't be renown, you'll be a dork. Now technically you might have done something very impressive, but all your hacker friends won't be too impressed.

Now you create a virus or worm with a gestation time of a few months, you get it onto a few systems and let it propagate itself and very shortly you've shut down the NYSE and NASDAQ, along with all of Bank of America's new ATM's and teller machines and who knows how many tens of thousands of company networks. Now you're renown, infamous if you will.

The problem with being a black hat hacker is there are a great number of people who's professional reputation, jobs, families and livelihoods all depend on them beating you. Then there are the former black hats who've decided to become productive. They are all programming Linux machines now if they're not working a security job somewhere.

So while open source may not inherently be secure, look how many security patches Mozilla puts out, it is inherently less targeted than Microsoft, since it's less prolific and less hated. If you're a Black hat hacker, are you going to look the gift horse in the mouth and attack linux? Maybe if you're a Microsoft zealot and don't care what other hackers think of you, but mostly people who are hackers would respect everyone that writes code for linux, and may also be some of the programmers who contribute to the cause ironically enough.

So when compared to Microsoft, basically open source is more secure, by reputation alone.

---

### Post by dr_pressure on 2007-08-26
I certainly agree that the problem is worse in Windows due to a larger target audience and various other factors...

Even so, it's not hard to imagine someone being motivated to target the Ubuntu boxes.



Actually the reason I was asking is because I'm about to set up a Ubuntu server. So far, I think I'm going stick to only the repos which are reviewed by the security team.

For desktop I'm not storing any highly sensitive information there anyway so I'll continue using the backports.

---

### Post by Paulmd on 2007-08-26
> **dr_pressure said:**
> Just wondering...

Theoretically speaking, how likely is it that someone could hi-jack the backports repo.

What I mean by that is, someone volunteers to compile a program for the backports, they insert a hidden logic bomb or backdoor, upload the binary to the backports, and suddenly they own a substantial number of ubuntu boxes.

I know that I could always use the repos which have been reviewed by the ubuntu security team, but there is a lot of software which I absolutely can't live without which is not reviewed by them. For example, if I'm not mistaken, VLC media player.

Are these concerns justified?

I think it is a reasonable concern. I think it unlikely, but not impossible that someone could do something like that. There would be a number of obstacles, though.

It would have to be a program that is desirable enough that a substantial number or people would download it,  and yet not so popular that it would already be in the repo. 

The change would have to be subtle, and the attack probably substantially time delayed.  It would do no good (well bad :) ) if one of the first victims to install it, has their firewall immediately complain about the program calling home. The minute that happens, the program would be removed from the repository, when people start calling Canonical.  

The change would also have to avoid breaking the functionality, so people don't just uninstall the program because it doesn't work right.  And to avoid rousing the suspicions of the repository maintainers.

It would also have to be something that could get tens or hundreds of thousands of downloads, to compromise a significant number of weakly protected systems. Such as those without an active firewall.

It would also have to be something that is infrequently updated, or it won't be long before someone uploads a new version.


Another possible vector could be a rogue repository. There would have to be some form of  social engineering to get people to add it to their sources.list.  It might be accomplished via spam, or a version of stealth spam, masquerading as a response to a question. Virtually every email virus uses social engineering as a means of getting people to open, and run an attachment. Social engineering attacks work on the principle, that while individually, a person is smart, people are dumb. Or a big enough percentage of them are dumb enough for an attacker to damage a large number of systems.

It could be something a lot of people want, but can't get for free. To get people who are desperate enough to let down their guard. How does "Looking for the full version of Conexant HCF modem driver",  complete with  a bogus reply "There is a .deb at Hxxp://someboguswebsite.net"  Does that sound nefarious enough? Easier to do on Usenet, than a moderated forum like this, though.



A third possible vector would be a disgruntled employee. Almost every largish company has some. It would be naive to assume that Canonical doesn't have any. They can sometimes do a lot of damage, before they leave.



While it shouldn't keep you awake at night, it is nonetheless a reasonable concern.

---

### Post by Magneticgravity on 2007-08-26
More secure than Windows anyway...

---

### Post by az on 2007-08-26
Not just anybody can upload to the repos (even backports).   And all packages are uploaded in source form and compiled by the autobuilders.

So, while the backports repos is probably a lot less popular, it is certainly a lot more secure than installing binary packages from third-party sources.  

> **SeanBlader said:**
> 

So while open source may not inherently be secure, look how many security patches Mozilla puts out, it is inherently less targeted than Microsoft, since it's less prolific and less hated. ...

So when compared to Microsoft, basically open source is more secure, by reputation alone.

That's wrong.  Binary-only software is way more vulnerable than source-based software simply because you can exploit a stable ABI a lot more easily than one that changes so often.  Linux is not more secure because it is less popular, it is a lot more secure because it is built differently.

Open source software is inherently *more* secure than closed-source.  The "security-by-obscurity" principle has been proven wrong.  It is far more helpful to have a security system running on transparent code than closed code - you end up with better code.  

Just because you know how the lock works does not necessarily  make it easier to pick.  Like encryption, just because you know the method of encryption does not make it easier to crack the key.  

> **Paulmd said:**
> 
The change would have to be subtle, and the attack probably substantially time delayed.  It would do no good (well bad :) ) if one of the first victims to install it, has their firewall immediately complain about the program calling home. The minute that happens, the program would be removed from the repository, when people start calling Canonical.  

There are contests, you know, to find the most subtle ways to insert malicious code into open source software.  Winners are awarded prizes based on their methods of causing vulnerabilities in plain sight.

I will look for a link...

> **Paulmd said:**
> 


Another possible vector could be a rogue repository. 

The only security measures you need to take in Ubuntu is to keep up-to-date with updates and avoid third-party software.


> **Paulmd said:**
> 

A third possible vector would be a disgruntled employee. Almost every largish company has some. It would be naive to assume that Canonical doesn't have any. They can sometimes do a lot of damage, before they leave.


AFAIK, all uploads to the repos are logged.

---

### Post by armandh on 2007-08-26
more secure than this mess
[http://tinyurl.com/25c6ch](http://tinyurl.com/25c6ch)

---

### Post by por100pre1 on 2007-08-26
It's just a myth that hackers only want to hack Windows PCs. Many of them want to hack Linux servers... most servers nowadays are Linux servers. I dunno, maybe Linux servers are safer than Windows clients... :-P

---

### Post by kwacka on 2007-08-26
> **por100pre1 said:**
> It's just a myth that hackers only want to hack Windows PCs. Many of them want to hack Linux servers... most servers nowadays are Linux servers. I dunno, maybe Linux servers are safer than Windows clients... :-P

I agree, the problem is not down to numbers, but to the construction of the system.


[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)


The original post expresses valid fears, but the propogation of the malware would depend upon users installing it on their machine, rather than being self-propogating.

---

### Post by Paulmd on 2007-08-26
> **az said:**
> Not just anybody can upload to the repos (even backports).   And all packages are uploaded in source form and compiled by the autobuilders.

So, while the backports repos is probably a lot less popular, it is certainly a lot more secure than installing binary packages from third-party sources.  

That's wrong.  Binary-only software is way more vulnerable than source-based software simply because you can exploit a stable ABI a lot more easily than one that changes so often.  Linux is not more secure because it is less popular, it is a lot more secure because it is built differently.

Open source software is inherently *more* secure than closed-source.  The "security-by-obscurity" principle has been proven wrong.  It is far more helpful to have a security system running on transparent code than closed code - you end up with better code.  

Just because you know how the lock works does not necessarily  make it easier to pick.  Like encryption, just because you know the method of encryption does not make it easier to crack the key.  

There are contests, you know, to find the most subtle ways to insert malicious code into open source software.  Winners are awarded prizes based on their methods of causing vulnerabilities in plain sight.

I will look for a link...

The only security measures you need to take in Ubuntu is to keep up-to-date with updates and avoid third-party software.

AFAIK, all uploads to the repos are logged.

While it's true that it's easy to avoid software from untrusted sources, not everybody is aware of the danger. There are plenty of neophytes on linux that just assume that linux is secure, and so violate common sense. The greatest security threat is Stupid User Syndrome.  Windows may have a greater number of Stupid Users, but not a significantly different percentage. Social engineering works because even the best designed system cannot truly protect a user from himself.


As for logs... they are useful for catching the ******* afterward, but do not actually prevent him from doing the deed. 


Restricting uploads to the reputable repos is a good security measure, but having an autobuilder build the source doesn't really make any difference. All the builder does is make sure the code is compilable.  Reviewing the source by hand may help. But people's eyes start glazing over after a reading a few dozen pages of code. As long as there's not a function called StealUsersCreditcardInfo(), or something like that. :)

---

### Post by dr_pressure on 2007-08-29
> Open source software is inherently *more* secure than closed-source. The "security-by-obscurity" principle has been proven wrong. It is far more helpful to have a security system running on transparent code than closed code - you end up with better code.

Yes, I think I chose a bad topic name. I was more referring to "is the open source distribution model secure" (a la ubuntu public repositories).

---

