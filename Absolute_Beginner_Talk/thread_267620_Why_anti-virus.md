---
title: "Why anti-virus?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-28
I noticed that when you use Automatix to get applications one of them is AV along with a firewall. The firewall I can understand, but I thought one of the reasons to go to Linux was to get away from viruses.
I was just wondering about this and figured this was the place to ask.:confused: 
Larry

---

### Post by ewl1217 on 2006-09-28
There are Linux viruses, but they are very rare and not at all widespread. Most anti-viruses for Linux only search for Windows viruses. You can go ahead and install it if you're paranoid or don't want to pass along viruses to Windows users. Otherwise, you don't need to bother.

---

### Post by DarkN00b on 2006-09-28
Because, while it is highly unlikely you'll get one, there are viruses that can attack Linux boxes.

---

### Post by hyper7 on 2006-09-28
To add to what's already been said; You'd have to accistupidly run something you shouldn't have to get infected(in most cases).

---

### Post by Mimsy on 2006-09-28
Personally, I like that thought of running an AV, but that's because I shre a lot of files with the Windows PC in the house. While that PC has its own antivirus and a whole slew of security software, a little extra precaution never hurt anyone. So far, I just make sure to update the Clam AV whenever it wants to, and I understand that will be enough.

/Mimsy

---

### Post by brianC on 2006-09-28
"accistupidly"   my new most fravoristest word

---

### Post by Albi on 2006-09-28
Don't bother installing it...there are virtually no linux viruses, and most of them just target servers.  It will eat up a lot of ram in the background though, one of the reasons I don't use windows is having to run an antivirus, makes the computer much slower.

---

### Post by sbergman27 on 2006-09-28
> **HareBall said:**
> I was just wondering about this and figured this was the place to ask.:confused: 
Larry

For all intents and purposes, there *are* no Linux viruses.  If one wants to get pedantic about it, yes, there are some laboratory curiosities.

However, email more or less swims in Windows viruses, these days. (At least mine does.)  And scanning email makes some sense, just to avoid forwarding them to Windows using colleagues.

Frankly, I'm more worried about Firefox extensions, which are the perfect vector for trojans.

---

### Post by Kilz on 2006-09-28
> **HareBall said:**
> I noticed that when you use Automatix to get applications one of them is AV along with a firewall. The firewall I can understand, but I thought one of the reasons to go to Linux was to get away from viruses.
I was just wondering about this and figured this was the place to ask.:confused: 
Larry

One answer is because its often requested by people switching over from Windows. Sometimes newbies dont know that linux doesnt have a lot of viruses. They feel safer because they have always had one when running Windows. Not that they really need it.

---

### Post by Sef on 2006-09-28
> is there by any chance a list of programs that someone can show me?

Also you need it, if you run a mail client.  A virus won't infect your GNU/Linux system, but it can sit on top on the system and infect your friends who have Windows OSes.

---

### Post by WalmartSniperLX on 2006-09-28
> **Albi said:**
> Don't bother installing it...there are virtually no linux viruses, and most of them just target servers.  It will eat up a lot of ram in the background though, one of the reasons I don't use windows is having to run an antivirus, makes the computer much slower.

Amen, I hate windows and needing to run antivirus programs. In linux I dont see a point in needing an antivirus program, but it doesnt do much bad to get one anyway just to be extra safe :D

---

### Post by Kilz on 2006-09-28
> **Sef said:**
> Also you need it, if you run a mail client.  A virus won't infect your GNU/Linux system, but it can sit on top on the system and infect your friends who have Windows OSes.

Am I correct in thinking that you would have to forward attachments for your Linux install to infect Windows users?

---

### Post by aysiu on 2006-09-28
Can someone explain the technical details about protecting fellow Windows users from viruses?

The way I see it, there are only two ways you could be forwarding viruses to your Windows-using friends and family:

1. You are deliberately forwarding messages containing attachments that are infected, and you're not sure if those attachments are infected or not. Maybe you shouldn't be forwarding weird attachments you didn't create.

2. Your computer has been compromised and is being used as some kind of zombie spam launching pad. If this is the case, you probably have a lot more to be worried about than "forwarding viruses."

Am I missing something?

---

### Post by sbergman27 on 2006-09-28
> **aysiu said:**
> Can someone explain the technical details about protecting fellow Windows users from viruses?

Tell them to stop running Windows? :D 

But seriously, that's about it.  And aside from running an open mail relay, which Ubuntu users wouldn't be doing, I'd say that the zombie thing is pretty unlikely under Linux, or really anything *but* Windows.

So forwarding a messages with Windows attachments is probably the only significant vector.

For anyone interested, Evolution allows you to set up message filters which pass the mail to an arbitrary command.

So you can, for example, install clamav and set up a filter like:

Pipe to Program | clamscan | returns 1
Move to Folder | Viruses

I just composed this on the fly, so I could be missing an option or two to clamscan, but you get the idea.  If the appropriate archive tools (unzip, etc) are available, it will, I believe, automatically unzip the attachment, before scanning, but I'm not certain of that in this context.  My mail server clamscans on the fly, so I don't have a good way of testing.

---

### Post by hyper7 on 2006-09-29
> **Kilz said:**
> Am I correct in thinking that you would have to forward attachments for your Linux install to infect Windows users?

I can think of some screwed up but not likiely scenarios where one could get themself into trouble..

However, I've not seen the *nix virus that concerns itself with such utterly ridiculous circumstances.  There'd be little point in creating a virus that targeted a linux based mailserver and disguised itself in a windows coak..

Okay, now I sound totally retarded.  I suppose that was my intent.

---

### Post by Kilz on 2006-09-29
> **sbergman27 said:**
> Tell them to stop running Windows? :D 

But seriously, that's about it.  And aside from running an open mail relay, which Ubuntu users wouldn't be doing, I'd say that the zombie thing is pretty unlikely under Linux, or really anything *but* Windows.

So forwarding a messages with Windows attachments is probably the only significant vector.

For anyone interested, Evolution allows you to set up message filters which pass the mail to an arbitrary command.

So you can, for example, install clamav and set up a filter like:

Pipe to Program | clamscan | returns 1
Move to Folder | Viruses

I just composed this on the fly, so I could be missing an option or two to clamscan, but you get the idea.  If the appropriate archive tools (unzip, etc) are available, it will, I believe, automatically unzip the attachment, before scanning, but I'm not certain of that in this context.  My mail server clamscans on the fly, so I don't have a good way of testing.

But even if you don't set up the anti virus. If you just don't forward attachments (why someone would forward attachments they are not sure of is beyond me). You cant pass a virus to a Windows user.

> **hyper7 said:**
> I can think of some screwed up but not likiely scenarios where one could get themself into trouble..

However, I've not seen the *nix virus that concerns itself with such utterly ridiculous circumstances.  There'd be little point in creating a virus that targeted a linux based mailserver and disguised itself in a windows coak..

Okay, now I sound totally retarded.  I suppose that was my intent.
O ya, I don't think anything is fool proof. As soon as you say it is, some fool will prove you wrong. But its hard to pass a virus if you are following the common sense rule of don't forward attachments.

---

### Post by sbergman27 on 2006-09-29
> **Kilz said:**
>  (why someone would forward attachments they are not sure of is beyond me).

Unbeknownst to Sally, her resume, MyResume.doc is infected with a macro virus.  You're trying to get her a job at the firm where you work.  She sends you her resume.  You forward it to your boss.

---

### Post by po0f on 2006-09-29
You could also be running a mail server that Windows clients use.  A virus scanner in this situation would be beneficial.

---

### Post by aysiu on 2006-09-29
> **sbergman27 said:**
> Unbeknownst to Sally, her resume, MyResume.doc is infected with a macro virus.  You're trying to get her a job at the firm where you work.  She sends you her resume.  You forward it to your boss.
She sends you her resume as a .doc, and you save it as an .rtf file and send it on to your boss, or you save it as a .pdf file and send it on to your boss. Problem solved.

---

### Post by Mimsy on 2006-09-29
Good point, Aysiu. All the same, since I move files back and forth between the Ubuntu laptop and various Windows computers, some of which belong to either my college or the company that was kind enough to let me intern with them, I like having Clam AV running. :)

/Mimsy

---

### Post by spockrock on 2006-09-29
yeah I only run the virus scanners in windows.......

---

### Post by aysiu on 2006-09-29
> **Mimsy said:**
> Good point, Aysiu. All the same, since I move files back and forth between the Ubuntu laptop and various Windows computers, some of which belong to either my college or the company that was kind enough to let me intern with them, I like having Clam AV running. :)

/Mimsy
I wouldn't want to stop people from using anti-virus if they had particular circumstances (like yours), but as a general rule, it's unnecessary, and people should know that.

For security, it's best to not start opening some ports to "listen" (unless you know what you're doing), to use the NoScript extension in Firefox to block Javascript exploits (which seem to be most of the vulnerabilities Firefox has), and to just generally not click on things you don't trust or install software from fishy (or phishy) sources.

---

### Post by spockrock on 2006-09-29
is there phishy software for linux machines??

---

### Post by Mimsy on 2006-09-29
> **aysiu said:**
> For security, it's best to not start opening some ports to "listen" (unless you know what you're doing), to use the NoScript extension in Firefox to block Javascript exploits (which seem to be most of the vulnerabilities Firefox has), and to just generally not click on things you don't trust or install software from fishy (or phishy) sources.

What could those scripts do in Ubuntu? I installed NoScript before doing anything else in Firefox, mainly because I have used it for so long that I feel uneasy not having it installed, along with AdBlock, but more for peace of mind than because I believed there was a danger. Is there one, and if so, what is it?

/Mimsy

---

### Post by sbergman27 on 2006-09-29
> **aysiu said:**
> She sends you her resume as a .doc, and you save it as an .rtf file and send it on to your boss, or you save it as a .pdf file and send it on to your boss. Problem solved.

Yeah, I usually convert .doc to something else just on general principles unrelated to security.

Personally, I have our company's mail server set up to filter both incoming and outgoing with clamav-milter, so I don't really think about local scanning my mailbox, which is imap anyway.  (And truth be known, I can't bring myself to feel too terribly responsible for people running Windows XP Security Sieve Edition.  But hey! [-(  )

---

### Post by aysiu on 2006-09-29
Well, the vulnerabilities actually get patched, but before they do, they're usually Javascript-related; for example, [this one](http://secunia.com/advisories/21906/).

---

### Post by HareBall on 2006-09-29
How do I get Clam to run? I installed it, but now I can't find it.
Larry

---

### Post by blx_286 on 2006-09-29
> **sbergman27 said:**
> Unbeknownst to Sally, her resume, MyResume.doc is infected with a macro virus.  You're trying to get her a job at the firm where you work.  She sends you her resume.  You forward it to your boss.

There should be a mail server or two in between to strip it out. And Sally is also not assuming personal responsibility for her computer or data, but that's probably another thread.

Probably not a good analogy, but your car has airbags and seatbelts, but neither one of those will prevent a wreck. The user has to step up to the plate sometime.

I would hazard a guess that as Linux takes hold, you will see more virus'. Hopefully Linux won't be dumbed down and everything integrated enough that things just run unknown to the user (like one of those other OSes).

Of course, your mileage may vary...

---

### Post by petri on 2006-09-29
> **HareBall said:**
> How do I get Clam to run? I installed it, but now I can't find it.
Larry

Try this [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by nudnik on 2006-09-29
> **brianC said:**
> "accistupidly"   my new most fravoristest word

I feels very crose to you right now, at thow we was bestest frends.:-\"

---

### Post by Mimsy on 2006-09-29
> **aysiu said:**
> Well, the vulnerabilities actually get patched, but before they do, they're usually Javascript-related; for example, [this one](http://secunia.com/advisories/21906/).

That makes seense. I now consider myself educated on the subject. :)

/Mimsy

---

