---
title: "Beginner to Linux wants to gain understanding"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Nephilim on 2006-06-14
Hello,

First off, let me say, I'm impressed with Ubuntu, great work has been done here.  I've tried many distros from Slack to Debian to Mandrake (pre-Mandriva), and even older versions of Ubuntu, and Ubuntu is the distro that has caught my interest in giving Linux a serious try as my main desktop OS.

I have some experience installing and 'somewhat' configuring a Linux box, however my main knowledge of computers comes from using Windows and Macintosh OS's and building them for many, many years.  The reason for this post has less to do with usage questions and more to do with the theory behind some of the things I see in Linux.

Can anyone point me to some reading material (or just explain it here) on why the directory structure is the way it is?  I'd like to gain some knowledge of the reasoning behind why it is the way it is, and hopefully some insight into how I can use it more effectively.  As it stands right now, I can muddle around and find stuff that I need to find, but it would be much more helpful if I *understood* why things are where they are as opposed to somewhere else in the directory structure.

I have searched the web for this, and maybe I was just blind and missed it somewhere, but any help with this would be greatly appreciated!

Thanks!

---

### Post by johnc4510 on 2006-06-14
Maybe this web site will help:
[http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

---

### Post by SavageBeginner on 2006-06-14
Here's the Ubuntu Wiki Page on the subject:  [https://wiki.ubuntu.com/LinuxFilesystemTreeOverview](https://wiki.ubuntu.com/LinuxFilesystemTreeOverview)

---

### Post by zxee on 2006-06-14
A great resource on things linux/unix is [www.linuxquestions.org](www.linuxquestions.org)
I believe the short answer to your question is that compared to the propriatary OSes you mentioned unix and therefore linux was designed so the everything you encounter is a file. In that manner everything was suppose to be transparent to the user. Of course in actuality it's not as simple as that but that's what I've understood from reading about the design concept.

---

### Post by Nephilim on 2006-06-14
@johnc4510
@SavageBeginner

Thanks, those look more like they answer the "what" of my question, but not the "why".  I'll certainly read them though, when I get home from work.

@zxee

Yeah, I've cruised through LinuxQuestions before, usually when trying other distros.  I'll cruise through there again and see if anything pops up.

I guess the main reason I ask this is two-fold.  Obviously I want to understand the OS better so that I can use it more effectively and feel less like I'm wandering around in a dark gymnasium with a single LED to light my way, but also just to understand why it is that way.  I know that someone (some people?) came up with the standard for the structure way-back-when and it has become defacto to the Linux community, but I'm curious to know if it could be changed, or possibly updated so that it cuts down the learning curve for new users.

Please understand that I'm not complaining about the way things are right now, it's just my curiosity talking.

What got me thinking about this is my iBook actually.  OS X is based off of BSD, which presumably started out with the same, or nearly the same, directory structure as Linux and Unix variants.  However, the directory structure in OS X is more easily accessible to the novice user, in that they don't have to wonder or spend time trying to find out what the /etc or the /bin directories are because all of that is hidden to the novice user (but still easily accessible to the more knowledgable users).  They just see /System, /Applications, /Users, /Library....only the directories that most day-to-day users need access to.

I can understand the want or need for transparency to the user, but I also wonder if it merely steepens the learning curve for novice users without serving any real purpose other than that transparency.

Again, please understand I'm not trying to start a flame-fest or anything, this is just my lust for understanding and my curiosity talking.  It is not intended seriously in any way other than to gain understanding. :)

---

### Post by SavageBeginner on 2006-06-14
[QUOTE=Nephilim]@johnc4510
@SavageBeginner

Thanks, those look more like they answer the "what" of my question, but not the "why".  I'll certainly read them though, when I get home from work.[/QUOTE]
I believe the directory structure is just base off of the "Filesystem Hierarchy Standard", established by the Free Standards Group.  I don't know of any documentation on the decision making behind it's development.  
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

