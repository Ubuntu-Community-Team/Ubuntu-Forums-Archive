---
title: "Anti-Virus/Spyware/firewall programs for linux??"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-07-07
Hi would anyone know some really good quality products for protecting your linux box against viruses, spyware and a good firewall program??? It doesn't have to be free, I just want the best. Thanks

---

### Post by regomodo on 2007-07-07
firestarter is a good firewall for ubuntu. I think it may be in the repo's

---

### Post by 5-HT on 2007-07-07
In terms of spyware protection: I'm not aware of any, but it's not really a concern at the moment (arguments will be abound as to whether it'll ever be needed, but  I don't like to say 'ever'-- and it all comes down to user permissions).

As for anti-virus, it's the same argument: Your only concern would be for the permissions of the user infected...however, there are VERY few *nix viruses in the wild. Compared to Windows, they are *practically* non-existent (but not *totally* non-existent). IMHO, the biggest concern would be spreading viruses to users of other operating systems.
I personally like to use f-prot for linux. Many others are available (AVG may be familiar, clamav, panda...etc).

If you like a GUI anti-virus, xfprot provides a nice GUI front-end to f-prot.

---

### Post by robertc36 on 2007-07-07
Have a good look around the forums you will find plenty of info on why you do not need any of these apps.
Why bloat your system when you do not need too.

---

### Post by mytwobears on 2007-07-07
There is Avast! Antivirus Workstation for Linux, which is free.  AVG also has a Linux version of their Antivirus, which is free as well:

[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl") 

[http://www.avast.com/eng/avast-for-linux-workstation.html]("http://www.avast.com/eng/avast-for-linux-workstation.html")

---

### Post by regomodo on 2007-07-07
this article seems good

[http://www.linux.com/feature/55319](http://www.linux.com/feature/55319)

---

### Post by smoker on 2007-07-07
there's no need for antivirus and antispyware apps on linux, but if you feel the need, have a look in the repositories.

iptables is a built in firewall in ubuntu, and there is a gui available for this called firestarter,

---

### Post by nite owl on 2007-07-07
Hi thanks for your suggestions, does that make Ubuntu a little bit more safer then other distros due to the sudo command? and how you never really have admin permissions until you sudo??

---

### Post by RomeReactor on 2007-07-07
Hi. I don't think there's any need to have an antivirus on Ubuntu; that is, unless you regularly transfer files from your Ubuntu system to windows systems, and you want to make sure the files are clean for those systems. Personally, I like [ClamAV]("http://www.clamav.net/download/") and [F-Prot]("http://www.f-prot.com/download/home_user/download_fplinux.html"); both are command line scanners, and I find them to be very good. You can find ClamAV through Add/Remove or Synaptic, or from the command line:
```
sudo apt-get install clamav
```
ClamAV has a couple of graphical frontends: ClamTK (goes better if you're using Gnome) or KlamAV If you're on KDE (Kubuntu). There's also Aegis in the repositories, but I haven't tried it.
EDIT: Wow... Too slow...

---

### Post by ugm6hr on 2007-07-07
I don't use any antivirus at present on Xubuntu, although I do occasionally boot into Windows.

I'm not too worried about the risk of transferring a virus to my XP partition, because I don't open any external files on XP anyway.  It is purely for synchronising with my WM5 PDA (for database backup rather than diary / contacts if anyone is confused).

My question regards my Phone / MP3 player:
The SonyEricsson website advises I use antivirus on my W810i phone/mp3.  I synchronise with Banshee (from Xubuntu), or copy files directly on to the Memory Stick, without antivirus software.  

Am I jeopardising my phone by doing this?  Do I need antivirus?

Sorry to borrow this thread - but the discussion seems to be heading this way anyway.

---

### Post by jbaloul on 2007-08-09
This mite answer some of your questions...
[http://howtoforums.net/viewtopic.php?t=549](http://howtoforums.net/viewtopic.php?t=549)

JB

---

### Post by anewguy on 2007-08-09
Think a little outside your box regarding anti-virus:

If you have ever received a virus via email, then even though Linux may at this time be safer than Windows, think of your friends, family, etc., that you may forward emails to who still use Windows.  Do you want to forward a virus to them just because Linux didn't get hurt by it and you had no anti-virus running?

This is just one point overlooked by those who say you don't need it in Linux - maybe your machine didn't get infected because the virus was written for Windows, but why pass it along?

:)

---

### Post by asmoore82 on 2007-08-09
> **anewguy said:**
> Think a little outside your box regarding anti-virus:

If you have ever received a virus via email, then even though Linux may at this time be safer than Windows, think of your friends, family, etc., that you may forward emails to who still use Windows.  Do you want to forward a virus to them just because Linux didn't get hurt by it and you had no anti-virus running?

This is just one point overlooked by those who say you don't need it in Linux - maybe your machine didn't get infected because the virus was written for Windows, but why pass it along?

:)

an attachment of any kind sticks out like a sore thumb and I would not send one unless
I knew what it was. And I do hope that every Windows machine in the world catches
every possible virus!! my Friends/Family will be converted to Linux.

P.S. Is windows really so pathetic/important that you have to slow down linux machines with useless software to protect it?

---

### Post by misfitpierce on 2007-08-09
Antivirus for linux is used to stop the spread of windows viruses to windows machines from your computer. They cant affect your machine directly so dont worry about antivirus... Antispyware not needed either. Firewall could be a good idea on any OS.... Try firestarter

---

### Post by oilchangeguy on 2007-08-09
> **misfitpierce said:**
> Antivirus for linux is used to stop the spread of windows viruses to windows machines from your computer. They cant affect your machine directly so dont worry about antivirus... Antispyware not needed either. Firewall could be a good idea on any OS.... Try firestarter

just a quick tip. firestarter is NOT a firewall. it's simply a gui for iptables, the already built in firewall, for ubuntu.

---

### Post by stmiller on 2007-08-09
> **oilchangeguy said:**
> just a quick tip. firestarter is NOT a firewall. it's simply a gui for iptables, the already built in firewall, for ubuntu.

just another quick tip, K3B is NOT a cd burning program. It's simply a gui for cdrecord and other commands.

etc., etc., etc.

---

### Post by oilchangeguy on 2007-08-09
> **stmiller said:**
> just another quick tip, K3B is NOT a cd burning program. It's simply a gui for cdrecord and other commands.

etc., etc., etc.

thats nice, but don't think this thread is about a cd burning program.

---

### Post by anewguy on 2007-08-09
> **asmoore82 said:**
> an attachment of any kind sticks out like a sore thumb and I would not send one unless
I knew what it was. And I do hope that every Windows machine in the world catches
every possible virus!! my Friends/Family will be converted to Linux.

P.S. Is windows really so pathetic/important that you have to slow down linux machines with useless software to protect it?

Anyone (and there are A LOT) that do not do the things you say - checking everything, hopefully having an anti-virus that will protect them, etc. - will continue to spread viruses.    Not everyone has friends/family like yours, nor should one assume that all Linux users are either.  With the push in the magazines for Ubuntu as a desktop replacement things are going to happen.  The thing is, think about being pro-active in more than 1 way.  To say installing anti-virus in Linux is just wasting computer time, you are wrong.  The vast majority of viruses, etc., are written for Windows because of its user base.  But guess what - there ARE Linux/Unix viruses out there.  Just saying the odds are.......... isn't thinking responsibly.  If your PC is slowed down by anti-virus software, you need a new machine.  I'm running a very basic laptop with only a Celeron M in it, and I have no problem.  So, "P.S. is windows really so pathetic/important that you have to slow down linux machines with useless software to protect it?" is a very immature thing to say.

---

### Post by stmiller on 2007-08-09
> **oilchangeguy said:**
> thats nice, but don't think this thread is about a cd burning program.

I was making fun of your post.

---

### Post by Paulmd on 2007-08-09
> **nite owl said:**
> Hi would anyone know some really good quality products for protecting your linux box against viruses, spyware and a good firewall program??? It doesn't have to be free, I just want the best. Thanks

Linux is (mostly) immune to viruses. However: it's role in the reproduction of viruses is not to be underestimated. It can be a carrier of infected files in email, and others. And therefor it can be the OS equivalent of Typhoid Mary.  Infecting other machines with an infection to which it is immune. As a courtesy to others on the internet, if you forward attachments you get in email, then it would be a good idea to at least get an email scanner.

The same goes for Mac Users.

---

### Post by Orbital75 on 2007-08-09
Out of all the Anti-Virus software which has been discuss ( ClamAV, AVG, ect ) what
company would you say has the most current and up to date Definition files?
My linux machine is on an internal LAN and I'd like to keep the others safe from
files I transfer as well as e-mail attachments to others.  Its just the right thing
to do.  I know who their going to call when their windows machine breaks.

---

### Post by Bakon Jarser on 2007-08-27
I'm new to linux so I don't have much to offer on the subject, but I happened to run across this article about linux antivirus programs and thought i'd pass it on.

[http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1](http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1)

---

### Post by Perfect Storm on 2007-08-27
Not needed if you are a regular linux user.


But if you must burn away some precious resources, knock yourself out:

[F-Prot Installation Guide](http://ubuntuforums.org/showthread.php?t=88357)

[Free AVG Installation Guide](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by Dark Star on 2007-08-27
> **Artificial Intelligence said:**
> Not needed if you are a regular linux user.


But if you must burn away some precious resources, knock yourself out:

[F-Prot Installation Guide](http://ubuntuforums.org/showthread.php?t=88357)

[Free AVG Installation Guide](http://ubuntuforums.org/showthread.php?t=136064)
Absolutely these s/w slow down system performance and in Linux we don't need av :)

---

### Post by Jimmyfj on 2007-08-27
There's currently no need to use any of those programs. The way Linux is build makes it virtually impossible to infect your system. If you use your common senses it'll be even harder to jack your system. Is your password policy complex enough you needn't worry at all. Just remember that the more complex your passwords are the more secure you make your system. Don't ever use just one password for everything. Make sure that you have a password for your root account and one or two more for use on the internet sites you visit, like your mail account, forums etc. and you'll be safe with Linux. 

Linux come with all ports closed, and if you are behind a router with a build in firewall that's all the security you need.

---

### Post by hyper_ch on 2007-08-27
> **anewguy said:**
> Anyone (and there are A LOT) that do not do the things you say - checking everything, hopefully having an anti-virus that will protect them, etc. - will continue to spread viruses.  Not everyone has friends/family like yours, nor should one assume that all Linux users are either.
Well, I don't use antivirus either... most people that fetch a virus can't be helped anyway... they just click everything they get sent to... so why should I slowdown anything because of their ignorance. Furthermore if someone actually wants to be virus-free, meaning getting rid of windows, I help them...

> **anewguy said:**
> With the push in the magazines for Ubuntu as a desktop replacement things are going to happen.  The thing is, think about being pro-active in more than 1 way.  To say installing anti-virus in Linux is just wasting computer time, you are wrong.
An AV is retro-active and not proactive. Once a virus gets known there will be quite quickly a patch for it. So what does an AV use if you have a patched system or if the AV does not recognize the virus?

> **anewguy said:**
> The vast majority of viruses, etc., are written for Windows because of its user base.  But guess what - there ARE Linux/Unix viruses out there.  Just saying the odds are.......... isn't thinking responsibly.
There's more to it than just the user base. How comes IIS gets hacked more often than apache? Apache has still the largest user base in webserver... the reason is simple. In windows if you can get a virus on the system you can sort of assume total control. On linux however, a virus will only have very limited capabilites (except the user is stupid beyond anything and runs root all the time).
There will be an increase in viruses for linux as the number of desktop users grows but Linux is totally different from Windows and a virus will never have the same impact.

> **anewguy said:**
> If your PC is slowed down by anti-virus software, you need a new machine. 
Like you have to get a new computer for every OS upgrade? Now that was a very immature thing to say. Even new machines don't need unnecessary stuff... otherwise wouldn't every linux server also be running a gui?

---

### Post by fastpakr on 2007-08-27
> **oilchangeguy said:**
> just a quick tip. firestarter is NOT a firewall. it's simply a gui for iptables, the already built in firewall, for ubuntu.

Correct in that it's a gui for iptables, but iptables is NOT enabled by default in Ubuntu.

---

### Post by euler_fan on 2007-08-27
One thing to think about is OSSEC-HIDS. It performs some systems checks for hacks/rootkits, lets you know if certain files change, watches your logs, etc. and generally keeps an eye on your system. With email alerts it takes most of the pain out of things like log reading, etc. VERY CUSTOMIZABLE too.

Since ClamAV is not running unless scanning using the standard configuration, the only time you'll see machine performance changes (if at all) is while scanning--just like any other AV. But since on-access scanning is not enabled by default, it won't be on all the time.

---

