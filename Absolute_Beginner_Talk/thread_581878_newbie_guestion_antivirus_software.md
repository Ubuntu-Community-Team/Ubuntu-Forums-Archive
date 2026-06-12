---
title: "newbie guestion: antivirus software"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by cybergalvez on 2007-10-19
Hi all, 
I know that in general linux does not need any anitvirus software, so here is my problem. I m going to build a new system and install ubuntu on it (desktop addition, but I will be running apache on it as I run a small personal webserver that I do access from outside my intranet, so I guess I should run a firewall) and I will be installing virtualbox with XP as a guest (there are some apps that still only run on windows that I need like Photoshop and my nokia phone stuff to get music on my phone). 

So with that as a background if for some reason I get a virus on the windows side would it be able to do any real harm to the linux side? granted I will have antivirus software on the windows side, and will use virutalbox's nat for windows internet access.  

Any and all help would be great
Jose

---

### Post by Pumalite on 2007-10-19
Windows cannot do anything to Ubuntu, but if you are in a LAN or Network with Windows you might acquire an anti virus for THEIR protection

---

### Post by Linux_Man on 2007-10-19
Short answer no. Longer answer, because your not really "installing" Windows onto your hard disk, a virtual Windows can do no harm to Linux at all, however you /may/ want to keep an Anti-Virus handy on your Windows partition because many spread Spam and other Viruses so you don't risk spreading it, you might want to consider anti-virus software on Windows, on Linux, the Viruses from a virtual Windows install can't do anything to it so don't worry and enjoy the freedom :popcorn:

---

### Post by Tyke91 on 2007-10-19
i have another question concerning this

i've had windows and linux dual booted on my computer now for half a year, and just recently i've found a driver for windows that allows it to read ext2-3 partitions. my question is - now that windows can read and write my linux partition, can viruses on windows harm linux? i've got antivirus software on my comp (avast, avg, adaware). but were a virus to make it through their scans, can it delete data on my linux partitions?

i'm not really worried about viruses on windows since i only websurf on linux ( i only use windows for half life 2, garrys mod, and oblivion anyway) but i want to ensure the safety of my precious linux :)

---

### Post by bloodniece on 2007-10-19
You can, however, pass on emails that have viral attachments to Windows users. *So, if you network with Windows users and care about this kind of stuff, you should install ClamAV.

---

### Post by bodhi.zazen on 2007-10-19
> **Tyke91 said:**
> i have another question concerning this

i've had windows and linux dual booted on my computer now for half a year, and just recently i've found a driver for windows that allows it to read ext2-3 partitions. my question is - now that windows can read and write my linux partition, can viruses on windows harm linux? i've got antivirus software on my comp (avast, avg, adaware). but were a virus to make it through their scans, can it delete data on my linux partitions?

If windows has your linux partition mounted rw, yes. linux partition(s) would be vulnerable to deleteion or alteration. 

And, my usual post :

Anti-Virus scanning on Linux is of limited utility as there are no know linux viruses "in the wild" so there is essentially nothing to scan for.

In addition Antivirus is reactive, not proactive meaning it can not protect you from the next Linux virus until AFTER it is released, not before.

A potential use of linux antivirus is to "protect" windows or if you are running a mail server, and even then, IMO, Windows antivirus is better then Linux antivirus.

In the end, the choice is yours to make, but I would be willing to bet that the more experience one has with Linux (Ubuntu) the less one feels the need for scanning / for 

viruses.

If you would like to learn a little about Ubuntu  security, see this link :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to discuss antivirus on linux, see this forum:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

Please keep this thread on topic, off topic comments to recurring discussions please.

---

### Post by tech9 on 2007-10-19
> **Pumalite said:**
> Windows cannot do anything to Ubuntu, but if you are in a LAN or Network with Windows you might acquire an anti virus for THEIR protection

LOL!

---

### Post by tech9 on 2007-10-19
> **cybergalvez said:**
> Hi all, 
I know that in general linux does not need any anitvirus software, so here is my problem. I m going to build a new system and install ubuntu on it (desktop addition, but I will be running apache on it as I run a small personal webserver that I do access from outside my intranet, so I guess I should run a firewall) and I will be installing virtualbox with XP as a guest (there are some apps that still only run on windows that I need like Photoshop and my nokia phone stuff to get music on my phone). 

So with that as a background if for some reason I get a virus on the windows side would it be able to do any real harm to the linux side? granted I will have antivirus software on the windows side, and will use virutalbox's nat for windows internet access.  

Any and all help would be great
Jose

If you are really concerned... you can always install clamav

sudo apt-get install clamav

---

### Post by cybergalvez on 2007-10-19
Thanks everyone for your replies, you've confirmed what I thought was the issue.  Since all my other Windows computers have AV software all ready installed, I think I'll just leave the clamav off the system and see how it goes
Jose

---

### Post by Tyke91 on 2007-10-19
thx for the heads up. 

do you know if there's a way to mount/unmount hard drives in windows? (i believe you can eject them, but how do you bring them back?)

---

### Post by Paulmd on 2007-10-19
> **cybergalvez said:**
> Hi all, 
I know that in general linux does not need any anitvirus software, so here is my problem. I m going to build a new system and install ubuntu on it (desktop addition, but I will be running apache on it as I run a small personal webserver that I do access from outside my intranet, so I guess I should run a firewall) and I will be installing virtualbox with XP as a guest (there are some apps that still only run on windows that I need like Photoshop and my nokia phone stuff to get music on my phone). 

So with that as a background if for some reason I get a virus on the windows side would it be able to do any real harm to the linux side? granted I will have antivirus software on the windows side, and will use virutalbox's nat for windows internet access.  

Any and all help would be great
Jose

In a semi-related note: I've seen at least 2 reports of successful Firefox hijacks, on this forum over the past month. Both of these were running Ubuntu linux.

---

### Post by Pumalite on 2007-10-19
> **Paulmd said:**
> In a semi-related note: I've seen at least 2 reports of successful Firefox hijacks, on this forum over the past month. Both of these were running Ubuntu linux.

I'd like to have the links if you have them.

---

### Post by bodhi.zazen on 2007-10-19
> **Paulmd said:**
> In a semi-related note: I've seen at least 2 reports of successful Firefox hijacks, on this forum over the past month. Both of these were running Ubuntu linux.

Yes, this is the problem with something like firefox that runs cross platform ... so the problem is not necessarily with the operating system.

My advice is to use a hosts file, use noscript, and block all cookies. Add trusted sites (like the Ubuntu forums) only for session and only as needed. It takes an extra few minutes to generate your white lists, but then you are set...

Or, run an alternate browser (Dillo ? kazehakase ? Opera ?) using Firefox only when needed.

=====

@Pumalite:

[http://ubuntuforums.org/showthread.php?t=535401](http://ubuntuforums.org/showthread.php?t=535401)

[http://ubuntuforums.org/showthread.php?t=577524](http://ubuntuforums.org/showthread.php?t=577524)

---

### Post by Paulmd on 2007-10-20
> **Pumalite said:**
> I'd like to have the links if you have them.

Sure thing: (I can't seem to locate the 2nd post, but it's more recent than this one)

[http://ubuntuforums.org/showthread.php?t=572033](http://ubuntuforums.org/showthread.php?t=572033)

Here is an older post

[http://ubuntuforums.org/showthread.php?t=535401&page=7](http://ubuntuforums.org/showthread.php?t=535401&page=7)

---

### Post by Paulmd on 2007-10-20
> **bodhi.zazen said:**
> Yes, this is the problem with something like Firefox that runs cross platform ... so the problem is not necessarily with the operating system.

My advice is to use a hosts file, use noscript, and block all cookies. Add trusted sites (like the Ubuntu forums) only for session and only as needed. It takes an extra few minutes to generate your white lists, but then you are set...

Or, run an alternate browser (Dillo ? kazehakase ? Opera ?) using Firefox only when needed.



I vote for Opera because it's lighter-weight (or at any rate I get much better performace) than Firefox, looks cleaner, and gets you everyhere you can go in Firefox (or IE for that matter)... Opera is also well-established (it's been around longer than Firefox, dating back before Netscape released their source code, that spawned mozilla),  it will run on Windows, MacOS, and Linux. 

Opera isn't immune either, however, neither Firefox nor Opera have near the number, or severity of successful hijacks, relative to IE.  I figure whatever browser you use,  assume it CAN be hijacked.

---

### Post by bodhi.zazen on 2007-10-20
> **Paulmd said:**
> I figure whatever browser you use,  assume it CAN be hijacked.

+1 ; it is in the nature of browsers independent of operating systems.

Take home message: learn to secure your browser.

---

### Post by tech9 on 2007-10-22
> **bodhi.zazen said:**
> Yes, this is the problem with something like firefox that runs cross platform ... so the problem is not necessarily with the operating system.

My advice is to use a hosts file, use noscript, and block all cookies. Add trusted sites (like the Ubuntu forums) only for session and only as needed. It takes an extra few minutes to generate your white lists, but then you are set...

Or, run an alternate browser (Dillo ? kazehakase ? Opera ?) using Firefox only when needed.

=====

@Pumalite:

[http://ubuntuforums.org/showthread.php?t=535401](http://ubuntuforums.org/showthread.php?t=535401)

[http://ubuntuforums.org/showthread.php?t=577524](http://ubuntuforums.org/showthread.php?t=577524)

Interesting

---

### Post by hyper_ch on 2007-10-22
[QUOTE=bodhi.zazen;3581269]+1 ; it is in the nature of browsers independent of operating systems.[QUOTE]

There is one browser that is dependant on the OS (or vice versa) and if that browser gets hijacked the evil-doers have full access to that machine. Now have a guess which one I'm speaking off. :popcorn:

---

### Post by tech9 on 2007-12-04
> **hyper_ch said:**
> [quote=bodhi.zazen;3581269]+1 ; it is in the nature of browsers independent of operating systems.[quote]

There is one browser that is dependant on the OS (or vice versa) and if that browser gets hijacked the evil-doers have full access to that machine. Now have a guess which one I'm speaking off. :popcorn:

let's see ... IE :lolflag:

---

