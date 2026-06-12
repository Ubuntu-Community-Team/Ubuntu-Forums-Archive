---
title: "Upgrading from 6.06 to 6.10"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by groucho22 on 2006-10-26
Hi all,

I'm quite new to ubuntu. I've had Ubuntu 6.06 installed on my laptop for about two months and I've installed all the updates that the Upgrade Manager has shown. I would like to know if I have to do anything to upgrade to 6.10 or  if, as I've installed all updates, I am already at 6.10 or if the upgrade to 6.10 will appear in the Upgrade Manager.

Thanks,

g

---

### Post by petersjm on 2006-10-26
EDIT: See other posts in this thread for ways to upgrade.

---

### Post by groucho22 on 2006-10-26
Thanks!

And, if I use the CD, I will be able to upgrade and not install 6.10 from scratch overwriting everything I have installed and my data?

g

---

### Post by timetunnel on 2006-10-26
You can upgrade to 6.10 without downloading the CD. Here's a manual in the the ubuntu wiki:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by J77 on 2006-10-26
> **petersjm said:**
> You'll have to download the new CD image. Upgrades do not, AFAIK, give you the option of upgrading to Edgy.but that's how the upgrade from breezy to 6.06 was made :confused:

---

### Post by CupofDice on 2006-10-26
You have to download a cd to get edgy.

edit-yeah, got rid of it.

---

### Post by PriceChild on 2006-10-26
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) will explain things to you.
 
Please remember that edgy is still "edgy". Dapper will be supported longer and is meant to be more stable.
 
> **CupofDice said:**
> I don't think you have to download a cd to get edgy. Just-
```
sudo apt-get dist-upgrade
```
You may want to wait for someone else to see if that is the correct command. There is a gui way to do it too, though I forgot how I went from breezy to dapper.Is in correct.
 
The update-manager notification should also inform you that a new version (6.10) of ubuntu is availiable.

---

### Post by toasted on 2006-10-26
> **PriceChild said:**
> [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) will explain things to you.
 
Please remember that edgy is still "edgy". Dapper will be supported longer and is meant to be more stable.
So Edgy is not stable?

---

### Post by Esben Kramer on 2006-10-26
When they say stable, they don't mean that it will crash! Stable means that the packages for the distro are 'locked'.

---

### Post by toasted on 2006-10-26
> **Esben Kramer said:**
> When they say stable, they don't mean that it will crash! Stable means that the packages for the distro are 'locked'.

Locked.....  could you please explain that a bit more?

---

### Post by chuckyp on 2006-10-26
> **CupofDice said:**
> You have to download a cd to get edgy.

edit-yeah, got rid of it.

You do NOT have to download the cd to upgrade to edgy.  It CAN be done with update manager.  If people would please read the desktop guide or wiki they would see this.  Just gksu "update-manager -c"

Upgrading, please see the instructions on: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by PriceChild on 2006-10-26
Edgy is an edgy release and has new technologies.
 
Dapper is an LTS release... it is rock solid!
 
Not everyone should upgrade to edgy.
 
Check out [http://ubuntuforums.org/showthread.php?p=1665650#post1665650](http://ubuntuforums.org/showthread.php?p=1665650#post1665650) for a few things about upgrading.

---

### Post by TitusDalwards on 2006-10-26
i can use my wireless under Dapper, and i can do much more things with Dapper, so for now i don't have to upgrade to Edgy. Am i right?

---

### Post by PriceChild on 2006-10-26
You never have to upgrade to Edgy... Dapper will be supported with critical bugfixes and security updates for a year after they stop Edgy on the Desktop, and 18 months longer on the server.
 
Plus, several wireless cards have taken a step back in Edgy... check out the stickies in the edgy dev forum.

---

### Post by toasted on 2006-10-26
> **PriceChild said:**
> You never have to upgrade to Edgy... Dapper will be supported with critical bugfixes and security updates for a year after they stop Edgy on the Desktop, and 18 months longer on the server.
 
Plus, several wireless cards have taken a step back in Edgy... check out the stickies in the edgy dev forum.

Ok so then why have an Edgy release at all, why not just keep it as a development item till such time as its stable and ready for the public? I mean, its offered as first choice on the download page and the explanations there are rather vague about the differences. 

True it does say that Dapper is LTS but someone new would not know what that is, Heck, I am only guessing what it means. 

Not making a lot of sense to me so far... Ive had Edgy installed as a test for a while and my video hasnt worked correctly in weeks.... I think it should not be offered so readily on the front page!!!

---

### Post by gruffy-06 on 2006-10-26
Nobody gets it!

Ubuntu 6.10 IS a stable release because it will only get security and critical updates. No new bleeding-edge software packages will be added at all, though you can still use the "backports" repository.

You can expect bleeding-edge software packages through "Feisty Fawn", the next Ubuntu release, soon to be in development.

---

### Post by toasted on 2006-10-26
> **gruffy-06 said:**
> Nobody gets it!

Ubuntu 6.10 IS a stable release because it will only get security and critical updates. No new bleeding-edge software packages will be added at all.

You can expect new bleeding-edge software packages through "Feisty Fawn", the next Ubuntu release, soon to be in development.

I for one do not "get it" thats for sure.

---

### Post by gruffy-06 on 2006-10-26
Like any Ubuntu release, you only have supported repositories and security and bugfix updates installed by default. If you enable "backports" in "Software Sources", you can have newer software, which is not supported.

Put simply, Edgy is only Edgy if you use backports.

---

### Post by toasted on 2006-10-26
whatever

---

### Post by J77 on 2006-10-26
> **gruffy-06 said:**
> Nobody gets it!
:mrgreen: Yeah.

Best to read the EdgyUpgrades page before ploughing in.

My desktop's being upgrading as I type...

---

### Post by ButtonMasher on 2006-10-26
Wow, now I'm confused...

So Dapper Drake LTS has locked in packages for three years.  These will not be upgraded as new software comes out.  Hence Firefox is stuck at version 1.5.

Edgy Eft has newer packages than Dapper Drake (Firefox 2.0) but that one is only going to be supported by the normal support cycle.

Feisty Fawn will have the latest bleeding edge packages and will be released about six months from now.  

If I want to get the latest bleeding edge packages with my current install, I need to enable the 'backports' repository. 

Am I right?  If I am I gather that if I like my system as it is, I stay with Dapper and if I want newer software (but not the newest) I upgrade to Edgy.  Any corrections are welcome.

---

### Post by Eddie Wilson on 2006-10-26
I asked the upgrade question and could get no one to answer. It seems that you have to have a high speed connection to upgrade and thats about all a person could do. If you don't have that you have to start from scratch to get the latest version. The way everybody talks I wonder why people would put out an os that is not finished. You are correct. Something doesn't seem right.

---

### Post by toasted on 2006-10-26
> **ButtonMasher said:**
> Wow, now I'm confused...

So Dapper Drake LTS has locked in packages for three years.  These will not be upgraded as new software comes out.  Hence Firefox is stuck at version 1.5.

Edgy Eft has newer packages than Dapper Drake (Firefox 2.0) but that one is only going to be supported by the normal support cycle.

Feisty Fawn will have the latest bleeding edge packages and will be released about six months from now.  

If I want to get the latest bleeding edge packages with my current install, I need to enable the 'backports' repository. 

Am I right?  If I am I gather that if I like my system as it is, I stay with Dapper and if I want newer software (but not the newest) I upgrade to Edgy.  Any corrections are welcome.

That sounds about right except if you upgrade to Edgy then some stuff will cease to work...  such as wireless cards, and with me, my video has been broken for weeks with no fix in sight.

---

### Post by J77 on 2006-10-26
> **Eddie Wilson said:**
> Something doesn't seem right.Then why make an announcement: [http://ubuntuforums.org/showthread.php?p=1665487#post1665487](http://ubuntuforums.org/showthread.php?p=1665487#post1665487)

There is no conspiracy :-#

---

### Post by Dinerty on 2006-10-26
It is a simpler process to just download the iso and burn it, if you did the dist-upgrade from Dapper to Edgy and things went wrong you would need to install Dapper from scratch and then upgrade again to Edgy, why not just do a one off download and use the CD as much as you want?

---

### Post by Mathiasdm on 2006-10-26
> **ButtonMasher said:**
> Wow, now I'm confused...

So Dapper Drake LTS has locked in packages for three years.  These will not be upgraded as new software comes out.  Hence Firefox is stuck at version 1.5.

Edgy Eft has newer packages than Dapper Drake (Firefox 2.0) but that one is only going to be supported by the normal support cycle.

Feisty Fawn will have the latest bleeding edge packages and will be released about six months from now.  

If I want to get the latest bleeding edge packages with my current install, I need to enable the 'backports' repository. 

Am I right?  If I am I gather that if I like my system as it is, I stay with Dapper and if I want newer software (but not the newest) I upgrade to Edgy.  Any corrections are welcome.

That's basically it, yes.

The reason there's a LTS version (Dapper), is mostly because some people prefer to stay with the same version for a while.
Companies, for example, don't like to switch to something new every 6 months. That's why Dapper is an LTS edition.

Edgy has some newer features (which does not necessarily mean it's 'unstable', like some claim), and changes some things in the boot process.

---

### Post by petersjm on 2006-10-26
If people are having problems with upgrading to edgy, maybe it's worth simply downloading the CD image, after all? I'm assuming the CD image comes complete with a LiveCD thing, as standard, so people can run Edgy without installing it first. That way, if everything works, you can go ahead and install it, but if things aren't working as they should, stick with Dapper...?

---

### Post by Eddie Wilson on 2006-10-26
Well I think that the best thing I could do is keep my mouth shut and stick with Dapper.

---

### Post by toasted on 2006-10-26
> **Eddie Wilson said:**
> Well I think that the best thing I could do is keep my mouth shut and stick with Dapper.

+1

---

### Post by J77 on 2006-10-26
> **J77 said:**
> My desktop's being upgrading as I type...That was fast - flashy new colours...

---

### Post by Circus-Killer on 2006-10-26
> **petersjm said:**
> You'll have to download the new CD image. Upgrades do not, AFAIK, give you the option of upgrading to Edgy.

if you dont know, dont pretend to know, otherwise you're just not helping, you're just adding to the poor guys confusion.

---

### Post by bennyj on 2006-10-26
Before I upgraged to edgy my hp3180 all in one would not scan.Since I have upgraded it works.seems to boot a little faster too.seems pretty stable to me.

---

### Post by missmoondog on 2006-10-26
yeah, those apt-get updagrades and synaptic upgrades never go smoothly. at least going from hoary to dapper to trying to do edgy has never gone right for me. much easier to either order the cd from shipit.com or download the iso and start over anyway.

---

### Post by Circus-Killer on 2006-10-26
it aint rocket science. 
the upgrade process between dapper and edgy is perfect.

---

### Post by serlex on 2006-10-26
Its getting more and more complicating

---

### Post by Circus-Killer on 2006-10-26
i wish you people would stop talking outta your asses. upgrading is a matter of issuing 2 commands, and letting it do the rest. read up before making more of an *** of yourself.

---

### Post by Roger Mudd on 2006-10-26
Circus-Killer,
Please refrain from belittling other forum members. You're bellicose posts are not helping the situation.

---

### Post by Circus-Killer on 2006-10-26
stop being a winey prat. if those people that im "belittling" thought for two seconds, they would
a) realise how stupid they being
b) that questions on upgrading has been answered a thousand times, no need for repition
c) they are actually hurting ubuntu's good name by stating that its "hard"

---

### Post by Zdravko on 2006-10-26
Nope. Automatic update didn't work for me. I did the following and nothing was found to be done. What should I do now?
> 
gksu "update-manager -c" 


---

### Post by RedBowers on 2006-10-26
I was able to update mine using the following
code:
gksudo "update-manager -c -d"
The only issues I have found so far have been with my vmware server which were addressed in other posts.

---

### Post by Roger Mudd on 2006-10-26
> **Circus-Killer said:**
> stop being a winey prat. if those people that im "belittling" thought for two seconds, they would
a) realise how stupid they being
b) that questions on upgrading has been answered a thousand times, no need for repition
c) they are actually hurting ubuntu's good name by stating that its "hard"

Thank you for your insight. Your posts have been reported.

---

### Post by John.Michael.Kane on 2006-10-26
Keep the thread on topic.

---

### Post by rplantz on 2006-10-26
"Stability" is relative. A set of software the size of a Linux distribution is much too complex to be 100% stable.

I have not been able to find a definition of "LTS" on the Ubuntu site.

I am guessing that as bugs are found, developers will give higher priority to fixing those in 6.06 (Dapper Drake) than those in 6.10 (Edgy Eft). But it would be nice if the developers could explicitly state this in an obvious place so people could make an informed decision about upgrading. However, having been a developer for several decades, I also understand how difficult it is to find the time -- between fixing bugs -- to write such documentation.

My take:
1. If a smooth running machine is important to you, stay with 6.06.
2. If you enjoy playing with newer things and can accept a few more problems in the spirit of "play," upgrade to 6.10.
3. If you are intrigued by software problems and like to figure out what the cause is, install Feisty Fawn when it first becomes available.

For what it's worth, I'm a long time Mac user (from March 1984). Of the many, many OS upgrades I did in that world, some went very smoothly, some were a nightmare. In my professional life I've written OS-level software and installed several OSs. Same thing -- some go smoothly, some tempt me to throw the computer out the nearest window. All of these have been environments where the possible hardware configurations were very limited and quite well known. We install Ubuntu on an extremely varied set of hardware configurations. It would surprise me if all Ubuntu installation and/or upgrade experiences were even remotely similar, let alone went smoothly.

---

### Post by petersjm on 2006-10-26
> **rplantz said:**
> I have not been able to find a definition of "LTS" on the Ubuntu site.

Just for clarification, I believe "LTS" means "Long Term Support". Ergo 6.06 will be supported longer than 6.10... At least, that's my understanding. If someone can confirm or deny that, I'd be happy.

Anyway, I'm downloading the ISO now. 13% so far... Woohoo!

---

### Post by PriceChild on 2006-10-26
> **petersjm said:**
> Just for clarification, I believe "LTS" means "Long Term Support". Ergo 6.06 will be supported longer than 6.10... At least, that's my understanding. If someone can confirm or deny that, I'd be happy.

Anyway, I'm downloading the ISO now. 13% so far... Woohoo!Quite correct :)

Dapper will be supported for 5years on the desktop/3 years on the server and Edgy for 1.5 years on the desktop/3 on the Server with critical bugfixes and security updates.

--clarified that... sorry just fed up of typing it out completely so often :)

---

### Post by toasted on 2006-10-26
> **PriceChild said:**
> 
Dapper will be supported for 5/3 and Edgy for 1.5/3 on Desktop/Server.

What does this mean?

---

### Post by joris1977 on 2006-10-26
just upgraded on my labtop.(acer aspire 5610) Was not flawless, wouldn't reboot. restarted in recovery mode. Rebooted again and than it worked. There's one package that doesn't want to be upgraded; libggi2 But wireless is working great and google earth wasn't working properly in dapper and works now. So it seems allright for the moment.

solved libggi2 issue: in synaptic force install mplayer edgy-version and than libggi2 will be upgraded.

update: Wireless works better than in the past. On dapper i had to push the wireless button on the side at the start up, otherwise it wouldn't run. Annoying. In edgy this button started working. 

Thanks ubuntu developers :)

---

