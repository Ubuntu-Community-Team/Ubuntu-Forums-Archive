---
title: "Newbie Question- Do you need Antivirus/firewall/spare protection for Ubuntu?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by UMD TERPS FAN on 2008-01-25
Newbie Question- Do you need Anti-virus/firewall/spare protection for Ubuntu?  If so where I can it? Also is there any free ware for Spy ware/firewall/Anti-virus?

Thanks,

Grant

---

### Post by frank002 on 2008-01-25
Ubuntu comes with a built-in firewall called iptables. To change the settings in it use Firestarter.  Download Firestarter from Applications>Add/Remove and search for Firestarter. You can also search for it using Synaptic. As far as antivirus, antispyware etc. they are not needed.

---

### Post by olskar on 2008-01-25
I am no sure, but I imagine antivirus is good if you communicate with windowscomputers a lot? If you gat a virus in a mail witout knowing it and perhaps sending it onto a windowscomputer or something

---

### Post by overdrank on 2008-01-25
> **UMD TERPS FAN said:**
> Newbie Question- Do you need Anti-virus/firewall/spare protection for Ubuntu?  If so where I can it? Also is there any free ware for Spy ware/firewall/Anti-virus?

Thanks,

Grant

HI and this link may help
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
also you may look here
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by RomeReactor on 2008-01-25
Hi. This is a question that comes up very frequently; do a search here for **antivirus** and you'll see many results. The short answer is, "for Ubuntu, no, you don't need an antivirus". As for the firewall, Ubuntu comes with a command line program called **iptables** that lets you create rules for incoming and outgoing traffic; you can install a graphical interface for it called Firestarter (look for it in 'System->Administration->Synaptic'). For more information, give these pages a read:

* [Ubuntu Security by bodhi.zazen]("http://ubuntuforums.org/showthread.php?t=510812")
* [Psychocats page on Ubuntu Security by aysiu]("http://www.psychocats.net/ubuntu/security")

---

### Post by UMD TERPS FAN on 2008-01-25
> **frank002 said:**
> Ubuntu comes with a built-in firewall called iptables. To change the settings in it use Firestarter.  Download Firestarter from Applications>Add/Remove and search for Firestarter. You can also search for it using Synaptic. As far as antivirus, antispyware etc. they are not needed.

After its installed, where is it located?

-Grant

---

### Post by RomeReactor on 2008-01-25
> **UMD TERPS FAN said:**
> After its installed, where is it located?

-Grant

Firestarter can be found in 'System->Administration->Firestarter' and 'Applications->Internet->Firestarter'.

---

### Post by JoshuaRL on 2008-01-25
Okay, that's a two part question.  First the firewall:  Yes, and Linux comes with a great one pre-installed.  And to mess with the settings you can download the Firestarter program.  It's a GUI frontend for the standard firewall iptables.

As far as anti-malware programs, no.  There are some, but they use system resources for no reason.  Currently there are no Linux viruses in the wild.  The OS is just much more stable and secure than Windows.  That's the beauty.

[http://ubuntuforums.org/showpost.php?p=1867793&postcount=85](http://ubuntuforums.org/showpost.php?p=1867793&postcount=85)

There's another one that has some great ideas about how to make sure you're secure.  I'll go try to find that.

---

### Post by JoshuaRL on 2008-01-25
> **overdrank said:**
> HI and this link may help
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
also you may look here
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Beat me to it.  Man, when I started typing there were NO responses.  Ha!

---

### Post by UMD TERPS FAN on 2008-01-25
Im trying to install Firestarter, but it wont. It dowloads and this quickly closes....man thats weird. 

-Grant

---

### Post by UMD TERPS FAN on 2008-01-25
whenever I go to add/remove programs, its say you need a working internet connection?  I'm using one right now?

-Grant

---

### Post by RomeReactor on 2008-01-25
Did you have a working internet connection when you installed Ubuntu? If not, then the repositories were disabled by the system; in Synaptic, go to 'Settings->Repositories' and on the first tab (Ubuntu Software) make sure the boxes for **main, universe, restricted** and **multiverse** are checked (see attached screenshot). Close that window and, still in Synaptic, press the blue 'Reload' button. You can then install Firestarter.

---

### Post by Casual Fan on 2008-01-26
Remember, if you're behind a router, you really don't even need a firewall.

---

### Post by UMD TERPS FAN on 2008-01-30
What about spyware/mailware?

-Grant

---

### Post by Abu_Dayya on 2008-01-30
The main reason that made me switch from Windows to Linux is 'No Malware'

That and free software

---

### Post by gn2 on 2008-01-30
> **Casual Fan said:**
> Remember, if you're behind a router, you really don't even need a firewall.

Depends on the hardware, not all routers have built-in firewalls.

---

### Post by Abu_Dayya on 2008-01-30
Accualy I heard that Windows is prone to viruses becuase  Microsoft made a mistake i early Windows versions that any program that has admin permitions can kill or modify other programs, and fixing this will compromise their backward and forward compatibility, so they didn't fix it. And this is not the case in Linux. 

Is this true?

---

### Post by scorp123 on 2008-01-30
> **Abu_Dayya said:**
>  Accualy I heard that Windows is prone to viruses becuase  Microsoft made a mistake ...  "a" mistake? Like in "one mistake"? :) They made ***many*** mistakes. For one, Windows was never really planned as multi-user operating system. Until the release of Windows NT 3.xx it even did not have real multi-tasking. And the home user versions Windows 1.x-3.x, Windows 95 + 98, Windows ME where nothing but a rather shaky wannabe pseudo-multitasking GUI on top of a single-user + single-task operating system: MS-DOS ... because that's what those GUI's in reality had underneath.

Linux was designed with being UNIX-like, and UNIX was designed from start as being multi-tasking + multi-user.

The difference is obvious. Having multiple users logged in on a Linux or UNIX system at the same time doing different things with different programs is probably a "most natural thing" ... this is exactly what it was designed for. On Windows however programs are still struggling ... many programs are still designed with being single-user and single-task in mind.

> **Abu_Dayya said:**
>   in early Windows versions that any program that has admin permitions can kill or modify other programs See above. Early versions of Windows home user products were in fact running on top of MS-DOS which technically was a single-task and single-user OS which crashed very frequently because there was no real memory protection whatsoever, each dirty written program could easily take over the entire RAM or CPU power if it wanted to (there was no sophisticated execution scheduler or "task manager" that would prevent programs from doing that!) ... the problem was when two programs tried that at the same time ... voila, crash!

I use computers since 1985 and I remember those times very well  :)

> **Abu_Dayya said:**
>  and fixing this will compromise their backward and forward compatibility, so they didn't fix it.  There is more to this. Microsoft is struggling with this since they abandoned the MS-DOS parts underneath Windows, starting with professional products such as Windows NT and then Windows XP on the home user front. The problem is that some programs simply won't run if they don't get full access to the full hardware, ie. they can behave like in the old days of MS-DOS. The problem is: The only user account really having always full access to the full hardware is the administrator account .... So that's why many programs insist on being run with "administrator" priviledges, they want full access to everything like on old MS-DOS. So it's partially also the fault of those application programmers.

But Microsoft made other mistakes too ... Take a look at all the various network services a normal Windows box is running. I am not talking about a server here, I really mean a plain + simple + stupid home user installation. There are sooo many unneeded stupid and insecure services always running in the background, always waiting for connections from anywhere, with no security whatsoever in place. Stupid old protocols that were once invented in the early 1980's or even before .... Microsoft is still using lots of such stuff. 

But instead of fixing those security holes by shutting down those stupid old network services they came up with the stupid (because easy to get around!) "Windows Firewall" ... which wouldn't be needed in the first place if a Windows installation wouldn't be running so many vulnerable stupid services in the first place.

The sad thing is that people got so used to having this crap firewall and having crap network services always on in the background that one of the first things newly converted users ask is "Does Ubuntu have a firewall .... "

> **Abu_Dayya said:**
>  And this is not the case in Linux.  See above. UNIX-like operating systems were designed from start as being multi-tasking and multi-user capable.

---

### Post by Abu_Dayya on 2008-01-30
> **scorp123 said:**
> "a" mistake? Like in "one mistake"? :) They made ***many*** mistakes. For one, Windows was never really planned as multi-user operating system. Until the release of Windows NT 3.xx it even did not have real multi-tasking. And the home user versions Windows 1.x-3.x, Windows 95 + 98, Windows ME where nothing but a rather shaky wannabe pseudo-multitasking GUI on top of a single-user + single-task operating system: MS-DOS ... because that's what those GUI's in reality had underneath.

Linux was designed with being UNIX-like, and UNIX was designed from start as being multi-tasking + multi-user.

The difference is obvious. Having multiple users logged in on a Linux or UNIX system at the same time doing different things with different programs is probably a "most natural thing" ... this is exactly what it was designed for. On Windows however programs are still struggling ... many programs are still designed with being single-user and single-task in mind.

 Early versions of Windows home user products were in fact running on top of MS-DOS which technically was a single-task and single-user OS which crashed very frequently because there was no real memory protection whatsoever, each dirty written program could easily take over the entire RAM or CPU power if it wanted to (there was no sophisticated execution scheduler or "task manager" that would prevent programs from doing that!) ... the problem was when two programs tried that at the same time ... voila, crash!

I use computers since 1985 and I remember those times very well  :)

 There is more to this. Microsoft is struggling with this since they abandoned the MS-DOS parts underneath Windows, starting with professional products such as Windows NT and then Windows XP on the home user front. The problem is that some programs simply won't run if they don't get full access to the full hardware, ie. they can behave like in the old days of MS-DOS. The problem is: The only user account really having always full access to the full hardware is the administrator account .... So that's why many programs insist on being run with "administrator" priviledges, they want full access to everything like on old MS-DOS. So it's partially also the fault of those application programmers.

But Microsoft made other mistakes too ... Take a look at all the various network services a normal Windows box is running. I am not talking about a server here, I really mean a plain + simple + stupid home user installation. There are sooo many unneeded stupid and insecure services always running in the background, always waiting for connections from anywhere, with no security whatsoever in place. Stupid old protocols that were once invented in the early 1980's or even before .... Microsoft is still using lots of such stuff. 

But instead of fixing those security holes by shutting down those stupid old network services they came up with the stupid (because easy to get around!) "Windows Firewall" ... which wouldn't be needed in the first place if a Windows installation wouldn't be running so many vulnerable stupid services in the first place.

The sad thing is that people got so used to having this crap firewall and having crap network services always on in the background that one of the first things newly converted users ask is "Does Ubuntu have a firewall .... "

 UNIX-like operating systems were designed from start as being multi-tasking and multi-user capable.

Wow. This is too much....

Thank you for the clarifications

---

### Post by Techwiz on 2008-01-30
Nope. That simple. I have none and have had no trouble.

---

### Post by scorp123 on 2008-01-30
> **Abu_Dayya said:**
>  ... that any program that has admin permitions can kill or modify other programs ...  Something I think I need to clarify here: Obviously ***any*** program that runs with "administrator" or "root" priviledges will be able to do that, e.g. kill or destroy other programs. Yes, also on Linux. But the big difference is this: On Linux there are only very very very few programs that really need the powers of the "root" account, you really rarely use them. On Windows on the other hand every silly and stupid program demands to have "administrator" powers!

Obviously, the more you have to use programs with such almighty and therefore "dangerous" priviledge levels the more likely "accidents" will happen.

That's why on Linux you're told again and again and again: Never ever work as "root" or use "sudo" or other 'dangerous' commands unless you really really have to.

On Windows? Being logged in with "administrator" powers is considered "normal" here ...

---

