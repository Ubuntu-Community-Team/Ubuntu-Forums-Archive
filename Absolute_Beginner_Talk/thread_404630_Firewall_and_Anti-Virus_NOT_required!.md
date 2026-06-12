---
title: "Firewall and Anti-Virus NOT required!"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Gif on 2007-04-08
Hi

OK following on from my first post: 
[http://ubuntuforums.org/showthread.php?t=402096]("http://ubuntuforums.org/showthread.php?t=402096") (thanks to all the help and comments)

I've installed it! - Xubuntu went on reasonably easy via the alternate CD and seems to have detected all the hardware correctly (I hope).

Everything about Xubuntu seems so clear and uncluttered and looks like being ideal for my project - I'm impressed.

Two more questions I would like to ask at this stage are;

**1)** I'm a totally Linux newbie and can't get my head around Firewall and Anti-Virus NOT required. Can somebody confirm this as it seems so risky or have i been using windows to long -  will it be safe as a web browser with possible transactions taking place by family members?

**2)**  When browsing certain sites - firefox does not handle media clips / trailers etc - what do I do to make them play within the web page?

Many Thanks

---

### Post by LaRoza on 2007-04-08
To quickly answer your questions, Anti Virus software is not required. Ubuntu comes with a firewall, Xubuntu probably has one too, but you do not need to use it.

Your browser needs the plugins for certain media. I can not help you further with that, go to 

 [https://addons.mozilla.org](https://addons.mozilla.org)

You do not need antivirus software because of many reasons but the simplest reason is no one writes viruses for Linux because it is not worth it. Any security concerns are fixed very quickly and freely after they are discovered.

---

### Post by xopher on 2007-04-08
> 1) I'm a totally Linux newbie and can't get my head around Firewall and Anti-Virus NOT required. Can somebody confirm this as it seems so risky or have i been using windows to long - will it be safe as a web browser with possible transactions taking place by family members?

Correct. But you actually do have a firewall enabled by default, so you're safe ;)

> 2) When browsing certain sites - firefox does not handle media clips / trailers etc - what do I do to make them play within the web page?

You install a plugin for firefox, eg. totem-mozilla or mozilla-mplayer :

```
sudo apt-get install totem-mozilla
```

---

### Post by xpod on 2007-04-08
If you need simple gui access to the firewall settings for any reason then install the "firestarter" frontend for it from the repo`s.

It`s a bit easier to get the head round than iptables itself me thinks:)

---

### Post by LaurelLynn on 2007-04-08
Dear Gif,

The reason Ubuntu has no firewall or anti-virus by default is two-fold:

1. Ubuntu ships with no open ports.  A firewall stands between your ports and outsiders. Putting a firewall on would have been like boarding up the doors of a house with no doors.

2. As of now (knock on wood) the only Viruses for linux exist in labratories.  If they were out there, they usually need the root password to spread.

That aside, when you start installing things from the repositories you might grab applications that run servers.  SSH probably doesn´t need a firewall IF you follow a guide that tells you how to generate unique key.  Samba on the other hand assumes your trust the machines next to you.

So, a firewall such as Firestarter becomes a good install once you start using networking to do more than browse the internet.

You can also install anti-virus software such as clamav.  Their main purpose though, seems to be scanning Windows mail and partitions.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-08
>  The reason Ubuntu has no firewall or anti-virus by default is two-fold:the firewall is installed and ON by default in ubuntu. 
did you mean that a firewall *frontend*(eg firestarter) is not installed by default?

---

### Post by LaurelLynn on 2007-04-08
ComplexNumber,

Quite right. I tend to think of iptables as being more a network configuration (NAT, ...) with firewall capabilities than as a firewall in itself.

Actually it is more powerful, but not for the faint of heart.

---

### Post by Gif on 2007-04-08
I did not know that a Firewall was installed by default!

Thanks again for all your help and advice! =D>

---

### Post by in_flu_ence on 2007-04-08
In fact, I feel very safe with the default. You probably won't see many (if not none) post concerning about virus attack in this forum 'cause things are pretty much in safe hands.

Just not too sure if we can get virus through wine/crossover office etc since the topic pop up.

---

### Post by Tundro Walker on 2007-04-17
Cool!  I read other threads about needing to d/l a firewall, but they were a bit confusing and vague.  Then I read your reply about the firewall already being installed an ON (what a concept), and got the "firestarter" front-end to check it out.  Awesome!  Thanks!

On a side note, I think folks using Cross-Over Office and Cedega are still safe from Windows viruses.  It falls into the category of "why can't Windows applications run on Linux?", in that the virus would have to be altered to run on Linux in addition to Windows in order to penetrate the base Linux machine running COO or Cedega.

Some folks, using VM (Virtual Machine) to install Windows on top of a Linux base, have had instances of their VM getting a Windows virus.  But, VM's are usually ran in a "cell" like setting, meaning they're running in their own virtual computer, so infection to the main computer should not occur.  If the VM gets infected, they can just wipe it and set it up again, without harm to the main computer.

It would take a pretty smart and industrious person to write a virus that was cross-platform compatible.  Well...let me say that differently...  A lot of programmers already complain about how difficult it is to sometimes do cross-platform compatible software (that isn't web-based).  With the kind of skill it would take to make a Windows virus that could also infect Linux, and bypass the security measures of VM machines and Linux in general...   A person with that skill usually isn't wasting their time making stupid viruses that just destroy things carte blanche.  A person with that skill is usually already employed, either with a legitimate company getting paid tons of money as a security expert, or in illegitimate fashion to do virual breaking-and-entering of computers to do stuff without being detected.

Most viruses these days come from script-kiddies messing around to learn or just wanting a power trip.  And, regretablly (or thankfully...take your pick) they're focused on making Microsoft's life miserable (IE: take down "the establishment").

Only thing I could think of that might pose a risk would be a Windows virus that actually infects the Master Boot Record (MBR) of the computer.  I think a person would have to be running a Windows VM, and have it set somehow to have full access of the computer, and then the virus would execute in the Win VM environment and attack the physical MBR.  Or maybe one that attacked the BIOS (?).

---

### Post by jpmswiss on 2007-04-17
I am also a Linux n00b.

It is assuring to know that ubuntu appears to be "safe".

Everyone in this community is soooo friendly!

---

### Post by freebird54 on 2007-04-17
If anyone wants a more in-depth look at the problems facing a virus on Linux, here is a link that discusses that: [http://linuxmafia.com/~rick/faq/index.php?page=virus#virus](http://linuxmafia.com/~rick/faq/index.php?page=virus#virus)

Kind of interesting.  The author put out a challenge for people to TRY to infect his machine - it is included in the above post...

Basically - ***IF*** the writer is clever, and ***IF*** he guesses right about your configuration, and ***IF*** he is good at social engineering, and ***IF*** he gets you do something unwise (like upping yourself to root status and executing unkown code) **THEN** it ***MIGHT*** work -but it still would not be able to spread very well, or far.  For one thing - what are you running for an email prog - it won't be Outlook! And **none** of the Linux emailers will run attached code....

---

### Post by airtonix on 2007-04-17
linux catching a windows virus is like a metal-robot catching malaria from a human. 

Cant be done becuase malaria doesnt know how to corrupt and digest metal.

Doesnt mean viruses for linux wont exist in the future, especially if all the apathetic-lazy people in the windows world start using linux and just install software from untrusted sources.

autopackage behaves in a way that allows this to occur in the future, its only a matter of time.

windows virus need to be : 

1 - small. tiny infact...
2 - undectable, which means usually they reassemable themselves from some "apprent-garbled-mess" upon activation.
3 - coded in an effcient and lean manner, which usually means assembler.

Points 1 and 3 and the Revolutionary-Aspects that Tundro Walker expresses are the reasons why 99.999999%  of the time a virus written for windows wont and cant execute inside a linux enviroment. the assmebler code is targeted at windows and since it has to be small and tiny and undectable, it wont be able to bloat it's size and decisions by including assmebler code that targets more than one enviroment.

But this doesnt actually rule out "viruses-for-linux" per-se. really all it takes is an ignorant user to run a malicous script that requests sudo priveldges under the guise of doing some happy-fun-world-reward-scenario. but then it would actually require more than one user for this to propagate round the world.

the best thing linux did to me was sudo. making me sudo admin privledges to myself for all mission-sensitive operations.....it really changes your frame of thought and keeps you from dozing off (get it? dozing on windozer. hur hur)

---

### Post by juantovarm on 2007-04-17
For firefox to play videos i suggest:

[https://addons.mozilla.org/es-ES/firefox/addon/446](https://addons.mozilla.org/es-ES/firefox/addon/446)

---

### Post by Sef on 2007-04-17
> Most viruses these days come from script-kiddies messing around to learn or just wanting a power trip.

Script kiddies don't make most of them any more.   Most malware comes from people,  including those in organized crime, wanting to make money.   Easy way to make money illegally, and in some countries the penalties are light.

---

### Post by frodon on 2007-04-17
BTW just to bring more insight on the firewall question.

The firewall in ubuntu is the common firwall included in all 2.4 and 2.6 kernel series called netfilter which is one of the most powerful firewall (for me just the best ;) ), then the standard language used to configure netfilter is iptables and finally there are some GUI fronted to generates easily iptables rules like Firestarter.
By default ubuntu and linux in general is safe because even if a user come on your computer he will have no rights, in general you just need a firewall with linux when you run services.

---

### Post by Tundro Walker on 2007-04-18
> **airtonix said:**
> Doesnt mean viruses for linux wont exist in the future, especially if all the apathetic-lazy people in the windows world start using linux and just install software from untrusted sources.


Hehe, I got to thinking about this, and checked over the replies to see if somebody mentioned that before I did.   What you said is pretty much the house of cards for Windows and Linux.  There's tons of .exe software on the net for Windows, and lots of folks d/l it for whatever reason (to tweak their comp, to get some app for free, etc).  Some of those, come to find out, are spyware or adware.  Some could be viruses in disguise.  Not to say there aren't legitimate folks out there producing great stuff for the common good.  But there's just as many (if not more) folks with alterior motives.

And you're right, the coolest thing I've liked about Linux is the Apt-Get package managment systems.  But, I, like others, use non-Ubuntu repo's.  Anyone of them could have something on it that contains malicious code.  And all it would take is some appetizing description (like "ultimate computer tweaker!  d/l this to unlock secret settings in Linux to double your speed!") for me to d/l it faster then a hog in heat.  

Folks have gotten wise to email attachments, but a lot of us are still pretty gullible to "free software".

A friend of mine and I thought the best virus attack in the world would be somewhat like a magic trick.  You think you're watching the hand that's performing the trick, then *WHAM!*.  

Our idea was that someone would have to create a virus hoax, or perhaps even a real, but not very dangerous virus.  Folks would be prompted to go to their anti-virus sites to d/l a special package to eliminate this.  However, the virus attackers have hacked into the anti-virus site and replaced the "cure" file with the actual virus file they wanted to infect people with.  Folks d/l it, and they think they're curing their computer, but are acutally infecting it with the real slammer of a virus.  This would only work on the folks who don't run anti-virus to begin with, because folks who do usually use a package with secure d/l from antivirus servers.  But those folks that rely on "freebies" from Symantec's web-site and such...it'd be disasterous, partly depending on how fatal the virus is, but mainly if an antivirus software company was found to be unknowingly propogating a virus because they got hacked into.

The liklihood of that scenario actually occuring is probably 1:1,000,000,000,000, because antivirus software companies are (should) be pretty tight with security.  But, if it did happen...wow, the media would go ape.

---

### Post by singedwings on 2007-04-21
I agree that linux is pretty safe from viruses at the moment, and that it could potentially be attacked more in the future.

However if you transfer files to a windows computer or forward tons of emails to friends it should be your duty to ensure that those files are virus free.

---

