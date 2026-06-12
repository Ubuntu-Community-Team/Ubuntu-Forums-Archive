---
title: "Virus software?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Bombdogs on 2007-01-24
A reply to my other thread prompted me to think about this as I haven't seen anything about it at all. Strange.

Do you need anti-virus software for ubuntu? Is it built in? Or don't hackers bother with it? What's the story? I have a hardware firewall but I'm also interested in whether this would be needed if I didn't have one.

Many thanks,

PMF

---

### Post by meng on 2007-01-24
Simply put, you don't need it. Generally, anti-virus software on Linux is used to protect any Windows machines that may connect to it.

---

### Post by oilchangeguy on 2007-01-24
95% of the worlds computers run windows, so the clowns who write virus's usually pick on windows. while it's not impossible to get a virus in linux it's just damn hard. when you set up ubuntu you should have been prompted to set up at least 2 user id's. the admin. id and a regular user id, as long as you use the regular user id (unless you need to perform an admin. function) there should be no problem with your computer contracting a virus.

---

### Post by houstonbofh on 2007-01-24
In most cases, a virus is a windows binary.  It will not run in Lunix.  (Might be able to get it working in Wine, but I doubt it)
> **oilchangeguy said:**
> when you set up ubuntu you should have been prompted to set up at least 2 user id's.
It does not do this in Hoary, Dapper, or Edgy.  And an Admin user still does not have system access unless the sudo password is entered.  You might notice that. :)

---

### Post by picpak on 2007-01-24
Using a firewall is good if you have a router; I do.

---

### Post by CCBalla10 on 2007-01-24
yea like these other guys said, you really don't need a virus protector.  Really no need for it.  Save the Hard Drive space for games! ;) like Enemy Territory!

---

### Post by lamego on 2007-01-24
There is no default antivirus installed and it is not required (yet), but please don't get a false sense of security.
It's technically possible to have a virus for Linux which can delete all your user's data or which can spread itself using your email client or using other techniques which are common to windows virus, virus do not need admin access for this "features".
Anyway the fact is there are no such virus yet, at least not on the wild.

---

### Post by k1001001 on 2007-01-24
If you're still wanting anti-virus software, AVG Anti-Virus makes a Linux version. You can download it [here]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5"). It is below the Windows downloads.

I doubt you'll need anything pertaining to anti-virus or anti-spyware or anti-anything on Ubuntu. Most malicious software is written for Windows, and it just won't run in Linux, even on Wine.

---

### Post by az on 2007-01-24
> **Bombdogs said:**
> 

Do you need anti-virus software for ubuntu? Is it built in? Or don't hackers bother with it? What's the story? I have a hardware firewall

Viruses are not the only vulnerability you can encounter.  Viruses are windows-only.  Since Ubuntu does not try to provide a stable binary interface (the software connects on a source code level and the distro provides the binary) and the implementation of most of the features is subject to change, instead of scanning for viruses and putting a band-aid on it, the vulnerability would be fixed.

The only thing you need to do is keep up-to-date with security updates.

A firewall is useless on a desktop machine.  Just don't run services that listen to the netwrok unless you need to do so.  By default, nothing in Ubuntu listens to the outside world.  If you want to install something that does, you will have to open up your firewall anyway - what's the point?

---

### Post by Zzl1xndd on 2007-01-24
Gotta agree with most others here on this its not really needed, But I have Avast for linux on my machine. I have it to look out for the windows people I deal with everyday.  Really I only bother scanning my home directory as thats the only place I download things not in the repositories.

---

### Post by Canis familiaris on 2007-01-24
Linux being in heavy multiples more secure and prone to viruses does not require an Antivirus. Install a firewall like firestarter if you like.

---

### Post by bootslap on 2007-01-24
Like the other guys said an anti-virus is not usually required... however it is better to be on the safer side than regret later .... I have an AVG on my box... You can also protect yourself....

---

### Post by Zzl1xndd on 2007-01-24
> **bootslap said:**
> Like the other guys said an anti-virus is not usually required... however it is better to be on the safer side than regret later .... I have an AVG on my box... You can also protect yourself....

There is that also most of us do get/send/forward a lot of email to windows users so it is an act of kindness to look out for them I mean we dont wanna make it any worse then it already is for them.

---

### Post by Kemik88 on 2007-01-24
I don't mean to steal this topic, but which version of AVG would I need to download? There seems to be three different versions. Can I use apt-get?

Thanks.

---

### Post by oilchangeguy on 2007-01-24
just pick one they've all got the same version number, just probably different download sites?? just keep in mind that alot of people out here running linux are doing so on an older computer (meaning low cpu & ram power) and anti-virus software running in the back ground will use system resources that could be better used elseware. scan the forums and look how few cases of a virus getting into a linux computer that are posted.

---

### Post by Zzl1xndd on 2007-01-24
> **oilchangeguy said:**
> just pick one they've all got the same version number, just probably different download sites?? just keep in mind that alot of people out here running linux are doing so on an older computer (meaning low cpu & ram power) and anti-virus software running in the back ground will use system resources that could be better used elseware. scan the forums and look how few cases of a virus getting into a linux computer that are posted.

Avast only scans when you tell it too :) so that might be a good option.

---

### Post by oilchangeguy on 2007-01-24
scan is not the issue, does the program run in the background to keep a virus out?

---

### Post by Zzl1xndd on 2007-01-24
> **oilchangeguy said:**
> scan is not the issue, does the program run in the background to keep a virus out?

no it doesn't.

---

### Post by oilchangeguy on 2007-01-24
ok, that's fine, but doesn't that kinda defeat the purpose of having ANTI-virus software on the computer? it's to keep'em out, not find 'em after they get in.

---

### Post by Zzl1xndd on 2007-01-24
> **oilchangeguy said:**
> ok, that's fine, but doesn't that kinda defeat the purpose of having ANTI-virus software on the computer? it's to keep'em out, not find 'em after they get in.

Well im not worried about getting a virus myself, its more just to make sure im not passing things off to windows users.

---

### Post by oilchangeguy on 2007-01-24
just a thought. since you're using a virus scan & remove  program, and not an anti-virus program, does that mean that you scan your computer every time before you send an email to a friend with windows?

---

### Post by Zzl1xndd on 2007-01-24
just if im sending something with an attachment and only that one file.

---

### Post by homh on 2007-01-24
There are virus programs that have been written for Linux machines....mostly done as an academic exercise to show it is doable.  100 have been recorded, none are "in the wild".

Contrast that with 70,000  (thats a guess) that have been written for Windows machines.
It would be hard for a Linux virus to attack in the wild and to be spread.

---

### Post by The Joe on 2007-01-24
> **k1001001 said:**
> If you're still wanting anti-virus software, AVG Anti-Virus makes a Linux version. You can download it [here]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5"). It is below the Windows downloads.

I doubt you'll need anything pertaining to anti-virus or anti-spyware or anti-anything on Ubuntu. Most malicious software is written for Windows, and it just won't run in Linux, even on Wine.

One problem: That's an RPM, Ubuntu requires .deb packages. 

Going back to viruses, there aren't really any for Linux, there were testing lab viruses which have never been used. Not even Wine will make them work, yes Wine allows the use of Windows programs, but not Windows binaries (I think that's the right word for it) therefore a virus through Wine won't affect the system. So in plain simple words, as many have said before me: You won't need it.

---

### Post by Kemik88 on 2007-01-24
I think it's just because I've come from being a Windows user and using NOD32 to keep the viruses away, to coming to an environment where there aren't any viruses in the wild. It just doesn't feel safe not using an Anti Virus.

---

### Post by Zzl1xndd on 2007-01-24
> **Kemik88 said:**
> I think it's just because I've come from being a Windows user and using NOD32 to keep the viruses away, to coming to an environment where there aren't any viruses in the wild. It just doesn't feel safe not using an Anti Virus.

I get that man I felt the same way at first but it does pass. Really its not needed.

---

### Post by jldugger on 2007-01-24
> **oilchangeguy said:**
> ok, that's fine, but doesn't that kinda defeat the purpose of having ANTI-virus software on the computer? it's to keep'em out, not find 'em after they get in.

That would be nice, but the costs are quite high and nobody has offered a clean solution that kernel developers approve of. Furthermore, I'm not sure its possible to accurately determine whether a program is a virus or not.  

The approach you advocate, while incredibly common in Windows, is perceived with disdain by linux developers.  Real Time virus protection requires you to have some transparent kernel level interface, rather than a user program.  User programs (without a helper in the kernel) simply can't work against a sophisticated attacker.  Adding in some sort of recognition system into the kernel would be incredibly invasive and cause huge performance penalties. Moreover, new viruses are the most likely to successfully attack you, and the least likely to be caught by a scanner.

Linux systems come with a number of safeguards against attacks, and Ubuntu features many of them.  Viruses are primarily programs you run as a user that infect the system.  Unless you log yourself in as root, or provide your password to a virus, the system will be fine, but your user account, and everything you have access to could be hosed.  By not running as administrator, a huge vector for propagation is removed, and the system can recover without real time scanning.  This is why most unix attacks go after services that run as root (and why you should generally run as few as possible).  These attacks are usually called "worms." The distinction can be useful, but they're both important aspects of system security.  Worms send your programs bad data and trick them into running programs hidden in the data.  If the program was root, it's game over. It can suspend AV, add or remove kernel modules, chroot the av, all sorts of tricks.

**The things you can do that will likely improve security:**
* Update software daily, and make sure you have the security updates repositories enabled.  The most effective means of stopping worms is fixing the programs they attack.
* Turn off services you don't need.  Generally not a large problem with ubuntu, but sometimes people install goofy servers like telnet.
* Don't run as root / administrator.  Ubuntu encourages this through sudo and gksudo.  Vista will do the same I hear.
* Install harden.  Harden is an ubuntu virtual package that conflicts with software with known security flaws, so if a flaw is found but not yet fixed, a conflict is added and the server will be removed on next update. There's a whole host of related harden packages. Ubuntu packages this in universe, presumably because it takes some amount of effort to manage; uninstalled software will not return when fixed. 
* Turn on router firewalls.  If your home computer network has a firewall, I suggest you become friendly with it and learn how to open only the ports you know you need.
* Don't run software from the internet at large. I know this is a huge temptation, especially for stuff not packaged by Ubuntu.  But this is a huge problem looming in the distance of Ubuntu adoption. People are used to going to the internet, downloading software and installing it.  Firefox warns you, but its so common everyone ignores it.  If you can, stick with the ubuntu software repositories. They come with automatic updates, and verification of their identity.  It's also a lot harder to screw up an upgrade if you stick with ubuntu software.  If you do run software, be wary.  Most linux software is fine, but sometimes people get hacked, sometimes CVS gets hacked, and sometimes people are just malicious (see Sony's windows rootkit). Someone should probably write up a list flags for of identifying probable bogus software (requiring a script to run as root comes to mind as a flag).
* There are linux antivirus software tools out there, but don't use this as a safety net. All it takes is one miss and you're hosed.  

Finally, don't worry too much about it yet. Linux on the desktop is so obscure and diverse it's hard to write something that affects more than a few thousand potential people.  The only known viruses are academic proof of concepts that come with a virus uninstaller.  If your company or insurance or something requires an AV, just find something that satisfies the hoops and let the company worry about how they're going to get Vista ready -- I hear neither TrendMicro nor Norton works currently.

---

### Post by CoolFinalFan on 2007-01-25
WOW this is an awesome thread! Alot of info here!!

---

### Post by aysiu on 2007-01-25
My take:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by SomethingUniqueHere on 2007-01-25
If security is a big concern of yours, take a look in the repository for an application called Bastille ([http://www.bastille-linux.org/)](http://www.bastille-linux.org/)).  Not only does it harden your system, it teaches you a lot about system security along the way.  One thing to note though, bastille isn't anti-virus software, it just tightens restrictions on your system making it less prone to attack.

---

### Post by 3rdalbum on 2007-01-25
If you find attachments on your e-mail that you weren't expecting, don't open the attachments.

If Firefox opens a File Download window when you weren't expecting one, don't open the resulting file.

Don't install random crap from the Internet. Stick to the repos, or anything with source code provided (or that is supported by a well-known company, such as Skype, and only then download it directly from the manufacturer).

Together with Linux and your hardware firewall, you'll be very safe. If you're a bit paranoid (as some Windows users are, understandably) you could install AppArmour or SELinux, but they take some getting-used-to.

---

### Post by lamego on 2007-01-25
> Viruses are not the only vulnerability you can encounter. Viruses are windows-only. Since Ubuntu does not try to provide a stable binary interface (the software connects on a source code level and the distro provides the binary) and the implementation of most of the features is subject to change, instead of scanning for viruses and putting a band-aid on it, the vulnerability would be fixed.
Virus are not windows-only, the binary (in)compatibility of Ubuntu is not a virus stopper, there are plenty of scripting languages like shell scripting, python, perl which are stable enough and powerful enough to develop virus which can spread even across different distributions.

---

### Post by valkarin on 2007-01-25
Although I don't use it on my Linux box mysef, I do you Avast on my windows machine.  Great software and I have yet to get a virus on the Windows machine in over a year.

The Linux version scans automatically on Linux and provides realtime protection.  It is also absolutely free.  You can download it at [http://www.avast.com/eng/download-avast-for-linux-edition.html]("http://www.avast.com/eng/download-avast-for-linux-edition.html").

Let us know what you think of it if you decide to try it out.

---

