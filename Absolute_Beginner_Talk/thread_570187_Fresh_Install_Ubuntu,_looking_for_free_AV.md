---
title: "Fresh Install Ubuntu, looking for free AV"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-10-07
Any suggestions please? It must be free. The only thing I've installed right now is the Flash Player. ^_^ Thanks.

---

### Post by mindtrick on 2007-10-07
Antivirus? 
Try Clamtk

---

### Post by anjilslaire on 2007-10-07
ClamAV is free, but its highly unlikely you'll get infected. You're not in Windows anymore :) ...

It's in the repo's if you need it.

---

### Post by mindtrick on 2007-10-07
I've never seen anyone infected by a linux virus, btw.

---

### Post by LaRoza on 2007-10-07
The best AV is the user. I am using Windows (Vista) with no AV and feel totally safe, because I trust myself.

I consider myself invaluable :D, so that is technically not free.

---

### Post by equal on 2007-10-07
> **LaRoza said:**
> The best AV is the user. I am using Windows (Vista) with no AV and feel totally safe, because I trust myself.

I consider myself invaluable :D, so that is technically not free.

And if a worm virus enters through a security hole in your OS?

---

### Post by P4rD0nM3 on 2007-10-07
Ok ok, I know you guys are long time Linux users. I recently switched a couple of **hours** ago.

And seriously, I'm not used to not having an AV running in the background. I really am not used to it since the last time I did that on a Windows machine for an experiment...even without touching the Windows machine, as long as it's connected to the internet, it will eventually get a virus...even without a user touching the damn computer because of the os exploits.

So...uhm.

I install Ubuntu...be happy? I don't just open files and stuff. I'm not a happy click-here-click-there user.

---

### Post by mindtrick on 2007-10-07
I think there's no real-time scanner for Linux. You have to scan your system manually. I say install Clamtk (Gtk gui for ClamAV) from Add/Remove and scan your system once in a while.

---

### Post by P4rD0nM3 on 2007-10-07
So you don't run any AV too? LIke the one that runs in the background and checks to see if your files are still the same, someone looking at your ports, et. al.?

I'll be leaving my computer 24/7, isn't it unsafe not to have an av running in the background?

Sorry, please bear with me. I'm reading articles as we go too about Linux.

---

### Post by Faud on 2007-10-07
Here you go. AVG is actually what I used on XP when I had XP.

[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

Enjoy

---

### Post by mindtrick on 2007-10-07
Also there's a cool guide at [www.ubuntuguide.org](www.ubuntuguide.org) where you can find lots of info about installing software

---

### Post by mindtrick on 2007-10-07
> **P4rD0nM3 said:**
> So you don't run any AV too? LIke the one that runs in the background and checks to see if your files are still the same, someone looking at your ports, et. al.?

No I've never used an antivirus on linux. Never got infected, never heard anyone getting infected and I read a lot of linux stuff. 
You can install Firestarter firewall for firewall purposes.

---

### Post by P4rD0nM3 on 2007-10-07
I only see Aegis and ClamTK in the Add/Remove programs. There's no Norton? Stuff like that?

---

### Post by P4rD0nM3 on 2007-10-07
> **mindtrick said:**
> Also there's a cool guide at [www.ubuntuguide.org](www.ubuntuguide.org) where you can find lots of info about installing software

I'm reading it right now too. Thanks.

---

### Post by sstusick on 2007-10-07
The chances of you encountering a virus on Ubuntu are very slim. Though you could pass Windows viruses on to other users, without it affecting you. But the majority of viruses out there are Windows viruses so they are irrelevent on a Linux system.

---

### Post by Perfect Storm on 2007-10-07
AV is not needed :)
If you want to read more into the subject, I'll recommend you'll start here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bobplano on 2007-10-07
norton's proprietary and almost always costs money. you don't need one even if you leave your computer on, because the need to know your password to do any real damage to your OS. they can  get to your personal files, but you should be backing up anyway so that's not a HUGE problem.

---

### Post by Faud on 2007-10-07
> **P4rD0nM3 said:**
> I only see Aegis and ClamTK in the Add/Remove programs. There's no Norton? Stuff like that?


My AVG wasnt good enough ? :(

lol just playin'

yea, but seriously Ive never run an AV on Ubuntu and Ive never had a problem. I dont even really think about it

---

### Post by mindtrick on 2007-10-07
> **P4rD0nM3 said:**
> I only see Aegis and ClamTK in the Add/Remove programs. There's no Norton? Stuff like that?
Norton has a linux version but it's not free.

---

### Post by P4rD0nM3 on 2007-10-07
I just saw your post sorry. I apologize. I'm still overwhelmed a bit by the "You don't need it." answer.

Oh, it also made my old computer (2800+ AMX Athlon / 512MB / 80GB) really fast. Like a new computer.

---

### Post by P4rD0nM3 on 2007-10-08
> **Artificial Intelligence said:**
> AV is not needed :)
If you want to read more into the subject, I'll recommend you'll start here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Thanks. I'm still in the "Windows-mindset". :P

---

### Post by LaRoza on 2007-10-08
> **P4rD0nM3 said:**
> Ok ok, I know you guys are long time Linux users. I recently switched a couple of **hours** ago.

And seriously, I'm not used to not having an AV running in the background. I really am not used to it since the last time I did that on a Windows machine for an experiment...even without touching the Windows machine, as long as it's connected to the internet, it will eventually get a virus...even without a user touching the damn computer because of the os exploits.

So...uhm.

I install Ubuntu...be happy? I don't just open files and stuff. I'm not a happy click-here-click-there user.

Linux is quite secure, let it run and if you want, have a hardware firewall.

Even if you did randomly click everything in linux, it wouldn't do anything. Try this:

Make a file on Windows named "hw.bat", if you use notepad, use "Save As" and type the name in quotes. Put the line "hw" in that file, double click the file. Do the same in Linux, but use a ".sh" insead of ".bat", nothing will happen of consequence. Linux doesn't use the file extension to determine the file type, and more importantly, Linux will not execute a program or file without it being marked as executable. 

Most Windows exploits use those two features to attack the computer. If you set the file extensions ".vbs", ".wsh" and ".js" to open in a text editor, they will do know harm. The famed "I love you" virus was just a VBScript that Windows ran because of its file extension. Also, in Folder Properties, have Windows show know file extensions, so you know what the file is really.

---

### Post by P4rD0nM3 on 2007-10-08
Ok I'm going with this.

"My advice is to skip the anti-virus if you run Ubuntu."

Hooray Linux and Ubuntu, thanks guys.

PS: I actually installed openSUSE 10.3 first...but it's not really that newbie friendly to me.

---

### Post by Frak on 2007-10-08
You don't need an AV, ClamAV for Linux is actually used to scan Windows partitions and computers on networks.

But, YOU are the best AV, therefore, stick to the repos whenever you can. Make sure you get trusted GPG keys for the programs you get.

---

### Post by skipb on 2007-10-08
No need for AV, you may install firestarter for a firewall but that is all you should ever really need. You gotta love Linux.

---

### Post by JBAlaska on 2007-10-08
If you must have a AV proggy to feel at ease (I did when I first installed linux), try Avast for Linux. It's free and has a nice interface and auto updates.
```
http://www.avast.com/eng/avast-for-linux-workstation.html
```

But like the others mentioned...You prolly won't need it.

---

### Post by P4rD0nM3 on 2007-10-08
But it says the Ubuntu has a built-in firewall. Where can I go to for linux terminologies?

Does that Avast scan for linux viruses or it just scans for windows viruses that might be in a linux computer?

---

### Post by michaelzap on 2007-10-08
I like to scan my downloads because I do pass some of those files on to Windows users, and Windows users do connect to our network. I installed ClamAV and it works OK (it's slow and doesn't scan large files, however). Recently I tried out the free version of AVG, and I like it a lot better so far (it will probably be the one to make the cut in my new Gutsy install).

---

### Post by Faud on 2007-10-08
Do you mean firestarter ?

---

### Post by sstusick on 2007-10-08
I wouldn't use Norton if it were free, regardless of platform.

---

### Post by Frak on 2007-10-08
> **P4rD0nM3 said:**
> But it says the Ubuntu has a built-in firewall. Where can I go to for linux terminologies?

Does that Avast scan for linux viruses or it just scans for windows viruses that might be in a linux computer?
You're talking about IPTables, the default Kernel firewall. Firestarter is a GUI frontend to control it.

Feisty has some ports closed, and Gutsy has all ports open.

---

### Post by P4rD0nM3 on 2007-10-08
I see, thanks again! I like your quotation! I'm going to install Avast & Firestarter. Anything else to add?

---

### Post by Frak on 2007-10-08
> **P4rD0nM3 said:**
> I see, thanks again! I like your quotation! I'm going to install Avast & Firestarter. Anything else to add?
Care of what you install. Thats a BIG package that has no size.

Always be careful of what you install, because even though there are no documented malicious viruses or malware for linux, doesn't mean that it doesn't exist.

---

### Post by michaelzap on 2007-10-08
> **P4rD0nM3 said:**
> But it says the Ubuntu has a built-in firewall. Where can I go to for linux terminologies?

It does indeed, and if you want a GUI program to manage it install Firestarter.

> **P4rD0nM3 said:**
> 
Does that Avast scan for linux viruses or it just scans for windows viruses that might be in a linux computer?
Linux viruses?

---

### Post by P4rD0nM3 on 2007-10-08
Why isn't there one?

---

### Post by -grubby on 2007-10-08
you don't really need an antivirus.... I've been running without one ever since I started using Linux. check out the wikipedia article on linux viruses 
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)
but if you really want one, I would recommend Avast

---

### Post by Frak on 2007-10-08
> **nathangrubb said:**
> you don't really need an antivirus.... I've been running without one ever since I started using Linux. check out the wikipedia article on linux viruses 
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)
but if you really want one, I would recommend Avast
All of those have been created for competition and proof of concept, but new Linux Kernels have already filtered out the problems (usually in as little as a day).

Also, those don't really concern Desktop systems since they do not contain the necessary programs needed to run them.

---

### Post by justinmiller87 on 2007-10-08
> **sstusick said:**
> I wouldn't use Norton if it were free, regardless of platform.
Well, to be honest, I had two viruses that were kicking my butt hard. I being military get free copies of Symantec, Trend Micro, and McAfee scanners and all updates. I also use ClamWin.

ClamWin's most recent update didn't find one of them, and the one that it did find prior to this one it didn't do a full clean, so I still have a residue infection in registry entries that I can't seem to get rid of.

Symantec did find the virus that Clamwin didn't and did a full clean of the files it corrupted, not just the executable. So now I'm half-infected thanks to ClamWin and Symantec.

BTW, when I ran the ClamWin scan, I didn't have Symantec installed, so that's why it didn't find the first one.

Of all scanners I've used over the years, I would trust Symantec's any day. ClamWin/AV is good, but it has a long way to go to get to the standards set by the proprietary scanners.

---

### Post by michaelzap on 2007-10-08
For Windows machines, I trust Kaspersky more than any other anti-virus (although McAfee is a distant second).

---

### Post by thinkren on 2007-10-08
Timely question.  
I'm very new to Ubuntu as well.  I'm not worry much about viruses on Linux but this recent article makes me wonder about other malware that lurks on the net:

[http://computerworld.co.nz/news.nsf/scrt/CD0B9D97EE6FE411CC25736A000E4723]("http://computerworld.co.nz/news.nsf/scrt/CD0B9D97EE6FE411CC25736A000E4723")

Most of us are probably running desktops that are poor targets for those looking for servers to hijack.  But still I wonder about the vulnerability factor.  Although my installation is just a few days old, I've used it often enough to witness automatic software updates.  This inspires confidence in me with regards to how the folks at Canonical handle newly discovered bugs and exploits.  But for new guys like me, the default setting that come with a fresh install are the most cause for concern.  I'd like to assume that for example all unnecessary services are turned off by default, but in order to make Linux so user-friendly, what compromised did Ubuntu have to make?  I wish I knew enough to ask a good question but  my humble experience is so very limited.  I've heard about security auditing programs (I've heard of one called ?NMAP?) but operating one and understanding the results are probably beyond me.  Thoughts?  comments?

---

### Post by Perfect Storm on 2007-10-08
> **P4rD0nM3 said:**
> Why isn't there one?

Please read the link I provided earlier in this thread.

---

### Post by odzk on 2007-10-08
one advantage of ubuntu is not requiring AV. :)

---

