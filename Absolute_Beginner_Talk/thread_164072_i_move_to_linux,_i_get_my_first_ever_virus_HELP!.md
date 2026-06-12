---
title: "i move to linux, i get my first ever virus HELP!"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by kwyjibo on 2006-04-22
so i am a complete linux newbie, and recently installed ubuntu.  and then i start getting messages off all my msn contacts that i emailed them some rubbish that installed spyware. so obviously i have a virus, i assumed it woulda been windows  so did a scan and nothing, got some virus scanner for linux (aegis or something) and it's picked up absolutely loads of a w32 virus in my .wine directory and on loadsa dll on my NTFS mounts.

I'm a bit confused, how is it affecting the ntfs mounts as they are read only and i thought my wine directory had root permissions?  anyway more importantly what's the best way of fixing it, programs, possibly a howto?

Not the greatest introduction to linux to be honest, never get a bleeding virus ever and now i do... grrrrr

---

### Post by aysiu on 2006-04-22
Viruses can travel by email, and someone could be using your email account to send it to your friends--this is operating system-independent, as far as I know.

~/.wine is able to be modified by the user. It is not a root-owned directory.

---

### Post by DeusEx on 2006-04-22
obviously linux did not put the viri there, for ntfs is read-only in your distro.
and more over, w32 means it's only affecting a windows OS. Linux OS would think the virus was speaking chinese or something, it just wouldn't understand.

So probably somehow you yourself have installed something in Linux or Windows which has sent those e-mails.

Since the viri are on the ntfs partitions, windows must have put them there. I suggest you scan windows at boot time /  in safe mode. And DO NOT install multiple anti-virus pakkets in windows!

---

### Post by bscbrit on 2006-04-22
I agree with aysiu - this is more likely someone using your email address rather than your machine sending viri.

Windows cannot send viri while you are using linux UNLESS you have installed a specific program under wine that could do the task.  I cannot think of any innocent reason that you might do this and we can ignore the fact that you have done it intentionally - otherwise you wouldn't be asking for help.  If you want to use IM under Ubuntu, just use one of the linux equivalents.  Linux could transfer viri that are hidden in binaries or attached to emails which is why you shouldn't just relay emails without checking them out first.  You could use something like clamav to clean incoming/outgoing emails.  A Windows virus cannot run on your computer but it _is_ possible for you to pass a virus on unknowningly.

Ask the recipients to quote some times from the emails and, if you were using linux at that time, you can be reasonably assured that this is someone claiming to be you rather than something your machine is doing.  If however you had your machine booted in Windows at the time the messages were sent then it points fairly well at your Windows installation being infected.

---

### Post by kwyjibo on 2006-04-22
yeh i understand what you are all saying but there is no detection at all in windows, and the fact that when scanning in linux it is picking up viruses in the .wine folder surely means linux has something to do with it as windows doesn't even see the linux partitions.  a tad confused.

could running IE with wine cause a virus, or something?

---

### Post by bscbrit on 2006-04-22
YES!  You have just installed the weakest part of Windows software into your Linux system.  Why do you need to run IE under Wine?  Can't you use any of the many browsers provided with Ubuntu?

EDIT:  In an earlier post I referred to 'intentionally installing a specific program to spread viri'.  Although it wasn't intentional, you have probably achieved just that!

---

### Post by bscbrit on 2006-04-22
If it isn't an embarrassing answer - where did you get your software for IE and the associated dlls?  If it is from a legal Microsoft disk then I would be extremely concerned with the problem that you are having.  If it is from a pirated copy...... erm, I think that you might have learned a valuable lesson. ;)

---

### Post by linuxa on 2006-04-22
I'm sure that you are aware that IE has quite a few vulnerabilities (somewhat of a understatement I know :P).

And without running it in Windows, you are also not able to patch those vulnerabilities discovered & fixed by MS.

I'd go with **bscbrit**'s suggestion if I were you. Go with another Browser.

Most Browsers today have a non-existent learning curve when it comes to doing the basic surfing and what not.

If you are using KDE, you should have Konqueror installed already, which is a more than adequate File Manager/Web Browser.

For other choices:

You can try Firefox at:
[www.getfirefox.com](www.getfirefox.com)
(a lot of people prefer to download it using their package manager, but you can actually get the latest & the most secure version if you bypass the manager and install using the install script provided. Give us a shout if you need more instructions).

or my personal favourite:
[www.opera.com](www.opera.com)

Which is more feature packed (to anyone reading, this is **not** an open invitation for a flame war between firefox & opera :D).


For future reference, you might want to reserve Wine for those applications that you can't do without and with no equivalent on Linux (e.g. Windows Games). Most Windows applications have more than an adequate (in a lot of cases - superior) substitutes on Linux.

For a Window to Linux application mapping, try this excellent thread (sticky at the top of the forum):
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

Happy Linuxing :D

[EDIT: for spelling/grammar and other niceties :P]

---

### Post by r4ik on 2006-04-22
"Since the viri are on the ntfs partitions, windows must have put them there. I suggest you scan windows at boot time / in safe mode. And DO NOT install multiple anti-virus pakkets in windows!"

Very true.
This one you can try however give this a read,
Do not forget to update it before running.

[http://www.ewido.net/en/download/](http://www.ewido.net/en/download/)

Good luck ! 

It is a trail but worth downing and removing :)

---

### Post by linuxa on 2006-04-22
Also, you wouldn't happen to be running MSN Messenger in Wine as well? Cause that just might explain how you could both get the virus (through IE exploit when run in Wine), and how it is spread (through Messenger again in Wine).

Of course I'm not at all implying the Wine isn't safe, it's simply a platform for running Windows apps, it really comes down to thh the kind of app that determines how safe your system is. Good thing Linux is impervious to Window Viruses in most cases eh?

---

### Post by bscbrit on 2006-04-22
Just as a thought, if you want to run IE and MSN Messenger, you will find it far easier to run them under Windows because you will not have to waste time configuring them to run under Wine.

Of course, you might then have a problem with viri...... :D 

Switching to Linux was a wise move, installing Windows software to run under Linux is not quite as wise.

---

### Post by Kimm on 2006-04-22
Wine is not more secure then windows is, as the .wine directory is placed inside your home-directory any windows app can infect the existing "Wine System" just as easily as infecting a windows system - after all, the goal for wine is to run all windows apps inside Linux.
This means that any windows apps run in wine can attract and spread Windows viruses, Linux apps cant unless they where intentionally built to do so.
If you wish to have Windows applications running all the time you should also have some sort of WIndows AntiVirus running to scan the .wine directory, since wine technicly needs this just as much as windows does. 

Also, you should try to run Linux equailents to  your "normal" windows apps, both to ease the transition and to releave the computer from some reasure, there are many exelent Webbrowsers and e-mail clients for Linux, mozilla firefox and thunderbird for example.

---

### Post by kwyjibo on 2006-04-22
ah thanks for all the comments... i only installed wine cos i wanted to get a program called voipstunt working, but in the end managed to find a linux client and found out the SIP settings, so i suppose i could uninstall wine completely now.  and hopefully that will fix the issues.

only thing of concern is that my ntfs mounts in linux was detecting that lots of dll files were infected, a reboot and scan in windows didn't show anything so i'm kinda thinking/hoping these were false reports as linux shouldn't be able to edit the ntfs partitions anyway.

i'll start up linux soon and get rid of wine, and let you know

---

### Post by airtonix on 2006-04-22
ummm wouldn't this indicate how bad windows and windows-like apps are at detecting binary patterns? like viri. is that a virus checker in your pocket or are you just glad to see me running in root?

---

### Post by Kimm on 2006-04-22
> 
only thing of concern is that my ntfs mounts in linux was detecting that lots of dll files were infected, a reboot and scan in windows didn't show anything so i'm kinda thinking/hoping these were false reports as linux shouldn't be able to edit the ntfs partitions anyway.


Dont be sure its false reports. What AntiVirus program are you using in Windows?
Different AntiVirus programs can detect different viruses, and if the AntiVirus program is common, viruses can find its program files and rewrite them.

I take it your running ClamAV in Linux? I think theres a windows version for that...

---

### Post by olsonar on 2006-04-22
Unistalling wine is a good move. In windows, I run the free AVG anti-virus (free.grisoft.com). I also use the free ZoneLabs ZoneAlarm firewall ([www.zonelabs.com)](www.zonelabs.com)). The firewall alone blocks most viruses and spyware, but you'll want the anti-virus to get rid of what you already have. Ever since I installed ZoneAlarm, I have had no virus infections whatsoever in Windows.

---

### Post by Mustard on 2006-04-22
If my computer got infected, I wouldn't even bother trying to disinfect it.  It's like chasing a needle in a haystack and I would never feel completely secure about the operating system again.  The ability for someone to install a trojan and then install a rootkit, which could theoretically make the intrusion undetectable is something I couldn't ignore.  If it were me, I would be formatting and reinstalling windows and then never allowing windows access to the internet again.

Just as an aside, I purposely infected a Wine installation once just to see what would happen (using a virus I received in an email).  It's quite amazing how deeply into your system it can get.  I ended up reinstalling linux too after that, because it downloaded about 100 different versions of itself and stored them in all sorts of places I would never have thought Wine could access.  I didn't reinstall linux so much out of concern for what the viruses would do to linux, but more out of concern for any future installation of Wine.

---

### Post by wolfee on 2006-04-22
[QUOTE=Mustard]If my computer got infected, I wouldn't even bother trying to disinfect it.  It's like chasing a needle in a haystack and I would never feel completely secure about the operating system again.  The ability for someone to install a trojan and then install a rootkit, which could theoretically make the intrusion undetectable is something I couldn't ignore.  If it were me, I would be formatting and reinstalling windows and then never allowing windows access to the internet again.[/QUOTE]
  
;) I agree!!!!!!!!!!! Ubuntu for all your Ie needs and microshaft for things like 3dmax or other software that linux has nothing like. ( which really isnt much!! Linux has allot!!!!) Ya I would say keep yor microshaft xp "pro" an internet virgin and all will be well!!;)

---

### Post by nealklomp on 2006-04-22
[QUOTE=Mustard]If my computer got infected, I wouldn't even bother trying to disinfect it.  It's like chasing a needle in a haystack and I would never feel completely secure about the operating system again.  The ability for someone to install a trojan and then install a rootkit, which could theoretically make the intrusion undetectable is something I couldn't ignore.  If it were me, I would be formatting and reinstalling windows and then never allowing windows access to the internet again.[/QUOTE]
Chasing a needle trying/designed to hide.
And that is it right there.
I run Ubuntu on my laptop and XP on my desktop, it is just convenient for devices and ptp etc., but I wip the desktop OS every month or so; it is 24/7/365 connected to the net.

---

### Post by kwyjibo on 2006-04-22
i was thinking of doing a complete format, i got a windows ghost image so that's easy to do but as a linux newbie it took me bleeding ages to configure it how i wanted and now im gonna have to start again... nooooooo :(

---

### Post by DeusEx on 2006-04-22
avast is quite good too, and supported and free

---

### Post by AndrewCaul on 2006-04-22
The lessons here. Don't run IE or MSN Messenger on Wine if you don't have to and use decent virus detection software.
I'd better install a Linux anti-virus package and scan my NTFS partition now. Who knows what viruses could be hiding undetected?

---

### Post by IYY on 2006-04-22
> i was thinking of doing a complete format, i got a windows ghost image so that's easy to do but as a linux newbie it took me bleeding ages to configure it how i wanted and now im gonna have to start again... nooooooo 

Why do you need to reformat the Ubuntu partition?

---

### Post by BoyOfDestiny on 2006-04-22
[QUOTE=kwyjibo]ah thanks for all the comments... i only installed wine cos i wanted to get a program called voipstunt working, but in the end managed to find a linux client and found out the SIP settings, so i suppose i could uninstall wine completely now.  and hopefully that will fix the issues.

only thing of concern is that my ntfs mounts in linux was detecting that lots of dll files were infected, a reboot and scan in windows didn't show anything so i'm kinda thinking/hoping these were false reports as linux shouldn't be able to edit the ntfs partitions anyway.

i'll start up linux soon and get rid of wine, and let you know[/QUOTE]

Well if there were files on the nfts read only, those were there the whole time. For the ones in .wine, if you were running things off the ntfs, it's possible it copied them. AFAIK wine + windows apps == weakness to windows malware and viruses (although I don't think it would effect anything outside of the "fake c".)

Now, when you go to windows and scan it finds nothing... My first guess is your machine was infected by a rootkit. It can keep a set of files invisible to the OS and various apps. Other malware can take advantage of the rootkit as well (like with the Sony DRM 'fiasco') Distrubing huh? I would seriously reinstall or better yet remove Windows to be safe. That or try a different scanner and see if it picks things up. Adware for malware and clamwin for viruses...

---

### Post by AndrewCaul on 2006-04-24
I just ran the Aegis virus scanner last night. It showed a bunch of viruses, most of which were Netsky and Magistr. And Magistr was discovered in 2001, so I find it odd that it was never detected previously.
It might be a false positive. Is this virus known to affect installers, dlls, and the .NET Framework? Because that's where it found it.

---

### Post by linuxa on 2006-04-25
[QUOTE=wolfee] Ya I would say keep yor microshaft xp "pro" an internet virgin and all will be well!!;)[/QUOTE]

I actually thought about that when I first installed my Windows partition, however the need to download game patches and other Windows-Only software means that you'll always need some kind of Virus scanner to begin with. Might as well keep Windows connected but protected as opposed to downloading the stuff to Linux, and passing on potential viruses to an unprotected partition...

But yeah, I totally agree that a locked down computer - placed in a room with reinforced concrete walls, and no internet is a **moderately** ;) safe computer...

---

### Post by Caligula on 2006-04-25
well...
your problem is probably wine.
As far as I know, you don't need to have root permissions to install *.EXE files using wine.

So basically, using IE and wine is basically throwing away all the security linux provides us with and going back to windows...
Well, not totally, as not all viruses run on wine, but that's the idea...;) 

Better use stuff from the repositories... everything safe there...

---

### Post by steve.horsley on 2006-04-25
I would be inclined to try the clamav virus scanner on Linux. It might give you a feel for whether these are false positives - if clamav says you have an infection too, then it's beyond doubt, really. You can't really rely on windows based AV at this point - many viruses these days either hide from AV or at least disable AV so they can't be found. A scan of the NTFS disk run from another OS is much more trustworthy.

If the virus is there, you definitely passed it from Windows to wine rather than the other way, because Linux cannot write to NTFS partitions.

---

