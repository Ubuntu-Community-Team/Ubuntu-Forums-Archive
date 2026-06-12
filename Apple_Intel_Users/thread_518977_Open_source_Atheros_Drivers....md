---
title: "Open source Atheros Drivers..."
date: 2007-08-06
forum: Apple Intel Users
---

### Post by Gen2ly on 2007-08-06
I notice the other day that the Free Software Foundation has given the green light to OpenHAL to begin developing open source drivers for Atheros chipsets ( i.e wireless cards ).

[**[COLOR="Sienna"]Developers free to work on open-source Atheros Wi-Fi[/COLOR]**]("Developers free to work on open-source Atheros Wi-Fi")

I always like the open source solution, but I'm gonna argue that I think Atheros has been pretty good about developing LInux drivers - some companies don't at all.  And for the most part the drivers have worked pretty well.

As an advocate for open source I have to make a point however that open source also carries it problems.  With open source being open to anyone it gives a chance for anyone to put code into them.  Even code that is only beneficial to the programmer.  But yes you say, another programmer will catch it... but not necessarily so.  I think it's actually pretty rare that someone looks at another's code and more likely that they just write in what is needed.   Considering things as drivers above, hackers could take over a network by writing hooks into such drivers.  So we should all be concerned about the security of our computers.  I think to this point Atheros has done a good job so far.

---

### Post by duffman25 on 2007-08-06
> **Dirk.R.Gently said:**
> I notice the other day that the Free Software Foundation has given the green light to OpenHAL to begin developing open source drivers for Atheros chipsets ( i.e wireless cards ).

[**[COLOR="Sienna"]Developers free to work on open-source Atheros Wi-Fi[/COLOR]**]("Developers free to work on open-source Atheros Wi-Fi")

I always like the open source solution, but I'm gonna argue that I think Atheros has been pretty good about developing LInux drivers - some companies don't at all.  And for the most part the drivers have worked pretty well.

As an advocate for open source I have to make a point however that open source also carries it problems.  With open source being open to anyone it gives a chance for anyone to put code into them.  Even code that is only beneficial to the programmer.  But yes you say, another programmer will catch it... but not necessarily so.  I think it's actually pretty rare that someone looks at another's code and more likely that they just write in what is needed.   Considering things as drivers above, hackers could take over a network by writing hooks into such drivers.  So we should all be concerned about the security of our computers.  I think to this point Atheros has done a good job so far.

If you think opensource is not beneficial to driver development, then why do you use linux?

The point you try to make depends on the resources around an opensource proyect. You can find a proyect with no code review, no qa, etc. But that's not the point in linux. And I bet the people reverse engineering the atheros hal are smart people that can see failures in patches. Besides, if atheros commits a mistake and no one sees the source, you are in the exact situation you're afraid of. You think there are no code reviewers, but you are wrong. Ubuntu for instance has a security team that reviews code before it enters main. For instance: [https://wiki.ubuntu.com/MainInclusionCompiz](https://wiki.ubuntu.com/MainInclusionCompiz)

Open source is great.

---

### Post by benanzo on 2007-08-06
To my knowledge, the only code Atheros actually writes is the proprietary HAL module that Madwifi depends on.  The remainder of the code is done by the Madwifi devs, which is all Free/OSS.  I disagree that security-by-obscurity makes you safer because you're less vulnerable to malicious SVN commits by some rogue 16 y/o in his basement.  I'd rather have all the eyes on all the code than none.  I heard this argument come from MS in circa 1996.  "But if everyone can see the code, then they can write backdoors and viruses *really easily*!"  As if Windows being closed actually stopped the malicious 16 year olds from doing a bang-up job at proving Windows to be the most insecure blob of software on planet Earth.

Madwifi is heavily peer-reviewed.

---

### Post by Gen2ly on 2007-08-07
> **benanzo said:**
> Madwifi is heavily peer-reviewed.

Nahhhh really?!  You can comment on a text files that total more than 10MB!?

Definitely I'm being little paranoid - that happens a bit when you start looking into security  ;) -  and I made a philosophical reference when I should be commended the work at OpenHAL.  Believe me, I appreciate the job ther are doing.  It still is a concern of mine, though. Yeah, looking into the code, it's difficult to fathom to a newcomer how its kept secure ( a simple driver can take thousands and thousands of lines of it ), but then you realize the code is written by people who have been writing code for awhile.  I looked into more of the QA bit you both mentioned that that definitely helps make the Linux users more secure.  I love linux.  I actively support it, but this has to be pointed out that projects aren't always secure.  QA does look like it's becoming a standard on most developer projects.  Though good security really just means knowing people whom to trust as any program on any OS from a untrusted source is a potential worm. So to have code that is open definitely is reassuring.  Unfortunately not all Linux programs have QA, so I have discovered recently.  So a 16 year old pimpled chocolate eater can still put malicious code into some developers projects.  I'm still learning about programming, but I'm gonna be sure to learn more about developing QA.    My little beef here was not at OpenHAL, this sounds like a necessary and respected type of project.  I suppose I was just saying that QA doesn't exist for all these projects ( including a few popular ones ) and taking security as a non-issue in Linux isn't smart for anyone.

On a semi-side note I noticed this as I was perusing my [FONT="Fixedsys"]/var/log/messages[/FONT] the other day, lol:

```
Aug  4 10:04:00 localhost kernel: ath_hal: module license 'Proprietary' taints kernel.
Aug  4 10:04:00 localhost kernel: ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
```

---

### Post by benanzo on 2007-08-08
The madwifi devs peer-review every patch (which could be 2 lines of code, or 200) before letting it roll out into a release.  They don't have to audit all 10 MB of ascii text.  Every release is checksumed and if there are discrepancies a simple diff would reveal the problem.  The odds of an intentional backdoor being allowed into a release based on a patch posted to the list are extremely slim.

This is usually the way distributed development works:

1) A patch gets posted to the list (or an SVN commit)
2) The development team reviews the code (usually one of the lead devs digitally signs it before diffing it into the main tree.)
3) The complete tree (including the new patch) gets hashed for a new MD5 sum.
4) The code gets released with an option for the end-user to verify the digital sig before running it.

The only time a backdoor or other malware can enter the codebase is during the commit, since every alteration to *any* of the code will cause the whole tree to get a new signature (which is automated in CVS and SVN.)  This is why we import GPG keys for certain repositories.  It's so we can verify the integrity of the code by trusting that the maintainer (the signer of the GPG key) has taken the necessary steps to assure that the code can be trusted.  Of course, this whole code-security process is moot if the patches aren't reviewed before inclusion.  I trust that the madwifi devs do an excellent job of this.

---

### Post by cyberdork33 on 2007-08-08
Isn't the whole code-review, QA thing one of the major benefits of having a source repository? Does it not track changes and keep archives of source? I think it would be quite simple to have all changes reviewed, just by having the repository log when/where/by whom changes are made.

And while this is a great conversation, it is a bit OT for a support forum.

---

