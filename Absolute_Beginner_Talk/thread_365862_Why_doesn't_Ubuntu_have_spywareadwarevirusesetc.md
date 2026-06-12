---
title: "Why doesn't Ubuntu have spyware/adware/viruses/etc?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-02-20
Why is it that Ubuntu (and Linux in general, I suppose) does not have spyware, malware, and adware?

....dunno what else to say.  Heh.  The topic asks it all.  Why would nearly ALL of the Windows computers I have ever sat down at been virtually infested, yet Linux isn't?

---

### Post by Maestro23 on 2007-02-20
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Sarteck on 2007-02-20
> **Maestro23 said:**
> [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Well, I read that (it was linked in another thread I read), but it still doesn't explain it to me.  I mean, after all, the very last thing it talks about is users being stupid, and I know that I'm not the only Linux user who is a complete dumbass.  XD

Seriously, there's got to be plenty of us who have installed/compiled programs that we weren't 100% on, so on and so forth.  And I know a LOT of people probably just set themselves as the root user for convenience, thus bypassing THAT security.

So, is there another reason, other than the running as root and closed ports bits mentioned on that page?

---

### Post by kinematic on 2007-02-20
one of the main reasons is interest.
the people who write virusses and crapware just aren't interested in linux(yet).

---

### Post by mikewhatever on 2007-02-20
One reason is Ubuntu is just more secure then Windows. MS has neglected Windows security for years, but I have to say, things are alot better now. There other, it is a lot less widespread, so what's the point of creating a virus that would only work on 1% of computers in the world.
Now, no OS is 100% secure and really, most of the time, it's the users' fault. There is a lot of pirated software for Windows, have you ever wondered why? People like to open spam messages and visit problematic sites, so there you go.

---

### Post by Sarteck on 2007-02-20
kinematic, mikewhatever, both of you are basically saying "lack of interest."  mike, you go on to say that many people who are into that kind of thing would not want to create a virus that would work on only 1% of computers in the word...

However, is the Linux community truly so small?  And of the people that create viruses, malicious hackers, wouldn't they want to go for the BIGGER targets, i.e. servers?  And isn't it true that over half of the servers on the Internet are Linux?

---

### Post by mcduck on 2007-02-20
Well, most of the web servers run Linux or some other Unix-type OS, as do many banks and super computers. Having far more power and faster network connections than home computers these machines would be far more interesting target to virus writers and crackers than your normal desktop machine. So I don't think 'lack of interest' is a good explanation. The far better security of Unix-based systems would be a better one :)

Note, that Unix was designed from the very first versions to be a multi-user networked environment, whereas in Windows such features are 'glued on top' of the OS during years. (For long time MS wasn't actually going to support Internet, developing their own network instead. In the end they had to quickly adapt their system for Internet which led into some security issues).

Also, it would be pretty hard to get your virus on LInux system if the user only installs applications from the official repositories, instead of downloading all kinds of shareware and other apps from random web sites.. And then there's the thing with user rights handled in much more strict way than in Windows.. (in XP even normal users are able to install new applications and have write access to system directories)

---

### Post by Maestro23 on 2007-02-20
Here's an article written on 2004 discussing security in Windows vs. Linux.  Might give it a read: [http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)

---

### Post by ewl1217 on 2007-02-20
One point that is often neglected is the diversity of software used in different Linux distributions. Sure, a small percentage of home computers and many, many servers are running on Linux, but they often use different distributions, which typically use different software, or at least different versions of the same software. While we're all using Ubuntu, others are running distributions like Gentoo, Fedora Core, Linspire, Mandriva and so on. All these distributions have their own way of doing things, a different set of preferred software, and different methods of installing it. Consider different ways of gaining root privileges (logging in as root, su, sudo), different desktop environments (GNOME, KDE, Xfce), different package management systems (apt, rpm, portage, CNR), and different web browsers (Firefox, Epiphany, Konqueror, Opera) for example. Such variety means that a virus affecting one distribution likely won't do anything to another.

---

### Post by getaceres on 2007-02-20
Virus targetting web servers won't work because big servers, although they run Linux, are managed by very professional people that has big knowledge about security. They for example don't install a package in their web server at least it's reviewed, signed and absolutely free of bugs and virus.
They don't target Linux because the Linux desktop share is just too small. It will only affect 1% of computers vs. 95% of computers if they target Windows. Normally a dumbass user doesn't run a web server, but a desktop computer with Windows. It's the kind of user that opens an e-mail with the subject "See Condoleezza Rice naked" and spreads a worm without even knowing what he's doing. If dumbass people used Linux and it was used by 95% of the desktop computers, it would have exactly the same problems as Windows is facing nowadays.

---

### Post by Statik on 2007-02-20
Yes, its true that much of the internet webservers are running Linux. Why don't people write virus's and malware, etc. for those? Because webservers don't open email attachments, they don't install software, etc. Linux webservers are often HACKED into by people who guess the passwords, etc. for remote logins. They are often used for nefarious purposes by people who setup 'rootkits' on them. There are security measures for this, but mostly it isn't the OSs fault, rather the sysadmins who setup weak passwords and such.

As a desktop OS, Linux just doesn't have the market share, as well, they don't have the pirating problem of Windows. Most retired grandmothers don't use Linux. They use an MS product. They fall for the email 'nigerian scheme' and such. They spend tons of money on non-existent products. Virus's and malware are written for Windows becuase of:
1. largest market segment
2. largest available n00b base.
3. most widely known expolits.

If linux, as a desktop OS, had a large userbase of n00bs who were susceptible(sp?) to viral social engineering and such, and that same n00b base had a large amount of available money, we'd probably attract more attention.

As it stands, most linux users are slightly more educated, much poorer, and probably less interested in the usual malware/spyware/virus techniques used today.

Another factor is that most Windows installs use IE as their browser and a version of Outlook (Express) as their email client. In Linux, the web browser and email client are mostly dependant on the distribution in use (Redhat, Suse, Ubuntu, etc.) and also personal taste (Evolution, Thunderbird, etc.) So, even within the same OS (linux) there are several very different distributions and several different choices within those distributions. While they all strive to present a consistently usable front-end they all function differently on the backend making it even more difficult to design and build an effective infiltratioin package.

Variety, in this case, is definitely the spice of life.

Statik

---

### Post by lyceum on 2007-02-20
Reasons:

1. The code is open. This means that the holes can be fixed by anyone. If a hole were used for a bug or virus, it could found and fixed quickly. In the proprietary world, holes are found then sit on a desk until work on them is approved.

2. Root. Unless you give someone your root password, an outside party cannot make changes to your computer. 

3. Users. The people that currently use Linux learn more about how their computer works due to the open nature, or they are programmers or already knowledgeable about computers. 

4. Use. Vultures go for the easy target, and Windows is widely used, its users make for easier targets. This is a generalization, and not true for all Windows users. However, the odds are more in favor the more users there are.

This is a topic that gets discussed all the time, but these are the reason I see the most offten, and they make sense.

---

### Post by T3h_Dohtem on 2007-02-20
I have to agree with Statik. It still comes back on security equally, if not more than the fact that it's a smaller market. If you consider the amount of people that that 1% encompasses, it's still quite a large target, and one that is growing faster every day. If it was as easy to work a virus or spyware program into a Linux desktop as it was a Windows, the problems would be here as well. Wndows has that largest available n00b base, including the devs, and is much less secure as an OS itself. Remember when Microsoft had included an internal messenger that allowed anyone to use Windows' built in function to place a popup directly on your desktop without even having any browser running?

Before standard desktop users started migrating to linux, the userbase was programmers, network engineers, system administrators. People who not only used the OS but formed it. Linux, BSD, *nix OSes represent a hive mind. Rather than a small company with the guidance of one man, it's the entire world working together to improve the system, and all of the pieces that make it. A Linux OS is made up of a mixture of programs that come together to make it whole. Each piece is constantly being developed, tested, and improved by the developers, with help from the whole community.

Open Source is what makes Linux more secure.

EDIT: Iyceum posted while I was writing this, but I think I agree with him more than I do myself. I guess I type too slowly. :P

---

### Post by Strider42 on 2007-02-20
> **kinematic said:**
> one of the main reasons is interest.
the people who write virusses and crapware just aren't interested in linux(yet).

People who write viruses and crapware are Linux users, so they leave it alone...  :-$

Imagine getting done by your own virus.

---

### Post by getaceres on 2007-02-20
Let's suppose that 90% of the users use Ubuntu. Now Joe has Ubuntu and he knows how to install a package. It's easy, double click, enter your password, go. Then he goes to site XXX and finds the "Ultimate application to get free porn" and he clicks. That link points to a deb package and he selects the default firefox option "Open with gdebi". Now he is presented with the familiar gdebi screen that asks for his password, so he enters it just like he has done other times and that package is installed. If that package contains a worm or a virus that deletes all of the user's hard disk, how that scenario is different from the typical windows scenario? The security is based in that it asks a password, but dumbass user gets used to inserting that password whenever asked without even knowing what it's going to do.

Linux is safer that Windows not because it's better designed for security (it is) but because Linux users tend to be more computer savvy than the average Windows user.

---

### Post by lyceum on 2007-02-20
> **getaceres said:**
> Let's suppose that 90% of the users use Ubuntu. Now Joe has Ubuntu and he knows how to install a package. It's easy, double click, enter your password, go. Then he goes to site XXX and finds the "Ultimate application to get free porn" and he clicks. That link points to a deb package and he selects the default firefox option "Open with gdebi". Now he is presented with the familiar gdebi screen that asks for his password, so he enters it just like he has done other times and that package is installed. If that package contains a worm or a virus that deletes all of the user's hard disk, how that scenario is different from the typical windows scenario? The security is based in that it asks a password, but dumb-edit- user gets used to inserting that password whenever asked without even knowing what it's going to do.

Linux is safer that Windows not because it's better designed for security (it is) but because Linux users tend to be more computer savvy than the average Windows user.

Most spyware malware & viruses are uploaded and installed in Windows without user permission. I have to agree that you cannot save someone from themselves. At the same time, if this type of invasion is the most comon, it would still be easier to fix in an open code (FOSS) model than in a PC with code you cannot look at. In FOSS, there is nowere to hide. Though in your example, the user jsut learns a valuble lesson. Someone out there doesn't want him looking at porn ;)

---

### Post by 23meg on 2007-02-20
> **getaceres said:**
> how that scenario is different from the typical windows scenario? Here's one aspect of how it's different:

[http://www.ubuntuforums.org/showpost.php?p=2023639&postcount=819](http://www.ubuntuforums.org/showpost.php?p=2023639&postcount=819)

---

### Post by yidaho on 2007-02-20
As far as I can see it the philosophy of the two operating systems is as follows:

Image Windows as a boat sailing the ocean. Unfortunately this boat was designed like a sieve and to some extent intentionally.  M$ thought that the average user would be too stupid to activate a feature if they required it, so they activated all the features for you.  This lead to HUGE security vulnerabilities. Consequently they are for ever trying to plug the holes and M$ keep sending corks out to plug the holes but more keep appearing as fast as they plug the old ones.

Linux/Unix was designed to be water tight from conception and if you want a hole you have to ask permission for it.

Paul

---

### Post by lyceum on 2007-02-20
> **23meg said:**
> Here's one aspect of how it's different:

[http://www.ubuntuforums.org/showpost.php?p=2023639&postcount=819](http://www.ubuntuforums.org/showpost.php?p=2023639&postcount=819)

To add to your linked post, you are correct with the centralized repository model. I fear that does not stop people from being ignorant or doing ill advised things. I have read posts where people have made the switch, downloaded a program from a website and asked how to install and the correct answer was just to go to Add/Remove. :) 

If they are surfing with FireFox, once a page is known to be "bad" or suspisious, you should get a warning from FF not to go there. This would give even more security (in theory). In the end, someone someware will do something dumb. MS proves that by making their OS "fool proof", as in yidaho's example. (Which leads to my theroy that Fool Proof must mean proofed by fools :))

---

### Post by 23meg on 2007-02-20
> **lyceum]To add to your linked post, you are correct with the centralized repository model. I fear that does not stop people from being ignorant or doing ill advised things. I have read posts where people have made the switch, downloaded a program from a website and asked how to install and the correct answer was just to go to Add/Remove.[/QUOTE]
It does not absolutely stop them said:**
> In the end, someone someware will do something dumb. 
Sure. But compare the following: you teach a user who's uninformed about security and computers in general that the common way to install an application is to look for it on Google, download it, double click the downloaded file, click Next - I agree - Next - Next - Next - Finish, and they go about installing software this way. And you teach another that the way to do it is not touch the default sources.list, open Synaptic, look for the app, choose it and click "Apply". 

Which is more likely to end up in trouble?

---

### Post by floke on 2007-02-20
On the computer savvy point. What happens when someone wants to get Linux up and running? Sure, a lot of stuff on ubuntu works out of the box, but the very least someone will have to do is partition their hard drive - a giant step into the unknown for many windows users (counting myself here just a few months ago). So, my point is really this: its not just that Linux users tend to know more, but that the process of using Linux encourages you to learn more, that by itself (along with the huge community support here) helps to create a more educated user base. To take the above example; to install in Linux you must enter a password or use 'sudo'; so the new user asks 'why? Windows never made me do this' . The reply they get from the community then drums it into them about being a responsible user, about security, root privileges etc., and so the learning curve gets that little bit thinner....

Hope this makes sense anyway!

---

### Post by 23meg on 2007-02-20
[QUOTE=Steve.K]So, my point is really this: its not just that Linux users tend to know more, but that the process of using Linux encourages you to learn more, that by itself (along with the huge community support here) helps to create a more educated user base.[/QUOTE]This too will probably change at the hypothetical time point where Linux is as widespread as Windows, since by that time Linux based operating systems will almost certainly be shipping preinstalled with many, if not most computers. But advantages such as the one I mentioned in the last post will come in as well.[QUOTE=Steve.K]
To take the above example; to install in Linux you must enter a password or use 'sudo'; so the new user asks 'why? Windows never made me do this' .[/QUOTE]At that time, using sudo may be as second nature to the common non-technical user as double clicking Setup.exe or clicking the Start button is today.

---

### Post by lyceum on 2007-02-20
> **23meg said:**
> It does not absolutely stop them; it's not realistic to expect any security or installation model to stop people from doing stupid things entirely. If people are so inclined, they always will. 

However, the reason people who are new to Linux rush to look for a package on the web and download it when looking for a program is their old habits left from other models. In the linked post, I'm talking against the assumption that if Linux gets as popular as Windows, it will necessarily be equally insecure. I'm not saying that it can't be; but whether it will be or not depends on how well better practices such as sticking to centralized repositories for the majority of common software needs are adopted. 

Keep in mind that at a hypothetical time in which Linux is as commonplace as Windows, the majority of people won't be taking the Windows way of doing things for granted the way they do now. As many people will be growing up with the Windows model as with the Linux model.

Sure. But compare the following: you teach a user who's uninformed about security and computers in general that the common way to install an application is to look for it on Google, download it, double click the downloaded file, click Next - I agree - Next - Next - Next - Finish, and they go about installing software this way. And you teach another that the way to do it is not touch the default sources.list, open Synaptic, look for the app, choose it and click "Apply". 

Which is more likely to end up in trouble?

I may have come across the wrong way, but I was agreeing with you. My only point was that nothing is fool proof, but having repositories is most likely as good as it can get :)

---

### Post by lyceum on 2007-02-20
> **Steve.K said:**
> its not just that Linux users tend to know more, but that the process of using Linux encourages you to learn more, that by itself (along with the huge community support here) helps to create a more educated user base. To take the above example; to install in Linux you must enter a password or use 'sudo'; so the new user asks 'why? Windows never made me do this' . The reply they get from the community then drums it into them about being a responsible user, about security, root privileges etc., and so the learning curve gets that little bit thinner....

Hope this makes sense anyway!

> **23meg said:**
> This too will probably change at the hypothetical time point where Linux is as widespread as Windows, since by that time Linux based operating systems will almost certainly be shipping preinstalled with many, if not most computers. But advantages such as the one I mentioned in the last post will come in as well.At that time, using sudo may be as second nature to the common non-technical user as double clicking Setup.exe or clicking the Start button.

Very good points, I agree with both. I think it is the community that makes FOSS stronger and the users better equipped to handle their PCs. What is the saying? "MS gives you Windows but Linux give you the whole PC." 

I do fear the popularity may "dumb down" the user, as things would come pre-installed. But I wonder if there was a similar conversation between people when you had to make your own distro or when a live CD could install everything just by answering the few question etc... I think that there is at least a fighting change for learning in FOSS that Windows can not provide. But that is just my 2 cents.

---

### Post by 23meg on 2007-02-20
> **lyceum]I do fear the popularity may "dumb down" the user, as things would come pre-installed.[/QUOTE]I don't fear that popularity will dumb the user down said:**
> 
But I wonder if there was a similar conversation between people when the you didn't have to make your own distro or when a live CD could install everything just by answering the few question etc... I think that there is at least a fighting change for learning in FOSS that Windows can not provide.People sat down and properly learned Windows inside out as well, when the network effect didn't exist, and the standard of the day was DOS or *nix. Today however, the common set of Windows usage tasks (double click Setup.exe, hit the Start button, cut/copy/paste, uninstall programs etc.) is a very standardized and compacted set of information, enough so to be transferred from one non-technical user to the other, or learned by trial and error. I would go so far as to say it has become part of global culture; for a huge amount of people, it's not much less commonplace and more technical than learning what does what on a typical TV remote control. And once you learn how one remote control works, you can easily find your way around all of them, even though they all have their little differences and quirks.

For a fair and reasonable comparison, we have to be thinking of a time when sudo, Synaptic, or whatever their future counterparts may be, are nearly as second nature to a substantial number of people as what's what on a TV remote; a time when they're much deeper ingrained in computer culture.

---

### Post by Patrick K on 2007-02-20
Judging from the replies, no one read the link Maestro23 posted. I did , all of it. Quite long, btw, but very informative. First off, even if Linux had 95% of the computer market, it would not be nearly as vulnerable as Windows. This has a lot to do with the basic design criteria of the two OSs. Linux's modular design protect the kernal in a way MS' monolithic design does not. With the heavy intergration of the various components of the OS into the kernal, any vulnerability in most any app is a vulnerbility in the kernal. This is particularly true with IE and Outlook (Express). The modular design of Linux isolates the kernal from user apps. Sure a fool can DL some malicious code and it might even run but the damage is limited to that user's files and not the entire system. (Of course, if the user is running as root, then all the root files are at risk.)

I suggest reading the link Maestro23 posted. Here it is again:
[http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)
At least, skim it. There are many other reasons discussed other than the one I gave.

---

### Post by bikeboy on 2007-02-20
> **Sarteck said:**
> So, is there another reason, other than the running as root and closed ports bits mentioned on that page?

Remember that those who specifically choose to run as root for convenience would need to have a decent amount knowledge about Linux, so they aren't the dumbass desktop user mentioned here already. But at the same time, the people who have that knowledge also know why they shouldn't run as root and they know how to administer a Linux system, realising that running as a normal user is not inconvenient.

It's not a pain running as non-root because the system is well thought out, unfortunately for Microsoft, the same hasn't occurred in Vista, despite them trying to copy the same useful concept.

In summary, I doubt there are actually many people out there running as root on a daily basis, and even few people who do that whilst possessing little Linux expertise.

---

### Post by Patrick K on 2007-02-20
Unless they are the dumbass that posted complaining that he hated using sudo and wanted to login as root. He did even know that the time alloted as sudo/root could be changed. He had no concept of using a secure system. Hum, I wonder if "sudo firefox" works?

---

### Post by getaceres on 2007-02-21
If Linux was as popular as Windows the centralized repository model wont work due to some software being proprietary. I know some people that don't use gimp if they can get Photoshop for free even to only touch brightness of a photo. Linux would have the same problem (piracy, cracks, serials, ...) that Windows has faced for many years and obviously the central repositories nor the unofficial well known repositories couldn't provide this kind of software making some users install software the same way they do in Windows (search google, download, install).

---

### Post by bikeboy on 2007-02-21
You can still force gpg verification etc. to make it more secure and make sure a proprietary download is the genuine product. The vast majority of software would still be in central repos.

Not to mention the fact that there is already proprietary software available for linux, and programs you need to pay for. Why aren't we seeing problems with those?

Lastly, what do cracks, piracy and serials have to do with security? These aren't the cause of windows being vulnerable.

Linux isn't 100% secure, of course it's not. But the point is, even with huge popularity, it would be harder to exploit linux, or any sort of nix, bsd or similar.

---

### Post by proxima estacion on 2007-02-21
there are no virus's on linux out of respect. Its the same reason no one has ever tried to steal the Dali Llamas cell phone.

---

### Post by 23meg on 2007-02-21
> **getaceres]If Linux was as popular as Windows the centralized repository model wont work due to some software being proprietary.[/QUOTE]That's a very debatable judgement said:**
> Linux would have the same problem (piracy, cracks, serials, ...) that Windows has faced for many years and obviously the central repositories nor the unofficial well known repositories couldn't provide this kind of software making some users install software the same way they do in Windows (search google, download, install).There are already centralized commercial distribution schemes such as CNR. I don't think the "grab an installer from any site and double click it" model will ever get widespread.[QUOTE=bikeboy]Lastly, what do cracks, piracy and serials have to do with security? These aren't the cause of windows being vulnerable.
[/QUOTE]They are part of the cause. Most software on the Windows platform is third party and has to be paid for, thus people who don't want to pay for software go looking for cracks, and cracks are found in nasty sites that fill your computer with malware unless you take precautions. Also, a crack is just another suspicious unverified executable that's possible to stuff with malware.

Having a quality set of Free software that covers all basic needs available in a centralized repository helps a lot.
[QUOTE=proxima estacion]
there are no virus's on linux out of respect. Its the same reason no one has ever tried to steal the Dali Llamas cell phone.[/QUOTE]I [agree]("http://www.ubuntuforums.org/showpost.php?p=668315&postcount=357").

---

### Post by aysiu on 2007-02-21
This discussion has gone way beyond helping out a new user. I think the OP has gotten enough answers for now.

For more reading (and discussion), check out this thread:
[Ubuntu/Linux/Windows and Viruses/Malware](http://ubuntuforums.org/showthread.php?t=323028)

---

