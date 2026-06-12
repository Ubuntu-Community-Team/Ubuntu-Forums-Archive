---
title: "Security - I'm Paranoid!"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Craftycorner on 2006-10-09
I got a very nasty trojan horse in Windows and am migrating to Ubuntu.  What should I obtain along with Ubuntu to keep me safe and secure in the jungle of script kiddies and virus bandits that is the net out there?  I set my update calander to daily.  I have Xandros in the box while I wait for my friend's Ubuntu discs to arrive in the mail...my burn was bad.

A Noob

---

### Post by lemonsCC on 2006-10-09
There are 0.01% the number of problems on Ubuntu that you experienced with Windows.  However, if you would like to keep the people you email safe you may want to check out Clam Antivirus.  Other than that sit back and enjoy Ubuntu.

---

### Post by wererabbit on 2006-10-09
Much like the Mac's OSX, the Root folder is inaccessible with Ubuntu without you personally going in and changing it.  This, plus the fact that Windows viri and spyware won't run under Linux/Unix really negates most need for antivirus packages.  However, if you feel you need one, I'd recommend using the one that comes with the Automatix install - it seems pretty good.  You'd be wiser to setup your firewall than waste time with an A/V program.  Just my two bits.

---

### Post by lemonsCC on 2006-10-09
Also [Automatix]("http://www.getautomatix.com/") will install this for you, among many other useful app, scripts, etc...


**EDIT:**
Grr...you beat me to the Automatix mention!  I am leaving this post as it contains the link.

Is firewall setup really necessary?  All ports show as stealthed on the numerous port scanners on the net.

---

### Post by lodravah on 2006-10-09
You also have the firewall included in the install, called "Firestarter." I'm not sure of its performance though, since I'm not using it.. :P 
A healthy degree of paranoia is good, i guess.. But Ubuntu is safer to use out there..

---

### Post by lemonsCC on 2006-10-09
There is a firewall in Ubuntu already it uses iptables.  Firestarter is just a GUI to iptables and unless you **_NEED_** to I would leave well enough alone.  *"If it ain't broke, don't fix it."*

---

### Post by aysiu on 2006-10-09
If you're paranoid:

1. Don't enable extra repositories.
2. Use the NoScript extension for Firefox
3. Don't install software not from the repositories
4. Create a strong (i.e., hard to guess) password
5. Don't click on links in emails

---

### Post by Malta paul on 2006-10-09
Welcome to Ubuntu.
I would install your Ubuntu on a clean formatted partition on your hard disk.
You should not worry too much about a virus in Linux. If you wish you can down load 'Aegis-virus-scanner' using system>administration>synaptic package manager when Ubuntu is installed. If you have problems just ask in this forum and you will get an answer for sure, good luck, paul

---

### Post by Craftycorner on 2006-10-09
I had to do a reinstall, wiping Windows from the hard disk.  Had a trojan on it.  So far, Avast says it's clean.  Of course, when the buddy's disk gets here (the disk and spare) I will reformat again.  I have Xandros in here...as the first Ubuntu burn attempt was bad.  But Avast won't scan some files.

---

### Post by emarkay on 2006-10-09
What about spyware???  Surely not every Linux developer has a shiny halo, and altruistic intentions.  

So wouldn't it be possible for some miscreant to write a program that keylogs, hijacks or installs unwanted (possibly invisible to the user) stuff that could, in the future, cause a good day to go bad?

Comments welcome

---

### Post by MiXor on 2006-10-09
cf aysiu's answer. Just take packages certified by Ubuntu -don't enable extra repositories- :KS 
And relax, doesn't this forum prove that a large proportion of the Ubuntu community is honest and ready to help? ;)

---

### Post by zappa on 2006-10-09
Sure, but since it's open source the villain would quickly be caught :p 
In the end it all comes to the user. 

Also install addblock as an extension in FF (if you trust them that is ;) )

---

### Post by bulldog on 2006-10-09
If you download from the Ubuntu repo's it's almost impossible to do such a thing.

Software will be tested and the source-code is available so if somebody should put a 'bad' program up for the repo's it will be detected.

If you download from 'not trusted' repo's you'll take a risk .

---

### Post by aysiu on 2006-10-09
Here's a comment: if you're that paranoid, don't install *any* software unless you've examined *all* the source code.

Don't want to learn to read source code and then examine it for every single piece of software you install? Then a certain degree of trust has to happen.

If you're only slightly paranoid, use only the repositories to install software. Don't install software from some random website.

---

### Post by picpak on 2006-10-09
You've trusted Ubuntu enough to download 700MB's from them and install it to your computer, but you're afraid to install their software?

---

### Post by aysiu on 2006-10-09
> **picpak said:**
> You've trusted Ubuntu enough to download 700MB's from them and install it to your computer, but you're afraid to install their software?
You put it more succinctly than I did.

---

### Post by haxer on 2006-10-09
Hmm.. i never tried a software for virus becuse it has never been a problem to me but the worst thing that could happen if you got an trojan or worm or virus is to just install it over but if you want to be safe why not download the virus remove software from ubuntu it self on automatix dont have to scared any problems just post them here and youll get tons of answers :)

---

### Post by Jareth on 2006-10-09
Just rely on your own common sense, it'll save space on your hard drive!

---

### Post by haxer on 2006-10-09
yeah :p

---

### Post by Craftycorner on 2006-10-09
Spyware makers pitch for the common denominator.  There's too many distros in Linux.  There's only one in Windows.

---

### Post by emarkay on 2006-10-09
**Good points all - Thanks.**

Remember some of us have been BURNED big in the Window$ world - and I claim to at least have a clue as to that area... (I remember Windows for Workgroups and even DOS3.1 before that!)  

So looking forward to no longer having to worry about having to reinstall a 3 page document's worth of software (in proper order), configurations, reupdate all the anti malware definitions, do a baseline Window$ update, update all other drivers not found on distribution disks or backups, and then remember where all my data file backups were (because I also had to format c: first), about once a year (on average) may offer a little awareness to those of you lucky enough to have never got trapped in that mire to begin with, why we may be making such insane run on sentences and repeating "Blue Screen of Death" in our sleep...  ](*,)

---

### Post by TheWizzard on 2006-10-09
here is what paranoid people can do: 

0) backup your files!!!
1) use Guarddog to configure your iptables. Guarddog starts with "nothing is allowed" and you have to explicitly give access for stuff you want to allow. guarddog is perfect for paranoid people. 
2) daily scan (cron) for rootkits with both rkhunter and chrootkit 
3) daily scan (cron) for virusses with f-prot

---

### Post by Craftycorner on 2006-10-10
> **TheWizzard said:**
> here is what paranoid people can do: 

0) backup your files!!!
1) use Guarddog to configure your iptables. Guarddog starts with "nothing is allowed" and you have to explicitly give access for stuff you want to allow. guarddog is perfect for paranoid people. 
2) daily scan (cron) for rootkits with both rkhunter and chrootkit 
3) daily scan (cron) for virusses with f-prot

Are these things free?  I'm sooo broke... are there free alternatives?  As in no $$ outflow?  I was burned bad by windows and now I'm cleaned out.

---

### Post by aysiu on 2006-10-10
Yes, those are all free.

---

### Post by ReaderRat on 2006-10-10
> **Craftycorner said:**
> I got a very nasty trojan horse in Windows and am migrating to Ubuntu.  What should I obtain along with Ubuntu to keep me safe and secure in the jungle of script kiddies and virus bandits that is the net out there?  I set my update calander to daily.  I have Xandros in the box while I wait for my friend's Ubuntu discs to arrive in the mail...my burn was bad.
Info on Clam AntiVirus [Here](https://help.ubuntu.com/community/ClamAV)  :rolleyes:

---

### Post by fragos on 2006-10-10
NoScript extension with Firefox is an excellent suggestion.  I get my firewall from a separate wireless router which also gives me the benifit of NAT and my own LAN.  No configuration required.  The two most important security measures are common sense and turn your machine off when you're not using it.  Remember broadband allways on = allways available for hacking.

---

### Post by az on 2006-10-10
Keep up-to-date with security updates.

---

### Post by jeanjo on 2006-10-10
Yes, update that is the answer. I have a question about updating. I have been doing it whenever the icon appears and tells me there are new updates available and have felt secure...but can someone tell me if I can authenicate that the icon came from ubuntu? It has worked beautifully so far but can someone highjack the system and send me a fake update icon?;)

---

### Post by po0f on 2006-10-10
Create separate /var, /tmp, and /home partitions.  Mount /tmp with noexec,nosuid,noguid,nodev.  Mount / and /boot read-only.  When you do go to update, do a dry run to see what will be installed and examine the changelogs to see what has changed.   If the changes are satisfactory, remount / and /boot rw, update, and remount ro.

Mount /home with [dm-crypt](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO).  If you're really paranoid, encrypt your swap partition and mount /tmp in a tmpfs and encrypt that also.   Choose a really good password.  Don't write it down.  Good password: Io2|v|ttm4y!bes!ih1t$t.!;  bad password: lol.

Make sure you're wearing an aluminum foil hat.  2-3 really good layers should do.

Or you could just use OpenBSD.

---

### Post by fragos on 2006-10-10
The only sources used for updates are configured in your machine.  If you're careful what sources you add that shouldn't be a problem.

---

### Post by TheWizzard on 2006-10-11
> **jeanjo said:**
> Yes, update that is the answer. I have a question about updating. I have been doing it whenever the icon appears and tells me there are new updates available and have felt secure...but can someone tell me if I can authenicate that the icon came from ubuntu? It has worked beautifully so far but can someone highjack the system and send me a fake update icon?;)

you can automate this updating with a script like this. 
that annoying update notification thing reminds me too much of windows. 

```
#!/bin/bash

apt-get -y update 
apt-get -y upgrade 
apt-get -y autoclean

```

---

### Post by TheWizzard on 2006-10-11
> **fragos said:**
> NoScript extension with Firefox is an excellent suggestion.  I get my firewall from a separate wireless router which also gives me the benifit of NAT and my own LAN.  No configuration required.  The two most important security measures are common sense and turn your machine off when you're not using it.  Remember broadband allways on = allways available for hacking.

a standard router firewall is not secure enough for paranoid people 8)

---

### Post by fragos on 2006-10-11
> **TheWizzard said:**
> a standard router firewall is not secure enough for paranoid people 8)

Point taken.  Nothing will satify the truely paranoid.  No system is 100% secure they only have different degrees of deficulty for a would be hacker/crimminal.  I for one favor common sense above paranoia.  Your trash and mail box are more worth worrying about.

---

### Post by manishk on 2006-10-11
Another related doubt:

Is Ubuntu completely free of viruses?? Isn't it actually easier to get a virus since we have to get all softwares from the net?

---

### Post by Perfect Storm on 2006-10-11
No. If you keep to the official source and Open Source you are then %99.999 save.

---

### Post by az on 2006-10-11
> **manishk said:**
> Another related doubt:

Is Ubuntu completely free of viruses?? Isn't it actually easier to get a virus since we have to get all softwares from the net?

No, actually having a centralised repository is a good thing.

None of the software in main and universe is uploaded there in binary form.  It is all source code packages that get built by the autobuilders and then added to the repos.

Now, probably not a whole lot of packaged are audited line by line by people looking at the source code, but it is very difficult to get the priviledges to upload into main or universe.  It is trivial for most people to check the source if they think something fishy is going on.

I doubt that any malware would last long in Ubuntu before being discovered.  As well, it would be pretty easy to find the author of it and take action.

So the fact that this is free-libre open source and all of the development happens at the souce code level does have significant advantaged for the simple user who is not a developer and wants nothing to do with reading the source code - just the fact that it is available and used by lots of people makes it important.

---

### Post by aysiu on 2006-10-11
> **manishk said:**
> Another related doubt:

Is Ubuntu completely free of viruses?? Isn't it actually easier to get a virus since we have to get all softwares from the net?
Sony put a rootkit on people's computers off a CD-ROM.

What difference does it make--net / not net?

What matters is whether the source is trustworthy or not. If you stick with the repositories, you'll be fine. And you're far more likely to find out if there's been a repository breach (highly unlikely but possible) than if some software from somewhere on the web that you Googled... has malware in it.

---

### Post by jeanjo on 2006-10-12
Re: Update
Thanks to everyone for the good advice  but I am wary of using the auto update code. Don't get me wrong; it's good code but I think I would rather have the option to look at the updates if I want. Trying not to be too paranoid, I will continue to update with the icon. Usually though I prefer to go to the source to download anything.

---

### Post by fragos on 2006-10-12
Ubuntu updates are automatically offered.  The user can uncheck any update they want to delay.  You're still in control.

---

### Post by devnulljp on 2006-10-12
You want bastille linux 
```
sudo apt-get install bastille

```
then run it:
```
sudo Interactivebastille

```
In addition to hardening your box it will also teach you a bunch about security

---

### Post by sumguy231 on 2006-10-12
> Usually though I prefer to go to the source to download anything.
But the repositories are the source. :)

---

### Post by TheWizzard on 2006-10-13
> **devnulljp said:**
> You want bastille linux 
```
sudo apt-get install bastille

```
then run it:
```
sudo Interactivebastille

```
In addition to hardening your box it will also teach you a bunch about security

didn't know this. thanks man! :KS

---

### Post by viper on 2006-10-13
Another thought is if you have an old P2 sitting around gathering dust and want some good security, down load Ipcop from here [http://www.ipcop.org/](http://www.ipcop.org/)
and put that old box to some good use. The site has a wealth of info check it out. Great firewall and fully customisable, and best of all its linux and free.;)

---

### Post by Craftycorner on 2006-10-16
Around here, bad source code stands out like a boiled egg in a blood hound kennel.  :twisted:

---

### Post by CaveRat on 2006-10-16
> **fragos said:**
> NoScript extension with Firefox is an excellent suggestion.  I get my firewall from a separate wireless router which also gives me the benifit of NAT and my own LAN.  No configuration required.  The two most important security measures are common sense and turn your machine off when you're not using it.  Remember broadband allways on = allways available for hacking.

If I want to leave my machine running while I'm gone, I disable eth0. This has been a very good learning thread. Thanks for all the info guys.

---

### Post by Craftycorner on 2006-11-03
Of course I still run virus scans, catching WINDOZE viruses in my email, and getting rid of them cuz I'm a good...kind netizen for my Windows friends.  We all should take pity on the Windoze, and catch the bugs for the Windoze people...:(

---

