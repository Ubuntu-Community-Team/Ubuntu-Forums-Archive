---
title: "[SOLVED] Security Suite"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by joeartis on 2008-04-01
I use Kaspersky Internet Security Suite on my Windows machines. Has anybody tried their software for a linux workstation. It doesn't say that it can be used on Ubuntu but Debian does get a mention. All help greatfully received.

---

### Post by twright on 2008-04-01
it would work but you really don't need to bother, out of the box ubuntu is more secure than windows with any security application combo (even kaspersky)

anti viruses are only needed on windows because Microsoft have made such a insecure OS

really unless you allow a program to run as root, on the desktop there isn't much to worry about

the main use for anti virus programs for linux is in large networks to make sure that you aren't receiving infected files and passing them on to less well protected windows machines (linux doesn't know or care whether a file contains a virus)

---

### Post by marpstar on 2008-04-01
> **twright said:**
> anti viruses are only needed on windows because Microsoft have made such a insecure OS

Although I agree that running an AV on Linux is unnecessary, I wouldn't say that anti-viruses are because Microsoft has made an insecure OS.  When you've got over 90% of the world's computers running Windows, what would you expect the viruses to be written for?  

In that most recent hacking contest, pwn 2 own, the Mac OSX machine went down before the Vista machine, and I wouldn't recommend Antivirus for a Mac either...

---

### Post by pseudo-random on 2008-04-01
Whilst linux is not immune to viruses, I'm not aware of any examples of linux home users becoming victim to random malware. Sure, Linux web servers get pwned by zero day worms etc but thats different.

---

### Post by imT on 2008-04-01
> **marpstar said:**
> In that most recent hacking contest, pwn 2 own, the Mac OSX machine went down before the Vista machine, and I wouldn't recommend Antivirus for a Mac either...
hacking is a lot different than viruses, spyware or malware,
in linux are not viruses because they would simply won't work, all the linux software is administered by an open community, the only way you can harm your pc in linux is to run untested applications from the net or to run some malicious commands as root.

---

### Post by t0p on 2008-04-01
> **twright said:**
> it would work but you really don't need to bother, out of the box ubuntu is more secure than windows with any security application combo (even kaspersky)

While what you're saying is true, it's important not to become complacent about security.  Linux is certainly less vulnerable than Windows, but that *doesn't* mean Linux is *invulnerable*.

All computer users need to have good security awareness and to practise caution.  Especially if you are using an untrustworthy network like the internet, you need to remember that many security issues are operating system-agnostic.  *Be careful, everyone!!!*

---

### Post by marpstar on 2008-04-01
> **imT said:**
> hacking is a lot different than viruses, spyware or malware,
Agreed, but bugs and exploits are the basis for many viruses, it goes to show that nothing is bug free...

> 
in linux are not viruses because they would simply won't work, all the linux software is administered by an open community, the only way you can harm your pc in linux is to run untested applications from the net or to run some malicious commands as root.

You can't say that viruses on Linux aren't POSSIBLE. 

If everyone surfed the internet on a limited user account from within Windows, you'd see a reduced risk of infection, much like not running everything as root in Linux.

I'm by no means saying that Linux and Windows are equivalent on a security standpoint, because they're not.  These are computers... ANYTHING is possible...

---

### Post by Mogurijin on 2008-04-01
Well none of you answered his question ;). If you wanted to run it, Ubuntu is Debian based. If the people who made the software says it will run on Debian, your probably fine with Ubuntu.

---

### Post by zvacet on 2008-04-01
I think [this](http://ubuntuforums.org/showthread.php?t=510812) can put some light on topic.

---

### Post by twright on 2008-04-01
i'm not saying they can't happen (i do try to take as many precautions as possible on my server), i'm just saying that for the average desktop user the risks of any threat which does require root access are much lower than those of say hard drive failure or acidentally overiding partitions. i think that the design of windows does definelty contribute the the rate of infection, its lack of package management, running as root mentality and the fact that it costs money (so many people still run old versions) are the biggest problems in my eyes.

anyone other than enterprises and sysadmins can just relax and get on with using it > **marpstar said:**
> Agreed, but bugs and exploits are the basis for many viruses, it goes to show that nothing is bug free...



You can't say that viruses on Linux aren't POSSIBLE. 

If everyone surfed the internet on a limited user account from within Windows, you'd see a reduced risk of infection, much like not running everything as root in Linux.

I'm by no means saying that Linux and Windows are equivalent on a security standpoint, because they're not.  These are computers... ANYTHING is possible...

---

### Post by joeartis on 2008-04-02
Thank you all. I'm going to leave installing any security suite for 6 months and see what happens. If everything stays secure I will Ubuntu my other machines.

---

### Post by misfitpierce on 2008-04-02
Anti-Virus is good to have as a side tool if you communicate with windows machines and get content off the world wide web... why? Simple, It is still possible for you to pick up a virus and although it cannot open or execute on your machine it is possible to pass that virus in that file along to a windows user and mess up his/her machine. Think about others as well when computing rather than just yourself and it can keep everyone safe... :)

---

### Post by GOROSSI on 2008-04-02
> **joeartis said:**
> Thank you all. I'm going to leave installing any security suite for 6 months and see what happens. If everything stays secure I will Ubuntu my other machines.

If your that worried about security run AVG free there is a linux version [http://free.grisoft.com/doc/5390/us/frt/0?prd=afl]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl") download the .Deb file runs fine on Gutsy but I suggest to run it from ternimal using this command:  
**sudo avggui**  As the updater for the software needs root privileges to work.

as for firewall Ubuntu has all it's ports stealth by default and if you do like to monitor traffic you can install firestarter (a gui front end for the IP tables firewall thats part of the Linux Kernel. ) from add/remove programs.

anyway if your behind a decent wireless router say a netgear one they have good firewalls on them so you shouldn't need t if thats the case.

One of the reasons their hardly any virus's etc for Linux is as the people who write them use Linux and don't want to be infected with their own nuisance plus the small user base.

---

### Post by hyper_ch on 2008-04-02
> **marpstar said:**
> I wouldn't say that anti-viruses are because Microsoft has made an insecure OS.  When you've got over 90% of the world's computers running Windows, what would you expect the viruses to be written for?

I would say so... number of installs do not have as a big meaning as you think. Assume for example there are 70% linux installs and 30% windows installs. Now, which OS would you target for exploits? The one that can be very easily hacked and has a very bad security record (mostly resulting from it's base design) or the one with a majority of users but which will ask you a lot more to do in order to get your virus in and run and spread?

---

### Post by twright on 2008-04-02
though most webmail scans automatically anyway :)
> **misfitpierce said:**
> Anti-Virus is good to have as a side tool if you communicate with windows machines and get content off the world wide web... why? Simple, It is still possible for you to pick up a virus and although it cannot open or execute on your machine it is possible to pass that virus in that file along to a windows user and mess up his/her machine. Think about others as well when computing rather than just yourself and it can keep everyone safe... :)

---

### Post by bred on 2008-04-02
don't need to bother, out of the box ubuntu is more secure than windows!
read this thread [http://ubuntuforums.org/showthread.php?t=694198]("http://ubuntuforums.org/showthread.php?t=694198")
good luck

---

