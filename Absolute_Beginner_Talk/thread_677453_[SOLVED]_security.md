---
title: "[SOLVED] security????"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-24
I am new to Ubuntu and Linux. I have always used windows where you have antivirus and windows  firewall. I have heard that with linux there is no need for antivirus is this true? I have just installed ubuntu gutsy and i wanted to know what do i need to install to make my computer safe? Do I need to take any precautions to prevent intrusion? Do I need anti virus how do i set up a firewall?
any info at all would be appreciated because i am clueless.

---

### Post by taurus on 2008-01-24
I've used Linux for years and never even once installed an antivirus for it!  Don't need it and don't want it.  Also, there is already a firewall built in, iptables, so no need to worry about that, either.

This is Linux, NOT windows.

---

### Post by Paul820 on 2008-01-24
You don't need a antivirus program as there are nearly zero virus' for linux. But if you are swapping files between a linux system and a windows system then for piece of mind you can install **clamav**. Linux/ubuntu has a built in firewall so there is no need to install one, if you want to configure the settings for it then download **firestarter**. Both of these programs are available through the synaptic package manager.

---

### Post by p_quarles on 2008-01-24
A great introduction to how security works in Linux:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by PeterJS on 2008-01-24
And as ever I'll plug Bodhi's security guide:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Beaten by seconds :)

---

### Post by glotz on 2008-01-24
On a GNU/Linux system the safety comes from what you *don't* install! :)

---

### Post by AnonCat on 2008-01-24
I think it's difficult to wrap one's mind around the idea of not having any anti-virus program if you're just coming from Windows, but eventually you'll stop worrying about it.  The only reasons to have anti-virus for Linux is if you download programs meant to be installed in Windows or to stop email viruses from spreading to Windows machines.

---

### Post by tjwoosta on 2008-01-24
hey thanks that info was usefull

---

### Post by Herman on 2008-01-24
Last week I used one of my Ubuntu systems to capture a nest of Windows viruses and quarantine them for analysis.
Ubuntu eats viruses for breakfast. It spits out the bones. :lolflag:

The viruses disrupted the computer owner's business so much that the windows owner has decided to purchased a whole new computer.
I'll have the infested one to next week for re-installing.

Unfortunately some people do still need Windows, only because there are certain kinds of professional software written for it that their businesses depend on.
It certainly must cost business a lot of money to be interrupted by viruses and malware, all the time when they have to run such a vulnerable operating system.
I'm sure that when more people take up Linux and learn to write programs for businesses, almost all businesses will switch to Ubuntu as fast as they can.

When that happens, there will be a landslide, because then the rest of the software writers will have to follow suit or go out of business.

Regards, Herman :)

---

### Post by confused57 on 2008-01-25
> Ubuntu eats viruses for breakfast. It spits out the bones. 
Succinct, but accurate analysis...LOL  That's a good description, Herman.

I recently received an email "Valentine Attack Notice", which mentioned not to open any Valentine's emails which could infect your pc with the W32/Dref-AB worm...forwarded the notice to all my Windows email buddies....then deleted the email, since I'm using Ubuntu there was no concern on my part for my pc getting infected.

---

### Post by tjwoosta on 2008-01-25
so what if you have windows on another partition? does that make a difference?

---

### Post by p_quarles on 2008-01-25
Not for Ubuntu. When one OS is running, the other doesn't affect it at all.

---

### Post by Herman on 2008-01-25
Most of or almost all viruses can be found in Windows, because Windows lets them in in various ways, or the virus writers figure out ways to sneak them in, Usually by enticing the Windows sufferer with some nice game or software that's attractive, or by using all kinds of other tricks. In my friend's case, ironically, the viruses were installed by a fake antivirus software that he actually paid for.

A virus can be passed through a Linux file system, but I don't think it would be able to do anything while it's there. If you transferred an infected file into Windows from Ubuntu though, the virus might become active when it gets into Windows.
A virus can't cross the boundaries of a hard disk partition by itself, it can only get through if we copy it through inside some other file.
It's a good precaution to scan files on their way in and on their way our of your Wndows box, no matter where they came from or where they are going.
A separate shared data partition is great for that, to act as a half way staging point, or a USB flash memory stick would be just as good.
Just because a file has been scanned though, doesn't guarantee that it's safe. New viruses get written every day, and the antiviruses don't recognize them until someone reports them and they figure out a way to deal with them first.
Have you ever seen a message from an antivirus company that says something like " sorry, we goofed, you have a virus but we have no idea how to deal with it yet, our bad"? I don't think that's likely, they'd keep it a sectret until they figure out what to do, then make themselves out as your heroes for being clever enough to be able to beat the bad virus.

That's why I switched to Ubuntu. A virus was discovered in my Windows computer that must have been in there for at least six months before they found it. And all the while they kept telling me my computer was safe. I will never believe that again.

You can protect your Windows computer by restricting its exposure on the internet to only trusted sites like your Windows Update and your antivirus and antispyware update sites, and possibly just a few other sites like those.
Apart from that, if you use Ubuntu for all your web browsing, and collecting your email, you'll find your Windows will stay as clean as a whistle.

Ubuntu doesn't seem to be affected by viruses or suffer from things like 'drive by downloads' or things like that because it's designed better from the ground up.
It is still possible for Ubuntu to have bad software installed in it by users if they are gullible enough to install it themselves, usually requiring the sudo password.
The purpose of having to type 'sudo' before we apply a command that will make system-wide changes is to make us stop and think first.

Most of the time we don't install software in Ubuntu that doesn't come from the official Ubuntu repositories. The developers are registered with coded GPG keys so only trusted software programmers can submit code to the repositories, and there are verification keys built into out apt-get program that we use to get updates through or install added software.
Those who enable foreign repositories or install software from somewhere other than the official repositories should be aware of the risk they are taking and make sure they trust the source of their new software.
That makes it just about impossible to install bad software in Ubuntu, but nothing is 100% foolproof. A few users still install foreing software if it will do some job they want badly enough. Not all foreign software is necessarily bad either, most of it is okay, it's just that the potential is there for something to be wrong with it. 
With open source software, we're supposed to be able to access the source code so we can check it for ourselves if we're able to read code, to see what it will do. We are even allowed to edit it ourselves to do what we want.
Mostly, if there was bad software around, it would have a bad name here in Ubuntu Web Forums fairly quickly.

Well, he he, that's my rant for today,
Regards, Herman :)

---

### Post by TorqueyPete on 2008-01-26
> **Herman said:**
> Last week I used one of my Ubuntu systems to capture a nest of Windows viruses and quarantine them for analysis.
Ubuntu eats viruses for breakfast. It spits out the bones. :lolflag:


A nest! LOL :lol:

The more I use Ubuntu, the more I'm liking it.

---

