---
title: "[SOLVED] Absolute beginner questions"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Ertai87 on 2007-12-20
OK, so I have a really stupid question (stupider than my previous ones...with all the help I've been asking for I kind of feel like a nuisance to you guys =\), so if anyone can help me out, it would be appreciated:

I had a HUGE HUGE problem with viruses under Windows, and I'm a bit paranoid about security under Linux (even though every person I've talked to has said not to worry).  How can I know if I've got something shady on my computer?  For example, today I looked at my running processes and found a process called "vino-session".  Apparently I found out it's the Linux equivalent of RDP, but I didn't start it (or even install it!) and I want to know why it's running.  Where/how can I find a list of Ubuntu background processes that should or shouldn't be running at startup?  Thanks.

---

### Post by aeiah on 2007-12-20
in synaptic (system>administration>synaptic) you can select the 'Status' button and select a filter that'll show only installed applications, although you'd be trawling through quite a lot. there's probably a list knocking around of what to expect your running processes to be. but basically put, you'll find it very difficult to pick up any nasties that'll affect your ubuntu system. i have never encountered any virus or spyware. im not too sure that any exists right now.

---

### Post by obrient on 2007-12-20
By default Ubuntu installs Vino. However I don't believe that it runs unless you telll it to. You can find your settings System > Preferences > Remote Desktop. Just make sure it is turned off and you are set as far as I know.

---

### Post by Nano Geek on 2007-12-20
Hey, it's fine to ask a lot of questions. You can be sure that everyone here had to when they first started out. :)

The process 'vino-session" is installed by default in Ubuntu I believe, and it fine.
If you want to be double-sure though you could try a Linux anti-virus such as [clam-antivirus]("apt:clamtk"), or [Panda anti-virus for Linux]("http://www.pandasoftware.com/download/linux/linux.asp").

---

### Post by Ertai87 on 2007-12-20
Right, but why do I have a program with the word "session" in it for an RDP program by default? :S

---

### Post by Nano Geek on 2007-12-20
I think that's just its name. It's perfectly fine to keep running.
Every program in the repositories is virus-free and OK to install.

---

### Post by Ertai87 on 2007-12-20
OK, so I shouldn't be worried about the potential backdoor on my system?  Is it a potential backdoor?

---

### Post by Nano Geek on 2007-12-20
No, as long as you don't set it where anyone can connect to your computer via Remote Desktop, you should be fine. 

Currently, no Linux viruses exist that do any kind of damage.

---

### Post by Ertai87 on 2007-12-20
Well, for a time, it was set where anyone could control my computer, but nobody could see it (the first box was off but the second was on).  I'm just worried my comp's already been hacked...I just formatted on Monday and my wireless connection at the place I'm living is a bit sketchy...

---

### Post by Nano Geek on 2007-12-20
With Linux, you really don't have much of anything to worry about.
Don't give out your password, and you should not have anything to worry about.

---

### Post by niteshifter on 2007-12-21
Hopefully the below will ease your mind a bit more:

Windows (in all it's myriad forms) exists on 8 to 9 out of 10 personal (that is, non-server class) computers. Malware has evolved from idle hacking about to a regular business, complete with share-holders. Now I ask you: Which segment of the "market" would you target? *

On the technical merits: Windows is notorious for exposing open ports. Ubuntu (desktop) does not do this. Although Windows can be set up to use the concept of user privilege, out of the box it doesn't. And when people do set up user privileges they frequently revert - a fair amount of Windows software needs full admin rights to run. GNU/Linux (Ubuntu) is waaay different - user rights / privileges are built-in from the very core of it. One has to jump through hoops to set up an open-boot system. This concept of user privilege extends down to the device and file level: You don't have the requisite rights - you can't do anything with the object. This concept of ownership extends to RAM memory as well which also helps a lot.

There are very few (mostly proof of concept) attacks for GNU/Linux, but implementing them is way above the script-kiddie level of expertise. Will probably be fixed by the time we GNU/Linux users become a sizeable enough "market".

Even with all the above in play, the GNU/Linux user is not absolved of *all* responsibility: Beware of social engineering "attacks" - phishing and the like. Don't use software from a source you don't know (i.e. some arbitrary site), get what you need from the official repositories and from places recommended - and seconded - from these forums. Setup your wireless router (if you have one) with WPA and MAC address permissions. Enable macro security in OpenOffice.

In other words, a little common sense and ordinary care, you'll be fine :)

Although I hate to use the "I do X - you should too" argument ... You'd have to go some distance to find someone more paranoid about system security than me, and I'm quite comfortable with Ubuntu's security model with respect to external "by-wire" attacks. Physical threats (like theft) - that's a 'nuther kettle of fish to sort out.

* Last time I went barefoot (sans router, direct to cable modem) a few months ago, there were 50-some-odd computers found. 18 in the workgroup MSHOME - that's Win 95, 98 (and ME IIRC). Those machines haven't been patched for years now, M$ just doesn't do that anymore for those versions. Why go after the hard ones when there is such easy pickings to be had?

---

### Post by Ertai87 on 2007-12-21
OK, thanks.  But just out of curiosity: On my personal computer (work computer is different), I've never once in my life had to use RDP.  If I go sudo apt-get remove vino, will anything break?  I'd prefer not to have it on my system if I view it as a potential security threat with no upside.

---

### Post by Nano Geek on 2007-12-21
No, everything will still work fine if you remove vino.

---

### Post by Ertai87 on 2007-12-21
OK, I removed Vino and rebooted and now that session thingy is gone.  I feel better now.

---

### Post by Nano Geek on 2007-12-21
Good, I hope you enjoy using Ubuntu.

Merry Christmas!

---

### Post by thelatinist on 2007-12-21
Glad you got the help you needed.  Don't forget to mark this thread [Solved] using the thread tools!

---

