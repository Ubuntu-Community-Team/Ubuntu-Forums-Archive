---
title: "what's up with skype, anyway?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-02-01
Ok, here's how this goes:

I installed the next-to-the-last version of Skype from the Skype.com Web site. It immediately killed my sound and, although it would start up, I could never connect to another Skype user.

Then, I found a post in these forums by a user who had diagnosed the problem, compiled his own Skype deb file and had posted it somewhere with a brief, but very useful, "how to" for the installation. I still have this file on my computer: 

skype_1-1.2.0.18-1_i386.deb

but cannot find the original "how to" post.

The reason I need this is because I rather unsmartly "updated" my Skype program when Skype issued its latest Linux release - and once again I have a program that kills the sound and doesn't connect to anything. (I know, if it's not broke, don't fix it.)

I know this has been a problem for numerous people but I am wondering what's up with Skype? Are their packages bad and if so, why? And, meantime, what can I do to work around this ongoing problem?

I realize Skype is "free" (pc-to-pc anyway) but it would also be nice if it worked, too.

Thanks in advance.

gm

---

### Post by aysiu on 2006-02-02
If you installed a .deb, you should be able to mark it for "complete removal" in Synaptic Package Manager. Do that, erase your ~/.Skype folder, then reinstall the "good" .deb package.

---

