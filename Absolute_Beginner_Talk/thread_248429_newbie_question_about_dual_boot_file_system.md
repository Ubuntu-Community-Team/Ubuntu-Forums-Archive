---
title: "newbie question about dual boot file system"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-09-01
I am new to ubuntu/linux.  I have become fed up with windows xp vulnerabilities and attacks, but what made me start off on this journey was that it seems windows wants to be spyware now.  Anyway, I currently use several windows-only applications, so I don't want to entirely ditch windows.  Dual booting seems to be a really handy solution for what I want.  I am going to connect to the internet with both windows and ubuntu for several reasons, so both will be exposed to possible malware. 

I have created an additional partition which is fat32 so that both ubuntu and windows can easily exchange files with each other.  It is okay (well relatively speaking) if this "drive" is subject to no security, nothing important will reside there permanantly.  I don't mount the windows partition in ubuntu, and the ubuntu has whatever partitions the installation cd made for it, ext3 and swap and something else I think.

My stategy is that I want to isolate the two o/s from each other so that if one gets malicious attacks, the other will either be untouched or horribly obviously touched.  I suspect that the windows side gets attacks more often, so I'd save the important password stuff like ebay or paypal for ubuntu, and do the other stuff on windows.  

My question is how isolated are the two from each other?  I suspect windows malware could access the part of the drive that ubuntu uses, but probably would only be destructive and not plant some ubuntu spyware or virus.  Does windows have capabilities to read/write ubuntu file system?  And on the other side would an ubuntu malware be able to mount the windows partition and write something evil to the ntfs partition?

---

### Post by goatflyer on 2006-09-01
I think there are windows drivers that will let you read ext3 partitions from windows.  I also believe that after installing them windows may renumber (re-letter) the windows names for the partitions now seen on your hard drive.  This could cause some application links to stop working.

But without drivers, the worst a windows malware could do is format your hard drive, which wipes all OSes installed.

Ubuntu malware cant mount or format or anything without having your sudo password.  Once it has this, yes it could trash your windows setup.

Isolation is always relative.  The way you have yours set up already seems plenty good to me.  In order of increasing isolation, you could locate the two OSes on different hard drives, then on different computers, then putting the two computers on different lan segments, then in different rooms, then on different continents, then on different planets...

---

### Post by benfindlay on 2006-09-01
First of all windows can't even begin to register ubuntu's presence unless you install special software that allows windows to access the filesystem that linux uses. Without this software (called ext2fs I think) windows effectively registers your linux partitioned as rubbish. It knows theres something there, but doesn't have a clue what it is!

Ubuntu can access the windows partition if it's mounted and I wouldn't worry about doing that. linux can only read from ntfs. In order to write to it, you need special software installed, and by all accounts it's really buggy and not worth the hassle.

Linux doesn't suffer from the dangers of adware, spyware, viruses, malware etc. Sure, there have been viruses for linux (last time I looked, there were about 40 or 50 linux viruses, compared to a number above 60,000 for windows) but they mostly are concept viruses or viruses discovered in a lab(i.e. a they are discovered by developers and a security update is immediately released). Also linux is much more secure inherantly. It asks for your password whenever anything major happens on your system, so nothing can install without your permission!

Hope this helps!

---

### Post by new_foo on 2006-09-01
Yes, this answers my questions.  Thank you both.  I also appreciate levity.

---

### Post by benfindlay on 2006-09-01
No problems, and welcome to the club! ;)

---

### Post by anaconda on 2006-09-01
You might find VMWare interesting. ie. running windows in a virtual machine inside ubuntu...

I have such a setup, and in VMWare windows can't destroy anything from ubuntu.. actually windows thinks it has the whole hard-disk for itself...

Every other windows program runs fine, execpt games (fast graphics)

---

### Post by new_foo on 2006-09-02
I have the wine package, but I haven't got around to trying it out yet.  Is this similar to the program you are recommending?  If so which is better?

I was considering trying quicken with it.  There are two concerns I have about that since I don't have any background on how these linux programs will deal with these things.  What it is is that quicken does two things I find undesireable.   First it sets off my zone alarm saying it is trying to monitor my keystrokes and stuff.  Second it always asks to do things which would connect it to the internet.  It never has connected because I tell it I don't want it to, and zone alarm is instructed to not let it anyway, but if I run it under linux and I slip and press the wrong button and I don't have zone alarm to prevent it from sending out, that would be undesireable. Probably wouldn't hurt me, but it's the principle of the thing.

Anyway, how would the emulator handle the key logging thing?  Would it set up a "process" within the emulator only, which would go away when exited?

And assuming the emulator would let it connect, would fire starter have a way to set the firewall to block this?  Would this be a blacklist whitelist thing?

Thanks in advance

---

