---
title: "Firestarter &amp; Hackers"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-17
I've been reading around of people complaining taht they've been hacked.
I was worried and installed Firestarter. Immedietly I installed it, I noticed taht I was getting hits from the internet. Do those hits meant hackers trying to gain control of my computer?
Also, when I tell Firestarer to begin at startup, It says I'm not root and quits. I then have to start it manually. How do I make it begin at startup automatically.

Also, I've been hearing there is a way to read/see how many people have actually attempted to attack you. I mean read the IP's of people or bots after your computer. Where do I find this information.Thanks.1?1

:???:h34r: Jaygo333 :???:h34r:

---

### Post by kaamos on 2006-01-17
You start firestarter at startup by selecting this option in the firestarter preferences. The gui does **not** need to start when gnome kicks up because it is only a tool to change settings and to look at logs. The firestarter daemon is running fine without the gui.

---

### Post by heimo on 2006-01-17
[quote=Jaygo333]I've been reading around of people complaining taht they've been hacked.
I was worried and installed Firestarter. Immedietly I installed it, I noticed taht I was getting hits from the internet. Do those hits meant hackers trying to gain control of my computer?
[/quote] 
It's normal. Automated attacks, scans etc. It's going on all the time. As long as your computer doesn't have open services (Ubuntu does not have any outside listening services by default) and your computer is regularly updated, you're ok.

[quote=Jaygo333]
Also, when I tell Firestarer to begin at startup, It says I'm not root and quits. I then have to start it manually. How do I make it begin at startup automatically.
[/quote] 
  Firestarter is actually just a front end, user interface to make changes to firewall which is part of kernel (the actual part of your operating system that's called Linux). You do not need firestarter running all the time.

[quote=Jaygo333]
Also, I've been hearing there is a way to read/see how many people have actually attempted to attack you. I mean read the IP's of people or bots after your computer. Where do I find this information.Thanks.1?1
[/quote] I haven't heard of such thing. Your firewall logs could give some estimates, but there's no outside service that could give such information "universally". However, there's a "distributed" service which tries to answer the question if your computer is compromised (others reporting your IP as an attacker).
[http://www.dshield.org/]("http://www.dshield.org/")

These services can never be 100% accurate - or at least, you need to know how to interpret the information.

---

### Post by byen on 2006-01-17
If you are trying to install firestarter-gui during startup...this is what you do
_Step1_:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden 
Order: 20
(Notes: this is add firestarter to your start-up)

_Step2:_
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page 
username ALL=NOPASSWD:/usr/sbin/firestarter
(_insert your login user name in place of the username_)
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.

EDIT: I just found this[ howto .. might wanna look into it ]("http://www.ubuntuforums.org/showthread.php?t=110320&highlight=Launching+Firestarter+minimized+tray+login")

---

### Post by Jaygo333 on 2006-01-17
[QUOTE=heimo]It's normal. Automated attacks, scans etc. It's going on all the time. As long as your computer doesn't have open services (Ubuntu does not have any outside listening services by default) and your computer is regularly updated, you're ok.

 
  Firestarter is actually just a front end, user interface to make changes to firewall which is part of kernel (the actual part of your operating system that's called Linux). You do not need firestarter running all the time.

 I haven't heard of such thing. Your firewall logs could give some estimates, but there's no outside service that could give such information "universally". However, there's a "distributed" service which tries to answer the question if your computer is compromised (others reporting your IP as an attacker).
[http://www.dshield.org/]("http://www.dshield.org/")

These services can never be 100% accurate - or at least, you need to know how to interpret the information.[/QUOTE]

Thank's for all the tips. One Question though? Is it advisable to run your firewall at all times in Linux. 
Also, how does DShield actually work. It said my machine was not being used for cracking but what else can I do with the place.Help?
Thanks again for the advise.

:):h34r: Jaygo333 :):h34r:

---

### Post by Jaygo333 on 2006-01-17
[QUOTE=byen]If you are trying to install firestarter-gui during startup...this is what you do
_Step1_:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden 
Order: 20
(Notes: this is add firestarter to your start-up)

_Step2:_
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page 
username ALL=NOPASSWD:/usr/sbin/firestarter
(_insert your login user name in place of the username_)
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.

EDIT: I just found this[ howto .. might wanna look into it ]("http://www.ubuntuforums.org/showthread.php?t=110320&highlight=Launching+Firestarter+minimized+tray+login")[/QUOTE]

Thanks.1?1 Worked like a charm. 
Just finished restarting my pc and firestarter din't quit. 
Thanks Again.

:D:h34r: Jaygo333 :D:h34r:

---

### Post by byen on 2006-01-17
awesome! :-)
Glad I could help.

---

### Post by Jaygo333 on 2006-01-17
Hey byen,

Just as an offdity, do you know how to install shockwave.I've tried installing through synaptic but only flash shows and taht is installed. How do I install
it through terminal or synaptic.Any form accepted.

:confused:h34r: Jaygo333 :confused:h34r:

Checked thorugh
[http://www.macromedia.com/shockwave/welcome/](http://www.macromedia.com/shockwave/welcome/)

---

### Post by byen on 2006-01-17
[QUOTE=jaygo333]Just as an offdity, do you know how to install shockwave[/QUOTE]
Im sorry I dont think I would be able to help you much in that issue.. I dont think shockwave is supported in Linux (even after installing necessary progs/files). Infact here is a [petition ]("http://www.petitiononline.com/linuxswp/petition.html")goin on for this very reason. Sorry!! 

PS- Please note that I may be wrong. But I am sure about this to the best of my knowledge.

---

### Post by Jaygo333 on 2006-01-17
[QUOTE=byen]Im sorry I dont think I would be able to help you much in that issue.. I dont think shockwave is supported in Linux (even after installing necessary progs/files). Infact here is a [petition ]("http://www.petitiononline.com/linuxswp/petition.html")goin on for this very reason. Sorry!! 

PS- Please note that I may be wrong. But I am sure about this to the best of my knowledge.[/QUOTE]

Thanks, No Prob.
You seem to be the fastest help I've ever gotten here at the forums. 
If no problem to you, could I add yo to my buddy list. Would really help.

---

### Post by byen on 2006-01-17
sure.. 
And by the way...
Some seem to have some success running shockwave with Crossover
or with Wine (By Installing Firefox (windows version + Shockwave))

But as I said before..Im really not sure how well it runs...so you might wanna look around before you try...Sorry I cant give you more info abt this....
Goodluck!

---

### Post by Perfect Storm on 2006-01-17
Shockwaves runs perfect with crossover, but I havn't tried with wine, anyone?

---

### Post by Jaygo333 on 2006-01-17
[QUOTE=Artificial Intelligence]Shockwaves runs perfect with crossover, but I havn't tried with wine, anyone?[/QUOTE]

What exactly ins crossover?

How do  make shockwave run off it.

:h34r: Jaygo333 :h34r:

---

