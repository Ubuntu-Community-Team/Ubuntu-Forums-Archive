---
title: "security"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by eaststand on 2007-08-14
it says on the cover linux is free from viruses, but is that really true??? do I need antivirus and spyware software, I have installed firestarter but is that enough??

Also, torrents: is there anything available like peerguardian for linux that I dont have to 'untar' and do complicated things to make it work?? I cant find anything in the list of add/remove applications.

Thanks in advance, and I have to say, after the initial feeling of smashing my head into a brick wall, I'm starting to warm to linux, its very quick and smooth.

---

### Post by diatribe on 2007-08-14
no antivirus is needed and also firestarter is arguably not needed, and azureus is in the repos, and there is a linux client for peerguardian

[http://ubuntuforums.org/showthread.php?t=95793](http://ubuntuforums.org/showthread.php?t=95793)

---

### Post by Rocket2DMn on 2007-08-14
There have only been a handful of viruses made for linux and currently there are none "in the wild", meaning there aren't any active viruses.  The only reason to install a virus scanner is to prevent passing viruses on to windows users through email.  However, most of us feel that it is windows users' job to protect their own computer - don't waste your resources on it.

There are a bunch of torrent programs for linux including azureus, ktorrent, rtorrent, deluge, etc...
The only times you really ever need to untar anything is when you install programs manually, but most everything you need is in the repositories, you just might need to enable the universe and multiverse repositories.  System->Admininstration->Synaptic Package Manager: Settings->Repositories.

---

### Post by st33med on 2007-08-14
The reason why it is almost virus-proof is because of the password required for using things. A hacker could try to take control, but it needs your password to go any further.

That, and the fact Linux keeps open ports at a minimum.

---

### Post by yellowband on 2007-08-14
you actually always had the functinality of firestarter... well kindof.  firestarter is just a GUI frontend to iptables.  Iptables lets you rout traffic based on various rules (firewall ports).  

there is the clamAV antivrus server you could install from the repos quite easity.

In general though, because linux protects users from themselves via the use of a root account, it is tough to get control of resources needed by viruses (not to say that its impossible).

---

### Post by p_quarles on 2007-08-14
As others have pointed out, Firestarter is only a GUI tool, so simply installing it does very little. You can use it to create firewall policies for iptables.

There are security issues for Linux, but viruses are not one of them. The best practical advice for a beginner, imho, is the following:
1) Don't run any server software until you understand iptables
2) If you're using Firefox, install the Noscript and CookieSafe extensions.

---

### Post by eaststand on 2007-08-14
Right, ok, how do uninstall it?? think i've made a mistake along the way as it doesnt work (I'm talking about peerguardian howto) and there it isnt showing up in the add/remove thing, and all the deb installation lets me do is reinstall, which isnt what I want to do. 

And whats gedit?? I cant find an icon for that either.

thanks you by the way.

---

### Post by p_quarles on 2007-08-14
Uninstall what? Firestarter? Add/Remove shows a limited number of packages. For things that aren't there, you'll find them in System >> Administration >> Synaptic Package Manager.

Or, you can use the command line:
```
sudo apt-get remove firestarter
```
The program called "Text Editor" is Gedit.

---

### Post by bswilson on 2007-08-14
> **Rocket2DMn said:**
> There have only been a handful of viruses made for linux and currently there are none "in the wild", meaning there aren't any active viruses.  The only reason to install a virus scanner is to prevent passing viruses on to windows users through email.

I'll second these statements.  Most Linux users I know do interact with Windows machines, and that right there is reason enough to ensure that you have controls to prevent the spread of malicious programs.  Remember that just because there isn't currently a virus `in the wild` for Linux, that doesn't mean there never will be...

---

### Post by misfitpierce on 2007-08-14
From what i've read there have been only a few linux viruses ever created but they were never widespread over the internet. No antivirus needed. Firestarter is not a bad idea especially if no firewall on router. Firewall is never a bad thing.

---

### Post by Blutack on 2007-08-14
The nice thing about firestarter is you only need to run it when you want to change a config or watch stuff bounce off it.  Even if the gui ain't open it still works.

---

### Post by p_quarles on 2007-08-14
> **bswilson said:**
> I'll second these statements.  Most Linux users I know do interact with Windows machines, and that right there is reason enough to ensure that you have controls to prevent the spread of malicious programs.  Remember that just because there isn't currently a virus `in the wild` for Linux, that doesn't mean there never will be...
I think that running an av to stop Windows viruses from spreading is at the user's discretion. My attitude is that Windows users' security isn't my responsibility. 

As for the possibility of a Linux virus in the future, having an av scanner wouldn't help at all with that. It can only run tests for known viruses, and the virus itself would necessarily have to precede the creation of the ClamAV definition file.

---

### Post by bodhi.zazen on 2007-08-14
[Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Blutack on 2007-08-14
If you are smart about not forwarding any dodgy .exe's and open and resave any office docs you get as PDF's with OpenOffice there surely isn't much risk?

---

### Post by eaststand on 2007-08-14
thats good to know, great forum BTW, everything I've asked has been answered quickly and correctly, thats rare on forums. 

Peerguardian is my main concern, tho, dont want the MPIAA  getting me :(

---

### Post by eaststand on 2007-08-14
right this is getting annoying: following the how to, putting those codes in the terminal thing, and all I get are these errors what am I doing wrong???


[IMG]http://img239.imageshack.us/img239/4514/screenshotje7.png[/IMG]

---

### Post by Blutack on 2007-08-14
You are in the wrong directory.  First type
cd /home/liveforever/Desktop
then your dpkg stuff.
Why not just doubleclick on the .deb file though?

---

### Post by eaststand on 2007-08-14
I got confused the first time, so I thought i'd follow the instructions to the letter, of course!! Its so obvious now :) thanks. This switch has been one the most brain hurting things I've done in a long time, hopefully it'll click in my head soon.

---

### Post by p_quarles on 2007-08-14
The brain hurt just means you're learning quickly. :)

---

### Post by Rocket2DMn on 2007-08-14
> **bswilson said:**
> I'll second these statements.  Most Linux users I know do interact with Windows machines, and that right there is reason enough to ensure that you have controls to prevent the spread of malicious programs.  Remember that just because there isn't currently a virus `in the wild` for Linux, that doesn't mean there never will be...

However, if a virus is released, there will be a fix available for the vulnerability faster than it would take an anti-virus program to get updated database information.  Anti-virus software is reactionary whereas getting a quick update to fix the vulnerability is a preventive approach.  So in the end, the nature of open source software means viruses won't likely become a real problem.

---

### Post by eaststand on 2007-08-14
Final question on the matter: theres no icon for it, everything went through allright, got it to run on startup and update daily, but how do i know that its going to work everytime if theres no interface??

---

