---
title: "Repositories and Libraries ---- Clarificatino needed"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-05-16
Hi guys,

I have been using Ubuntu for a few months now, but one thing that I have yet to figure out is where/how do all the repositories work?  Is there certain software housed in certain repositories?  I guess a repository is a server with a database of software then?  Is that why you have to add repo's to your repo file to get software?  Aren't I missing out on software that's not listed in synaptic if a certain library is missing from whatever file lists my repositories?

Sorry for the bombardment of questions, maybe a link that can explain this all will help me figure it out.  Thanks :)

---

### Post by 67GTA on 2007-05-16
A repository is an address for a server where the software is housed. You can add more repositories at your own risk. Go to this site and look for the repositories section.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by 3rr0r on 2007-05-16
So a repository is just an address to a server that has software that I can download.  Okay, how do I know if a repo is safe to add to my list?  So, technically, I am limited to what software I can download so long as my repo list does not have ever repository listed in it right?  Like, currently, since i have never touched my repo list, I am only able to get what Ubuntu has provided me for.  Where is this file located so that I can edit this file?

---

### Post by FuturePast on 2007-05-16
> **3rr0r said:**
> So, technically, I am limited to what software I can download so long as my repo list does not have ever repository listed in it right?  Like, currently, since i have never touched my repo list, I am only able to get what Ubuntu has provided me for.

This is a *good* thing. It means that the software is properly maintained, and designed to work together.
Also Ubuntu imports a lot of software from the Debian distribution, which is regarded as a super-reliable source.

You are free to add whatever repository you want (see /etc/apt/sources.list) but then you take responsibility for making sure that that source is trustworthy.

---

### Post by 3rr0r on 2007-05-16
> **FuturePast said:**
> This is a *good* thing. It means that the software is properly maintained, and designed to work together.
Also Ubuntu imports a lot of software from the Debian distribution, which is regarded as a super-reliable source.

You are free to add whatever repository you want (see /etc/apt/sources.list) but then you take responsibility for making sure that that source is trustworthy.

Ahh, thats it!  The sources.list file.  I forgot the name of it :)  Okay, I see the reason behind not listing every repo.  I guess there can be malicious sites that would have some "good apps" to entice you to d/l them but may actually not be safe or compatible.  Now it all makes some sense.

---

