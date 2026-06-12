---
title: "More security concerns"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-11
My colleague like the idea of migrating to Ubuntu but is very concerend about security etc on a Linux box. 

Could someone in the know please answer these questions with as much detail as possible for me to alay his fears?

If a defualt install is performed how secure is it from hackers?

The fact that it can gain access to the WWW through a browser means a route is open to the Linux box so is it not possible for a hacker to gain access to his machine?

How secure is the browser regarding cookies and personal information?


Is is possible for hacker to track you through surfing to steal your identity and personal data on Linux?


His main concern is if his Linux box is somehow hijacked and used without his knowing to perform illegal activity.


What of spyware and addware etc?


On Swiftfox for example what of the surfing history, where is that kept and can it be hacked?

Thnx

---

### Post by mdsmedia on 2006-09-11
> **elpuerco said:**
> My colleague like the idea of migrating to Ubuntu but is very concerend about security etc on a Linux box. 

Could someone in the know please answer these questions with as much detail as possible for me to alay his fears?What is he migrating from? If he's migrating from Windows, without wanting to bash Windows, he'll be more secure in Ubuntu. Ubuntu's default installation leaves no ports open for anyone to get in through, unlike Windows which leaves ports open for "ease of use"

> **elpuerco said:**
> If a defualt install is performed how secure is it from hackers?Quite secure, as compared to Windows. Once again, not Windows bashing, by default Ubuntu is more secure than Windows. There is no absolute security, but if the user keeps their Ubuntu Linux OS up to date and doesn't deliberately or stupidly allow malware into their system, they are pretty secure.

> **elpuerco said:**
> The fact that it can gain access to the WWW through a browser means a route is open to the Linux box so is it not possible for a hacker to gain access to his machine?I can't answer this definitively, but I don't think that necessarily follows. I doubt that just having access to the net makes your box vulnerable.

> **elpuerco said:**
> How secure is the browser regarding cookies and personal information?Cookies are required by many sites for you to use their features. Cookies themselves are not necessarily bad. Generally cookies are just information saved on your harddrive and accessed by the site to re-use information you've given.

> **elpuerco said:**
> Is is possible for hacker to track you through surfing to steal your identity and personal data on Linux?Very difficult, in fact far more difficult than other OSs, but not impossible. I'd feel far more secure in Linux than other OSs.

> **elpuerco said:**
> His main concern is if his Linux box is somehow hijacked and used without his knowing to perform illegal activity.This is extremely difficult in Linux, especially Ubuntu, due to the permissions required to perform certain tasks. It's not impossible in any OS, but harder in Linux than say Windows, unless the user is running as administrator, which they are usually in Windows but not in Linux.

> **elpuerco said:**
> What of spyware and addware etc?Spyware and adware is next to non-existant in Linux. It's not impossible, but very rare in Linux.

---

### Post by xyz on 2006-09-11
Couldn't agree more with **mdsmedia**!

If you want te read more on "Security Issues":
[http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by Solver on 2006-09-11
Mdsmedia explains it all. I want to add something - most of the trouble comes from random stupid hackers who are searching for random computers to hack. Running Ubuntu, you are 99.8% safe from hackers lloking for random PCs, as they look for vulnerable Windows PCs. However, there is no such thing as absolutely security, so if a team of skilled hackers targets you specifically, they'll be able to hack through your Ubuntu security. But there's no reason why that should happen, unless you're the Pentagon, NASA or some other likely target for high-profile hackers.

So yes, Ubuntu's default install is far more secure than Windows. Moreover, Linux doesn't suffer from the spyware and malware problems.

---

### Post by 3rdalbum on 2006-09-11
I'd just like to add something.

People who write programs for Windows almost never sit down and think about "Is this program secure? Is there a way it could be misused to gain control of a system? Is my program sacrificing security in favour of convenience?". 

As a result, Windows programs don't warn users of the possible security implications of their actions (i.e. automatically opening e-mail attachments), and many Windows programs actually accept socket connections from remote locations! This isn't a case of the cracker finding a backdoor; it's a case of leaving the front door unlocked.

Because there's a whole security-concious culture about Linux, developers tend to be more mindful of good security practice, and this awareness gets into the design of the programs. For instance, the people working on Ubuntu's new startup sequence have been considering whether their code has holes in it that could allow malicious programs to start up. They have made sure that only the system administrator can add programs to the startup sequence.

If I was concerned about possible security holes in any part of my Ubuntu system, I could just download the source code and check its security myself. If I found a flaw, I could make changes, run the updated system, and submit the changes to the developers. Nobody can do that with Windows.

In addition, there are a number of things you can add-on to improve security on Linux, which have no equivilant on Windows. AppArmour is an extension that lets you define what a particular program can and cannot do. For example, your screensaver shouldn't need to modify passwords, so you can explicitly prevent your screensaver from being able to modify passwords. In this example, it becomes virtually impossible for crackers to remotely hack into your screensaver and convince it to change your password.

You can apply AppArmour to a Linux system, set the rules (or let AA set them for you), and then feel safe behind a number of layers of protection. If a program attempts to do something that you have banned, you immediately get a system mail warning you about it.

AppArmour is just one piece of your security puzzle. I'm assuming that if you're asking about Linux security, then you're not a network administrator and therefore wouldn't really need such things as AppArmour; but they are there if you want them.

This post has gone on quite long considering I originally only wanted to make one point, but I've not had a virus or spyware on either of my Linux machines and I don't take any special security precautions. AppArmour? Pfft. I don't need it, but if I did it would be available.

---

### Post by steve.horsley on 2006-09-11
I'd just like to reiterate three reasons why Linux is more secure than windows.

1)
Ubuntu's default install is **not listening** for incoming connections. Unlike windows which offers a number of services as default (including sharing your drive C - something I never found how to disable), Ubuntu offers **no** services, unless you explicitly install one. So people simply cannot hack in from outside.

2)
Linux doesn't run users with full admin rights. Now, it's always possible that a user will save and execute an email attachment, or a browser bug will be expolited to run malicious code from a web site, but that code has much less ability to compromise the machine because it can't write anywhere outside the user's home folder - it can't affect the system config or files.

3)
Because of 1 and 2 above, and also because Linux is less common than Windows, Windows is a much more productive target for the hackers and virus writers. So far, they pretty-much leave Linux alone. Why go for the hard ones when there are so many easy windows boxes around?

That said, you should use common sense. If you install a service that listens, you should think about a firewall to restrict who can talk to it. If you have secret data, consider that people may gain physical access and read it. You should still think before running any software you download.

---

### Post by elpuerco on 2006-09-11
Thanks for all the feedback folks muchly appreciated =D>

---

