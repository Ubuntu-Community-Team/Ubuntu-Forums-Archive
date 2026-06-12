---
title: "What is it about Linux that makes it Virus/Spyware proof?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2006-08-19
Hello :) 

I had a question for the community; what exactly is it about Linux that keeps it virus and spyware free? A buddy of mine said that Linux doesn't have any viruses written for it because "it's not popular" and isn't "drawing attention", implying that if the world ever did switch to Linux... we'd be seeing viruses.

I told him that that's not the case, but I realized I didn't really know *why* it's true.

---

### Post by Sef on 2006-08-19
In Linux, you are not the all powerful administrator that you are in Windows.  For a virus or other malware to get into your root system, you would need to type in your password.  Ubuntu goes further and uses sudo instead of root.  To read more about it, Click on [Root/Sudo]("https://help.ubuntu.com/community/RootSudo")

Note: This does not mean that Linux is virus or malware proof, just that it is harder to infect than Windows.

---

### Post by taurus on 2006-08-19
> **Nexusx6 said:**
> Hello :) 

I had a question for the community; what exactly is it about Linux that keeps it virus and spyware free? A buddy of mine said that Linux doesn't have any viruses written for it because "it's not popular" and isn't "drawing attention", implying that if the world ever did switch to Linux... we'd be seeing viruses.

I told him that that's not the case, but I realized I didn't really know *why* it's true.
Because it's NOT Windows...  :twisted:

---

### Post by tribaal on 2006-08-19
Well one of the reasons it's not a target for viruses *epidemics* is the way system rights work:

Users don't have the right to mess up the system itself. You have to get root rights to be able to change system files (that's why you need to enter your password again when you do upgrades for example). And any program you run will have the exact same restrictions.

So let's assume you deliberately click on a nasty email attachment that was specifially designed for linux, then the virus would only have the same rights you have - it couldn't hide itself in the system's internals because it wouldn't be allowed to access system directories. So it might mess up your personal files at worse (the ones in you /home), but it couldn't wreck your system as a whole. Also, scripting features in windows (active X componeents for example) can be used to replicate the virus (outlook scipts attached to emails for example, can send themselves to people in your adress book). There is no such things in linux, or rather, each email program has it's own scripting interface.
That makes it really hard for a virus writer to propagate his virus on linux machines.

That's why virus epidemics are almost impossible in linux. But of course, you could sill be infected by targeted infections. But how likely is that?

Does that answer your question?

- trib'

---

### Post by scxtt on 2006-08-19
remember that the same virtual lockdown is possible in windows, but a Windows install generally allows EVERY user to be an administrator and FEW ever do anything about that fact  (i.e. take those rights away).

---

### Post by kerry_s on 2006-08-19
I say it's because the crackers respect linux, linux has never done nothing to them, linux don't make them pay out there butt to use, linux dosen't step all over there right to do what they want with there computer, i think there are more crackers helping to improve linux rather than trying to exploit linux, in all likely hood linux is what the cracker is using and they would not want to use a system full of exploits.

---

### Post by Nexusx6 on 2006-08-19
Ah, yeah I was thinking along those lines. I told him one of the reasons is that, for example, programs arn't allowed to just edit the startup configuration and add themselves in without you knowing. They can't just go and mess with system settings like that.

Thanks everyone for the insight.

---

### Post by aysiu on 2006-08-19
The major reason is really that a greater percentage of Windows users are stupid (when it comes to computer security) than Linux users.

Most Linux users had to install Linux themselves and figure it out and configure it. They're savvy enough (I hope) to create strong, hard-to-guess passwords, not install software from untrusted sources, not click attachments in shady emails or fall for phishing scams. They won't fall for the old, "You've got a virus on your computer. Click here to get rid of it" pop-up ad.

If Ubuntu became more popular and started attracting stupid users, I can almost guarantee it would also start attracting viruses/spyware.

---

### Post by tribaal on 2006-08-19
Hehe I agree Asyiu:

The major security breach is usually found between the screen and the chair ;)

- trib'

---

### Post by stormblue on 2006-08-19
As far as destroying all the data in /home I'd rather a virus make my system not able to boot than destroy the /home folder.

I think the biggest thing that is preventing viruses is pure numbers.  If ubuntu or linux got the numbers of linux we'd see increase in virus and malware.

This is becuase you have to write the virus once and you want to maximize it's return on investment. Ubuntu or any other distro doesn't offer that, unless they want a botnet of *nix machines.

Also, ubuntu users, as mentioned tends to be a little more savy than regular users.

Linux isn't Virus/Spyware proof, rather it's day just hasn't come.  Maybe that's how we should measure when Ubuntu is ready for the desktop, when it is effected by virus.

In business there are good problems and bad problems, and I'd say a virus for ubuntu may be a good problem.

---

### Post by darkenedday on 2006-08-19
I always thought one reason it wasn't  as vulnerable is that things aren't as intertwined, I've noticed that if I get an error in one system task, the rest still ocntinue to work, whereas in Windows any time a system task was messed with too badly the entire system would lock up, so in linux it is much more possible to fix these problems being that your system will still run, thus eliminating the point of a widesspread virus, and the hundreds upon hundreds of different system configurations on different peoples computers would also make it much more difficult, whereas in windows it's generally one standard setup with very few possible modifications

---

### Post by beameup on 2006-08-19
There is an acronym for that. PEBKAC


Problem Exists Bewteen Keyboard And Chair

---

### Post by encompass on 2006-08-19
In addition to that... linux comes in so many ways it can be hard to create a virus to attack that wide veriety, linux is the same at the core but still can be made different.  It can be greatly hardened because of it's open source style.  Some worms like some apples.  Others like oranges.  As long as you keep them fresh the odds of you getting a rotten one with a worm in it are slim.  To be honest I have never gotten a virus in my hole life.  Windows, way way back, or linux.  Hacked is another story, but that was my stupidity.:-|

---

### Post by catlett on 2006-08-19
The real reason for windows issue is not stupidity of users or hackers dislike of them ( a cracker would like nothing more than to have a linux virus in his list of deeds. search the forum jail and you will see attempts at cracking the forum )
The issue is how aplications are written in windows as opposed to linux.
Windows wrote bad applications. Period. They had vulnerabilities that were exploited. Period, end of story. A stupid person going to a web site and hitting on a link is not in danger unless his OS is vulnerable.
The worst applications in windows have been Outlook/Outlook Express and Internet Explorer. Those are the 2 ways crackers have gotten in. (the majority of successful viruses/trojans today come in through buffer overflow not by downloading. it downloads itself)
The problem is/was window's released bad apps and didn't do anything about it.

In linux, "peer review" eliminates this. A bad application will never reach a  repository because others will see the entire code annd catch a badly written application. In windows there isn't any peer review because the code is closed. Noone sees what is going into their system. It is up to windows to test and then to patch any bad app and they have done a terrible job.
Just to give an example, here is an old article about an ie virus. Nothing to do with stupid people or linux friendly hackers. Just an exploited IE vulnerability
> COMPROMISED AD SERVER SPREADS A VIRUS LIKE WILDFIRE

Banner ads have become the latest delivery mechanism for Hijacking computers through security exploits. A recent wave of banners targetted a known flaw in Microsoft Corp.'s Internet Explorer browser.

Over the weekend, hackers broke into a server that handles ad delivery for Germany's Falk eSolutions. The hackers successfully loaded exploit code on banner advertising, and served them on hundreds of Web sites.

"Users visiting Web sites that carry banner advertising delivered by our system were periodically delivered a file from the compromised site. This file tries to execute the IE-Exploit function on the users' computer," a representative from Falk eSolutions confirmed on Monday.

The exploit (Bofra/IFrame) takes advantage of an IE vulnerability discovered and reported to Microsoft earlier this month. It is a new variant of the MyDoom virus that attacked vulnerable IE users two weeks ago.

---

### Post by tribaal on 2006-08-19
> There is an acronym for that. PEBKAC

Lol I didn't know this :) Thanks for pointing this out, I'll use it often (although it translates to PEECEC in French - "Probleme entre clavier et chaise")

The numbers argument is flawed: if it was true, then the apache webserver would be more prone to viruses than microsoft IIS. It is not, however, despite having a larger marketshare.

- trib'

---

### Post by noynac on 2006-08-20
The following are interesting articles that address this topic. The bottom line is that Linux presents a pretty hostile environment for virus's, and Windows is a much more attractive target for the people that write these things. 

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

[http://www.securityfocus.com/columnists/188](http://www.securityfocus.com/columnists/188)

noynac

---

### Post by stormblue on 2006-08-20
> **tribaal said:**
> 

The numbers argument is flawed: if it was true, then the apache webserver would be more prone to viruses than microsoft IIS. It is not, however, despite having a larger marketshare.

- trib'

There are a number of things that make Apache popular.  The first is that it runs on the linux platform, where as IIS doesn't.  The other is that it is well programmed.  Both of these two issues make exploits less of an issue, but a google search for "apache exploits" reveals they do exist.  You can't exploit perfect code, and although Apache isn't perfect it is more perfect than IIS.  The numbers argument holds up when you do an all things equal evaluation.  I'm not going to try to find an exploit in bubba-gumps-ultimate-web-server if only 3 people use in on the planet.  Where as Apache and IIS give me a much higher rate of return.

---

### Post by Cyraxzz on 2006-08-20
1. Most(if not all) black hat hackers use Linux.

2. It's very difficult to infect a Linux system.

---

### Post by aysiu on 2006-08-20
> **catlett said:**
> The real reason for windows issue is not stupidity of users or hackers dislike of them If we got a larger percentage of stupid users, do you think it would be difficult for someone to write a program that says "Click here to get a cool thing," prompt for the *sudo* password and then have it infest someone's computer with a virus that then propagates itself by email to another stupid user who would give away her *sudo* password?

---

### Post by richardward101 on 2006-08-20
Surely it wouldn't need the root password to propagate to others... if it, say, installs itself as a firefox/linux plugin, or adds itsself to the session, then it can run and email stuff to people, whithout even needing root access. As someone mentioned, losing /home would be more devastating for many that an unbootable system, and if people are led to believe that if they don't put in the root password nothing can hurt them then this sort of thing must be possible.

---

### Post by stormblue on 2006-08-20
Aysiu,

It wouldn't be difficult at all really to do.  I'm not sure of a fix, but from a psycological view point, "sudo" is a what I type to get something done.  For example if I want to change my ethernet settings through a GUI I'd have to type in my password, if I want to install something I have to type in my sudo password.  So I would think there are users who use ubuntu who would have no problem typing in their password to install some cool screensaver or something.  It's a very real threat.  And only a matter of time before linux becomes just as exploitable, and more dangerous than windows.

---

### Post by aysiu on 2006-08-20
> **richardward101 said:**
> Surely it wouldn't need the root password to propagate to others... if it, say, installs itself as a firefox/linux plugin, or adds itsself to the session, then it can run and email stuff to people, whithout even needing root access. As someone mentioned, losing /home would be more devastating for many that an unbootable system, and if people are led to believe that if they don't put in the root password nothing can hurt them then this sort of thing must be possible.
And most people I know don't do regular backups of their personal files. God knows why.

---

### Post by IYY on 2006-08-20
To get infected in Windows (unpatched, and not behind a router): 

1. Open internet explorer. 
2. Wait 5 minutes.
3. You're infected.

To get infected in Linux:

1. Download a program that contains a virus/spyware.
2. chmod +x programName
3. sudo ./programName
4. Type in your administrator password.
5. You're infected.

So you see, it still is possible to get infected, but the virus problem now becomes the same as it has been in the days before the internet: you actually have to download and run an untrusted program.

But note that most Linux users get their software via apt-get or from a trusted source like sourceforge. Windows users get their software from all over the internet, and are much more likely to catch a virus.

An analogy is this: 

Linux is like a perfectly secure castle. There is virtually no way to break into it. However, it's still possible for you to ask a mass murderer to come inside for a cup of tea and then it's your responsibility. 

Windows is like a tent in the middle of New York city.

---

### Post by aysiu on 2006-08-20
> **IYY said:**
> 
But note that most Linux users get their software via apt-get or from a trusted source like sourceforge. Windows users get their software from all over the internet, and are much more likely to catch a virus. But, as I said before, this can change. Right now a lot depends on the users and their habits.

---

### Post by insane_alien on 2006-08-20
> Windows is like a tent in the middle of New York city.

with a big neon sign above it saying 'infect here'. and a leaky roof.

---

### Post by richardward101 on 2006-08-20
> And most people I know don't do regular backups of their personal files. God knows why.
I know I don't, I can't.
I have a nearly full 320GB hard disk, Where am I supposed to back that up to? The only thing I back up is my Music collection, which itself is several DVD's worth.
I just keep my files as belonging to a different user symlinked in my home folder, the folders of which are writeable to and the files arent, so I can put stuff in it but not edit it, and then a cronjob chowns the files to the other user every so often. That took me hours to figure out (had to learn cronjobs, chown, bash etc). Was one of the first things I tried to do on linux, as I'd just lost a lot of data in an accident.
Most pc owners just can't do something like that, and don't have the means to back up (I would buy a hard disk to back up onto, but then in a month i'd have started using it for more media).

---

### Post by aysiu on 2006-08-20
This may seem expensive at first, but I'd advise getting an external hard drive--something like [this](http://www.newegg.com/Product/Product.asp?Item=N82E16822136025) would probably suit your needs.

The price tag can be shocking, but just imagine if you actually lost that 320 GB's worth of data...

That said, do you really think most people who don't back up have 320 GB of data?

---

### Post by stormblue on 2006-08-20
Most IE infections come over port 80, which most routers keep open by default, so the fact that you are behind a router is really irelevent in both windows and linux.  Linux, at least Ubuntu, has no ports open as default.

I rarely run anti-virus or firewall on windows, and I've never had issues with viruses.  It has to do with user habits and as Ubuntu becomes more prevelent and gains more marketshare, it also will probably gain more dumb users.  Also, one disadvantage is that linux is "virus and spayware proof" as the topic started suggested and that leads people into a false sense of security.

---

### Post by stormblue on 2006-08-20
Something that might be cheaper is getting an old box and a new harddrive 500GB for 300 so for roughly $350 you could have a ~500gb backup system.


Just saw a 400gb on newegg for $200 so for $250 you got ~400gb.

---

### Post by orb9220 on 2006-08-20
Plus thier is DVD's now 100GB takes 23 disks x .30 cents on sale runs about $7 and only $21 for 300GB and that would take a big load off of worring  about your collection.

I even have a archive set off site in case of fire or Borg Intrusion.

---

### Post by richardward101 on 2006-08-20
> This may seem expensive at first, but I'd advise getting an external hard drive--something like this would probably suit your needs.

Well, yes it deos seem expensive, I'm a student, It was all I could do to spend the £70 on the internal one, let alone £180 for another.

> The price tag can be shocking, but just imagine if you actually lost that 320 GB's worth of data...Actually I don't have to, I've suffered this kind of loss before, lots of music, lots of uni work, a fair catalog of windows source code, and several years of digital photos. I neglected to mention work and photos as what I back up now-days, but the work particularly takes up vary little space (no jokes please).

> That said, do you really think most people who don't back up have 320 GB of data?
I guess not. But also, I have seen a lot of people 'back up' by simply copying their stuff to another folder on teir HDD, assuming this will be safe. People are naturally unwilling to backup until they've learned the hard way. Personally I feel that one of the better backup tools with a pretty gui ought to be in ubuntu by default, just so pple are tempted to use it. possibly even have it as an icon on the desktop, stretched as large as possible with big writing... well maybe not, but included by default none the less

---

### Post by richardward101 on 2006-08-20
Of course, going back to the original post, none of the things mentioned technically classifies as a virus as they don't self propagate.

---

### Post by user1397 on 2006-08-20
btw, ubuntu is getting bigger and bigger every second.  already, there are more than 150,000 registred ubuntu forum members, not to mention all of the people not registered in these forums.  150,000 people is like 1/120 the population of earth.  that's something to think about.

check out this thread to see some fun facts: [Ubuntu is King!!!!!!!!!! (Fun Facts!!!!!!!!)]("http://ubuntuforums.org/showthread.php?t=239273")

edit: actually if you look at the last post in that thread, the total number of registered forum members for all those distros is about 400,000.  that's a lot of people.

---

### Post by richardward101 on 2006-08-20
> 150,000 people is like 1/120 the population of earth150,000 * 120 = 18 million, whereas the population of the earth is more like 6.6 billion. the fration is more like 1/44000 the population of the earth.

---

### Post by user1397 on 2006-08-20
> **richardward101 said:**
> 150,000 * 120 = 18 million, whereas the population of the earth is more like 6.6 billion. the fration is more like 1/44000 the population of the earth.lol.....wow, i'm really off today....:-k

---

### Post by sanderella on 2006-08-20
In my ignorance I'm worried that you guys might be giving ideas to creators of virus programs....:confused:

---

### Post by sanderella on 2006-08-20
I forgot to say sssshhhhhh.....

---

### Post by stormblue on 2006-08-20
> **richardward101 said:**
> Of course, going back to the original post, none of the things mentioned technically classifies as a virus as they don't self propagate.


Being able to execute arbitrary code is what's dangerous.  Just becuase they haven't yet created a virus that spreads through a particular exploit (Either computer or human) doesn't mean they won't. If they can execute the code then they can probably make it into a virus, instead of just installing spyware. That leap is rather trivial.

---

### Post by scxtt on 2006-08-20
[QUOTE=richardward101]Personally I feel that one of the better backup tools with a pretty gui ought to be in ubuntu by default, just so pple are tempted to use it. possibly even have it as an icon on the desktop, stretched as large as possible with big writing... well maybe not, but included by default none the less[/QUOTE]you mean something like Keep that comes installed by default in Kubuntu? ;)

---

### Post by cyberlite on 2006-08-20
Still I think that ubuntu is better at keeping virusus away then windows. It's the logical choice...........for me.:cool:

---

### Post by richardward101 on 2006-08-21
> **stormblue said:**
> Being able to execute arbitrary code is what's dangerous.  Just becuase they haven't yet created a virus that spreads through a particular exploit (Either computer or human) doesn't mean they won't. If they can execute the code then they can probably make it into a virus, instead of just installing spyware. That leap is rather trivial.

The step may indeed be trivial. Ok, of you find an exploit that allows you to execute arbitary code then you can go on to look for other computers with the same exploit and use it, thats a virus.

However, in the case of: Ignorant user downloads and installs x piece of untrustworthy code and executes it. In this case the same lapse/lack of judgement is necessary on the part of another user on a different machine, so the virus cannot spread under its own steam, and thats what I meant didn't equate to a virus.

---

### Post by beameup on 2006-08-21
> **tribaal said:**
> Lol I didn't know this :) Thanks for pointing this out, I'll use it often (although it translates to PEECEC in French - "Probleme entre clavier et chaise")



Here ya go!
[http://ars.userfriendly.org/cartoons/?id=19980506](http://ars.userfriendly.org/cartoons/?id=19980506)

---

### Post by richardward101 on 2006-08-21
This is a little OT, probably not worth anyone bothering to read it, just a little disclaimer.

> **sanderella said:**
> In my ignorance I'm worried that you guys might be giving ideas to creators of virus programs....:confused:

Speaking of, I came up with an (imo) excellent idea for a virus, or at least the attack a virus could perform once its infected a system, and I've wanted to tell people about it for a while...

If you can manipulate file IO or something at a more basic level with the HDD, you could predict how the heads would move with certain operations, causing a slight resultant force on the entire pc.

Now, if you found the harmonic resonance frewuency of the computer you could manipulate the heads in such a way that an oscilating motion would build up, until the PC eventually tips itsself over!!

There is only one problem (yes, just the one): You don't know where the PC physically is at any given time, so you can't adjust the input force (the movement of the HDD heads. There are, as I see it, 2 sollutions to this:
[INDENT]1. [INDENT]Use a webcam. If there is one that in any way would give you feedback (eg it is placed on the box or shows it slightly i the image), you could use this for feedback.[/INDENT]
2. [INDENT]Whenever a piece of metal passes through a magnetic field, it produces a current. The Earth has its very own magnetic field, through which, among other things, the microphone socket will move as the PC begins its pendulaic motion. By listening to the background hiss caught my the microphone socket one can work out how much the PC is moving and adjust the HDD head movement accordingly![/INDENT][/INDENT]
I prefer the second option.

Of course, a Linux box would be damaged no less by falling over than a Windows box, and it wouldn't discriminate when it comes to file permissions and other such protections. It could even fall on you back up disks!

But lets think bigger, what if we could infect an entire server rack with this virus, and tip over a cabinet containing dozens of slimline server.

Bigger still, What about a server room in a tall building? infect everything and find the harmonic resonance frequency of the entire building? Tall buildings are designed to withstand earthquakes, so rather than damaging the building, it would just cause it o sway in a very impressive manner. now THAT'd be a virus to be proud of!

---

### Post by richardward101 on 2006-08-21
> **scxtt said:**
> you mean something like Keep that comes installed by default in Kubuntu? ;)

Fair enough, but what about us Gnome users?

---

### Post by nocturn on 2006-08-21
> **Nexusx6 said:**
> Hello :) 

I had a question for the community; what exactly is it about Linux that keeps it virus and spyware free? A buddy of mine said that Linux doesn't have any viruses written for it because "it's not popular" and isn't "drawing attention", implying that if the world ever did switch to Linux... we'd be seeing viruses.

I told him that that's not the case, but I realized I didn't really know *why* it's true.

Well Linux is certainly not malware proof.  It's just a lot more resistant to it than windows is.

A couple of things include diversity (monocultures are a security nightmare), no open ports on default installs (hence nothing for a worm to attack), a more secure browser (no activeX), software installs from repositories that are digitally signed (instead of download.com).

There are other advantages too, but I don't have the time to go into it right now.

---

### Post by scxtt on 2006-08-21
> **richardward101 said:**
> Fair enough, but what about us Gnome users?i don't know what is KDE specific about Keep, i'd have to try an **sudo aptitude install keep** in Gnome and find out {no current Gnome install A.T.M.} - otherwise, i don't see why Gnome users can't use it ... (looks like a GUI frontend for rdiff-backup, which isn't KDE or Gnome specific) ...

---

### Post by ColdDeath on 2006-08-21
> far as destroying all the data in /home I'd rather a virus make my system not able to boot than destroy the /home folder.

Back it up ;-)

---

### Post by newbymick on 2006-08-21
[http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)

Try this link to find the real reasons.  It's a bit of a long read but well worth it.  :-k

---

### Post by richardward101 on 2006-08-21
> **scxtt said:**
> i don't know what is KDE specific about Keep, i'd have to try an **sudo aptitude install keep** in Gnome and find out {no current Gnome install A.T.M.} - otherwise, i don't see why Gnome users can't use it ... (looks like a GUI frontend for rdiff-backup, which isn't KDE or Gnome specific) ...

My point was it ought to be there by default.

---

### Post by 3rdalbum on 2006-08-21
> **stormblue said:**
> Most IE infections come over port 80, which most routers keep open by default, so the fact that you are behind a router is really irelevent in both windows and linux.

Do the routers really keep port 80 open? Mine didn't by default. I assume you mean ADSL routers.

---

### Post by scxtt on 2006-08-21
> **richardward101 said:**
> My point was it ought to be there by default.rdiff-backup probably is - and i see your point - but seriously, it's not hard to get some sort of backup going (it's not like windows does it by default) ...

---

