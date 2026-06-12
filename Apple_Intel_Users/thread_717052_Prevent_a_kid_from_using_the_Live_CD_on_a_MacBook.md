---
title: "Prevent a kid from using the Live CD on a MacBook"
date: 2008-03-06
forum: Apple Intel Users
---

### Post by kellykungfu on 2008-03-06
Hi Everyone,

I'm more of a PC person but would like to pose this on this forum.  Is it possible to keep a person from using the Ubuntu Live CD to boot up into Linux?  The reason I ask is because, the family that I'm helping has a son that is getting very computer literate.  On the MacBook, I setup the Parental Controls for time usage and also time restrictions.  So, if he was cleaver enough, he could pop in the Ubuntu CD and bypass the Mac OS.

On a PC, I can go into the BIOS and disable the CD/DVD Drive so he can't do this.


Thanks in advance.  Have a great day and God bless.


-kelly

---

### Post by fedex1993 on 2008-03-06
i think the intel macs have bios you might want to ask on the mac forums instead of here

---

### Post by aysiu on 2008-03-07
Maybe try [going into the rEFIt menu](http://refit.sourceforge.net/doc/c2s1_activate.html) and seeing if it has an option similar to the BIOS one for preventing the booting of a CD?

Frankly, though, physical access = root access. Your best bet if you want to limit this kid's time on the computer is to just lock the laptop away.

---

### Post by guidop on 2008-03-07
See this Apple document: 

[http://docs.info.apple.com/article.html?artnum=106482](http://docs.info.apple.com/article.html?artnum=106482)

Apple provides a utility to configure the boot firmware to require a password to boot the machine from anything other than the default partition, both for PPC and Intel Macs.

Since you have a MacBook, you should be running OS 10.4 or later.  The referenced document says:
> For Mac OS X 10.4 or later, you must use the updated version that can be copied from the software installation disc (located at /Applications/Utilities/ on the disc). 

However, if you're dual booting using rEFIt, it appears you'll also have to edit the rEFIt configuration to prevent CD booting from the rEFIt menu:

[http://refit.sourceforge.net/doc/c3s2_access.html](http://refit.sourceforge.net/doc/c3s2_access.html)


Please note that I have not tried any of this on an Intel Mac.  However, on a PPC Mac, I know that the utility can be defeated by removing or adding RAM to the machine and resetting the PRAM 3 times.  More info in this mailing list thread:  [http://lists.apple.com/archives/Client-management/2004/Nov/msg00092.html](http://lists.apple.com/archives/Client-management/2004/Nov/msg00092.html)  (BTW the link to the NSA pdf is broken.)  Thus to quote the previous poster aysiu:> physical access = root access  I believe one can also defeat a PC's BIOS password protection by removing the motherboard battery, so one is no more secure there, either.


I think the bottom line is that you can go to a lot of trouble to slow the kid down, but you can't stop him if he's got the machine in his hands and is determined enough and smart enough.  If he's bright enough to defeat your efforts, it may be time to try to educate him, and have his parents tell him the limits of acceptable behavior, and that they'll have to trust him on some things.  I figure it's just going to have be part of letting him grow up.

---

### Post by NightwishFan on 2008-03-07
My sister and her friends used my Ubuntu live cd to access Myspace.com from my computer. Frankly they are not invited over my house anymore. Best option is to hide the cds like you would a firearm.

---

### Post by steveneddy on 2008-03-07
Hide the computer.

Super glue the CD shut.

Hide all CD's, especially Live CD's.

Put the computer in a common area of the house where the parents can see what the person is doing when accessing said computer.

Password the person out of the machine.

Turn off the wireless router and hide the Ethernet cables.

Take the battery out of the laptop until Mom & Dad get home.

Take the laptop with you when you leave.

Sit down and have a talk with you son/daughter and discuss Internet responsibility and rules. You are the boss, let them know it. Maybe surf the Internet with them and get them to show you what they do. 

I never gave my kids Internet freedom in their bedrooms. The PC was always in a common room where they could be watched. Now they are both Internet responsible.

My .02

---

### Post by priegog on 2008-03-07
> **steveneddy said:**
> 
Sit down and have a talk with you son/daughter and discuss Internet responsibility and rules. You are the boss, let them know it. Maybe surf the Internet with them and get them to show you what they do. 

I never gave my kids Internet freedom in their bedrooms. The PC was always in a common room where they could be watched. Now they are both Internet responsible.

My .02

I kindda agree. I am not a father, but I DO know what my father did that was different to other fathers, that I think made me a better person. I think it's great that kid is getting computer literate (that's the way I was), but instead of demonizing it, or worse, trying to outsmart him (not gonna happen, at least not where computers are concerned), maybe they should try a different parenting approach. But then again, this is none of my business, and from what I gather, neither it is yours, so maybe you could try to explain to his parents that physical acces= acces, no matter what they do. Because you know that whatever you do to the pseudo-bios config files he can probably undo, and the same for every other method. The best way would be to take the computer away. But like I said, to me that would be like halting his development.

---

### Post by bilboe on 2008-03-08
Do the following to enable open firmware password, hence rendering any other boot option USELESS. (Besides main HD)


1) Boot into the Open Firmware. (Command + Option + O + F)

2) At the command prompt, type "password" (without the quotes, of course). You will be prompted to enter in the password you wish to use. Type your password, press the return key, retype your password again, and press return to verify that that the first password you typed is indeed the password you want. (Note: the password is stored in the "security-password" variable, but the contents of this variable is never shown via the "printenv" command.)

3) Type "setenv security-mode full" OR "setenv security-mode command" OR "setenv security-mode none", depending on which level of security you wish.

4) Then type "reset-all" to restart the computer.


Disabling Password Protection

1) Boot into the Open Firmware. (Command + Option + O + F)

2) Type "setenv security-mode none" and press return.

3) Enter in the password at the password request prompt and press return.

4) Then type "reset-all" to restart the computer.

---

### Post by raul_ on 2008-03-08
I think that if he bypasses it, you should give him credit for knowing what the hell he's doing (though you already should know, since he wants to get his hands on linux)

---

### Post by cyberdork33 on 2008-03-08
> **bilboe said:**
> Do the following to enable open firmware password, hence rendering any other boot option USELESS. (Besides main HD)


1) Boot into the Open Firmware. (Command + Option + O + F)

2) At the command prompt, type "password" (without the quotes, of course). You will be prompted to enter in the password you wish to use. Type your password, press the return key, retype your password again, and press return to verify that that the first password you typed is indeed the password you want. (Note: the password is stored in the "security-password" variable, but the contents of this variable is never shown via the "printenv" command.)

3) Type "setenv security-mode full" OR "setenv security-mode command" OR "setenv security-mode none", depending on which level of security you wish.

4) Then type "reset-all" to restart the computer.


Disabling Password Protection

1) Boot into the Open Firmware. (Command + Option + O + F)

2) Type "setenv security-mode none" and press return.

3) Enter in the password at the password request prompt and press return.

4) Then type "reset-all" to restart the computer.
This works on Intel Macs that do not have Open Firmware?

---

### Post by bcr88 on 2008-03-09
> **cyberdork33 said:**
> This works on Intel Macs that do not have Open Firmware?

This is definitely PPC-only, or else I probably would've played with it already and screwed something up, lol.

---

### Post by robzon on 2008-03-09
Poor kid.. His access to Linux (thus a lot of useful knowlege) will be denied. I'd be pissed if someone made me use only MacOS X :|

---

### Post by tgalati4 on 2008-03-09
You know LInux is becoming mainstream when you have to hide the Ubuntu CD's from guests.

---

### Post by st0n3cutt3r on 2008-03-09
Will this also lock out knoppix?   I actually was on the other side of this equation just about a month ago (helping a friend of mine use her computer after the computer was scheduled to shut down) and I suggested knoppix to her.

---

### Post by Depressed Man on 2008-03-09
> **kellykungfu said:**
> Hi Everyone,

I'm more of a PC person but would like to pose this on this forum.  Is it possible to keep a person from using the Ubuntu Live CD to boot up into Linux?  The reason I ask is because, the family that I'm helping has a son that is getting very computer literate.  On the MacBook, I setup the Parental Controls for time usage and also time restrictions.  So, if he was cleaver enough, he could pop in the Ubuntu CD and bypass the Mac OS.

On a PC, I can go into the BIOS and disable the CD/DVD Drive so he can't do this.


Thanks in advance.  Have a great day and God bless.


-kelly

Besides what's been pointed out. You might also want to ensure he can't boot from a flash drive. 

But as another poster said, physical access = root access. Heck even if you did anything to the BIOS he could be smart enough to open up the laptop and reset it [which would probably void the warranty as well]. And even now, with the recent news of such hacks (where no method of encryption is secure enough due to the method they attack).

---

### Post by mercenaryhmster on 2008-03-09
in all honesty, if the kid is intelligent enough and open-minded enough to even try a linux solution to his problems, then just let the kid use the computer!  he will be less likely to try and rebel, and god knows we need better computer techs these days

---

### Post by bilboe on 2008-03-09
> **bcr88 said:**
> This is definitely PPC-only, or else I probably would've played with it already and screwed something up, lol.:confused::confused::confused:


Absolutely not true! I have this on my very own intel macbook!

---

### Post by ronocdh on 2008-03-09
> **mercenaryhmster said:**
> in all honesty, if the kid is intelligent enough and open-minded enough to even try a linux solution to his problems, then just let the kid use the computer!  he will be less likely to try and rebel, and god knows we need better computer techs these days
I honestly do think this comes down to more of a parenting issue than a computer issue, but there was a very direct question posed. I think that question has been adequately addressed. Now just let the kid tinker already!

---

### Post by cyberdork33 on 2008-03-09
> **bilboe said:**
> Absolutely not true! I have this on my very own intel macbook!So you are saying that you can access an Open Firmware prompt on an EFI-based, Intel Macintosh by holding CMD+OPT+O+F? Just trying to make sure of what you are saying, because, although I have been able to make other Boot-Key combos work such as CMD+S and such, I have not been able to use CMD+OPT+O+F for anything...
> **ronocdh said:**
> I honestly do think this comes down to more of a parenting issue than a computer issue, but there was a very direct question posed. I think that question has been adequately addressed. Now just let the kid tinker already!Absolutely. This is not a thread on parenting.

---

### Post by bcr88 on 2008-03-10
> **bilboe said:**
> :confused::confused::confused:


Absolutely not true! I have this on my very own intel macbook!

I meant that you cannot hold down CMD+OPT+O+F to get into Open Firmware, because Intel Macs do not have Open Firmware. You can install a Firmware Password protection application to set up IN Mac OS X, you can boot directly into Open Firmware on Intel Macs.

---

### Post by scramasax on 2008-03-10
> **kellykungfu said:**
>  So, if he was cleaver enough, he could pop in the Ubuntu CD and bypass the Mac OS.

The "Mac OS" has been dead for some years -- and good riddance, too.  Current Apple machines run OS X, which is a form of Unix with a GUI based on NeXTSTEP on top (albeit Apple larded some old Mac stuff into it).

It seems to me that this is _your_ scenario.  The kid's may be different.  Assuming he really is computer-literate, he doesn't need a live CD.

He just reboots while holding down command-option-S.  That gets him single-user mode:

[http://docs.info.apple.com/article.html?artnum=75459](http://docs.info.apple.com/article.html?artnum=75459)


Of course, in reality he might not be that _au fait_ with what he *could* do.  But in general if someone has physical access to a machine all bets are off.

---

### Post by Stupkid on 2008-03-10
If Internet access is what you are trying to control have you thought about using an authenticating proxy?  As others have stated access to hardware means you can eventually do whatever you like.  How will you handle a friend bringing over an Internet enabled device that starts browsing the web?  An authenticating proxy will handle these scenarios for you.

---

### Post by Eniak on 2008-03-11
I'd b proud if it was my kid  :D

anyway, I passed through some similar problematic cuz I hang around very frequently with my MBP and I bought Undercover to feel a bit safer. The trick of Undercover is to set a firmware password and to make a numb account, so if an unauthorized person uses the computer, this person will be obligated to use this numb account (on OS X) so Undercover will do it's job. The problem was when I decided to install rEFIt and triple booting on my mbp, anyone could choose an OS without being asked for any password for it, and so undercover became useless.

The solution I found was to change the rEFIt installation from my HD root from the root of a pen drive, now If I want to use rEFIt, and boot from any other partition or from a CD/DVD, I have to type my password.

[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

