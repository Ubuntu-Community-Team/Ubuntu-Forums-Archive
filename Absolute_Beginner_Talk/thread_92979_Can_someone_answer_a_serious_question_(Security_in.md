---
title: "Can someone answer a serious question? (Security in Linux/ Windows)"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by cgrucelski on 2005-11-20
Hello all.

Being new to Ubuntu, and linux in general, I have frequently heard it said and seen it written throughout this web site (and other linux sites) that firewall, anti-spyware and anti-virus software programs are not necessary because Linux is inherenly not suceptible to these threats.

My question is... Why? What make Ubuntu, or any other flavor of linux for that matter, immune to these pests that so plague all versions of Windows?

Would someone mind seriously answering this question without simply bashing Microsoft? (even if they deserve it!) I know this seems to be the "sport" in the Linux community, but I'm not interested in the "linux is better than windows" argument at this point. I consider myself fairly computer literate, just not very experienced in the world of linux. Up until I recently discovered Ubuntu, I didn't think or believe linux was a serious option for anyone but the "geeks" (no offense to anyone on these boards!) But, I am beginning to change my mind. 

I love what I see in Ubuntu, but I think the "sell" is going to be difficult for some of the people I know. For example, my father-in-law, who owns a small business with 20+ workstations (all running different variations of Windows) and who is self-taught with computers and is basically the IT department for his own company, is suspicious of the claims regarding the inherent stability and security of linux.

Can someone give me an answer or explanation that is not "shallow" but also does not require a degree from MIT to understand?

Based upon the forum responses I have been browsing over the past week or so, I am looking forward to the knowledgable and helpful response I can expect from the Ubuntu community... Thanks in advance!

---

### Post by Kyral on 2005-11-20
IMO, I think it has to do with the permissions system. I go on a quasi-rant about it when I cover Permissions in Terminal For Beginners

---

### Post by matthew on 2005-11-20
Linux, Unix, and similar operating systems are designed for multiple users. Normal users are not generally allowed to install anything, nor are normal users allowed to modify configuration files in any way. Only one person (or a very limited number of people) on a Linux/Unix type system has that authority, that user is called "root" (or those to whom root has given authority, perhaps more limited than root, but greater than normal users).

In Ubuntu, instead of creating a user called "root" another method is instituted called "sudo" which allows a normal user who has been given permission to make modifications.

In either instance a password is required before any changes may be made. This eliminates the possibility of downloading a program that can execute itself and make harmful changes to configuration files or install something without the root user's permission.

That takes care of just about all virus/worm/spyware scenarios.

As for a firewall, linux already has one, it's called iptables and it is a part of the kernel. It is automatically configured in Ubuntu and most Linux distributions to not allow any traffic to enter the computer that is not specifically invited, i.e. through a web browser, or will simply not answer those requests thereby seeming not to exist. So by default malicious persons or programs trying to get into an Ubuntu computer will generally not know your computer exists and/or will be thwarted in their attempts to enter it.

That is simplified, but kind of the "no computer degree" but "not MS bashing or over-simplified" answer. I hope that helps.

---

### Post by cgrucelski on 2005-11-20
Thanks so much for both of your quick responses...

Matthew, your explanation was exactly what I was looking for and expecting. 

Thanks!

---

### Post by aysiu on 2005-11-20
As far as I know, it boils down to these factors in combination:

1. **A better security model**: Windows, by default, runs the main user as administrator, who can do just about anything to the system (even accidentally) without having to enter a password. Linux (and Unix-like systems, like Mac OS X) have a general policy of not letting ordinary users affect system-critical files, and even the main administrator must enter a password to make system-wide changes. Everyone acknowledges this system is a better security model because I hear even Windows Vista is supposed to have something similar to this.

Theoretically, you can set up Windows (XP and before) to have an administrator and regular users, but it's not fully functional. First of all, a regular user cannot merely enter a password to temporarily assume administrative responsibilities--she must actually log in as the administrator to make changes. Secondly, some Windows programs actually will not function properly unless the user is the administrator of the computer.

2. **Security through Obscurity**: this is what actually Windows advocates point to as the main reason. How big a part this plays in Linux security it debatable, but it is there--if you're the largest percentage of the user market, you're also the biggest target. Since Mac and Linux make up less than 20% of the desktop market, they're less likely to get attacked than Windows.

3. **Software Installation**: Yes, there exist open source programs for Windows, but most Windows users don't know about them (except maybe about Firefox). The ordinary Windows user has to be very wary of even innocuous-seeming programs that may install spyware on her computer. In Ubuntu, if you stick to the repositories, you *know* the software you're installing is safe for your computer (and honestly almost all Linux software--even the ones not in the repositories--do not have spyware or viruses).

---

### Post by 23meg on 2005-11-21
Spyware: Doesn't exist because there aren't huge corporations on top that want to spy on you.

Adware: Doesn't exist because software is free and doesn't need ad sponsorship.

Worms / Trojans: Don't exist because when hackers find a security flaw in Linux they concentrate on providing a patch to fix it rather than exploiting it to cause damage.

---

### Post by cgrucelski on 2005-11-21
So is it fair to say then, that the linux operating system itself is not actually completely immune to viruses and other types of security threats per se, but that the only way the system would be vulnerable to such threats is if the administrator _INTENTIONALLY_ allowed the system to become compromised?

Meaning, unlike in a Windows environment, one would have to be very knowledgeable and experienced _TO_ screw up their linux system, whereas in Windows, one has have to be very knowledgeable, experienced and dilligent _NOT TO_ screw up their system.

Fair assessment?

---

### Post by 23meg on 2005-11-21
[QUOTE=cgrucelski]So is it fair to say then, that the linux operating system itself is not actually completely immune to viruses and other types of security threats per se, but that the only way the system would be vulnerable to such threats is if the administrator _INTENTIONALLY_ allowed the system to become compromised?[/QUOTE]Yes.
[QUOTE=cgrucelski]
Meaning, unlike in a Windows environment, one would have to be very knowledgeable and experienced _TO_ screw up their linux system, whereas in Windows, one has have to be very knowledgeable, experienced and dilligent _NOT TO_ screw up their system.

Fair assessment?[/QUOTE]Almost, yes. If you take basic measures such as not logging in as root and not installing unverified packages you're very unlikely to get trouble in Ubuntu.

---

### Post by aysiu on 2005-11-21
Bottom line, though: security means nothing if you have a stupid user...

**JERRY**: Stolen?
**ELAINE**: [Kramer enters the apartment] Someone left the door open. [it's clear that she means Kramer; she walks to the bathroom]
**JERRY**: [to Kramer] You left the door open?!
**KRAMER**: Uh, Jer, well ya know, I was cookin' and I, I uh, I came in to get this spatula...and I left the door open, 'cause I was gonna bring the spatula right back!
**JERRY**: Wait, you left the lock open or the door open?
**KRAMER**: [bobs his head guiltily] The door.
**JERRY**: The door? You left the door open?
**KRAMER**: Yeah, well, I was gonna bring the spatula right back.
**JERRY**: Yeah, and?
**KRAMER**: Well, I got caught up... watching a soap opera...[with a broken voice] The Bold and the Beautiful
**JERRY**: So the door was wide open?
**KRAMER**: Wide open!
**JERRY**: [Elaine enters the living-room] And where were you?
**ELAINE**: I was at Bloomingdale's...waiting for the shower to heat up.
**KRAMER**: Look, Jerry, I'm sorry, I'm uh, you have insurance, right buddy?
**JERRY**: No.
**KRAMER**: [looks shocked] How can you not have insurance?
**JERRY**: Because...I spent my money on the Clapgo D. 29, it's the most impenetrable lock on the market today...it has only one design flaw: the door...[shuts the door] must be CLOSED.

--*Seinfeld*: "The Robbery"

---

### Post by cgrucelski on 2005-11-21
LOL - That's a classic episode! 

And you ain't kidding on that one... I'm the guy all my friends call when their Windows system is running slower than molasses running uphill in January, so I've seen my share of stupid installs, even more boneheaded uninstalls, system crashes, spyware, malware, viruses... the works. 

Everyone's comments have been very helpful so far. The more I know about linux (and Ubuntu specifically), the more dangerous I will become! I will spread Ubuntu like a virus... 

Hey, speaking of which, there's a great idea! Can't someone create an email attachment that installs Ubuntu onto their system when unwitting Windows users execute the "click me now" email attachment? (since that seems to be one of the most boneheaded things I see over and over again...)   

:)

Anyway, thanks for the explanations and comments. Keep 'em coming!

---

### Post by r4ik on 2005-11-21
Reading the Topic i get the following message since a few days

The "/usr/sbin/synaptic" program was started with the privileges of the root user without the need to ask for a password, due to your system's authentication mechanism setup.

It is possible that you are being allowed to run specific programs as user root without the need for a password, or that the password is cached.
This is not a problem report; it's simply a notification to make sure you are aware of this.

Can't remember changing anything question is how do i "undo" this and does it
affect synaptic only or the system in total?
Is there a need to change it ore can i leave it as it is.
Thanks in advance.

Had a cup a coffee wich opened my eyes sorry for beeing stupid.
Have a nice day all.

---

### Post by poptones on 2005-11-21
*Worms / Trojans: Don't exist because when hackers find a security flaw in Linux they concentrate on providing a patch to fix it rather than exploiting it to cause damage.*

Really dangerous generalization. The ssh exploit that caused so much trouble a year or so ago was only discovered when the code was anonymously posted on someone's door at a grey hat con. Obviously, it had been known before this... but only to a priviledged few black hats.

---

