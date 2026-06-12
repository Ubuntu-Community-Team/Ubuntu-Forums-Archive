---
title: "Ubuntu problems"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2006-11-28
First of all I am really an absolute beginner to Linux trying hard to migrate from Mcsoft.
 I have downloaded Ubuntu 6.10. Tested the CD. All checksums were correct. After installing I have a few problems. 
The search for files function does not work. No matter what I type (even Ubuntu) the answer is: File not found.
I cannot connect to my mail server. With Thunderbird I get: Please type valid Host name.
If I try to use Evolution Mail: server does not exist.
The server does exist. I am using the same configuration as I am using on the drive (seperate) I have XP on.
No problems with Firefox and Internet access.
I have more issues, but I better do a separate post after these hopefully are solved.
I really would appreciate your help. I do not like Microsoft and what it stands for. 
I love what I have seen of Linux and do not want to go back
Thanx in advance

---

### Post by nickburns on 2006-11-28
> The search for files function does not work. No matter what I type (even Ubuntu) the answer is: File not found.

You need to keep in mind that the file system on linux is case sensitive, and that you have to use file extensions on your search.  On my search, I have to remember that the search works only in my home folder, unless I change the drop down option.

---

### Post by turbojugend_gr on 2006-11-28
If you search for "Desktop" to you get a folder? Note Linux is case sensitive, this means A is different from a, and S is  not s.

---

### Post by Chamelion on 2006-11-28
Thank you heaps.
 I was not aware about the case sensitive. Again please have patience, after all right now I am still a stupid XP user:confused: I literally have been with Linux only a few days. If I can solve the problem with my mail server I can make Ubuntu my main OS.

---

### Post by Zaen on 2006-11-28
Hooray, another windows-addict (hopefully) on rehab good luck (from a fellow ex-windows user)

---

### Post by nickburns on 2006-11-28
I loved to ditch windows, you'll never look back. These forums are great b/c most everyone is nice.  Hope the search help was helpful, now lets look at the mail problem.

Are you planning on using Evolution or Thunderbird?

if you open a terminal and type:

ping youremailserver.com  

do you get a responce? (btw user ctrl+c to stop pinging)

if your using evolution, go to the form where you add the account and put in the mail server and your user account and press the check login types, what do you get?

also what type of mail server is it? Exchange? Pop? Gmail?

---

### Post by 3rdalbum on 2006-11-28
The Nautilus search function is a little buggy, I find. If you find that too, and you don't mind putting bits of KDE onto your system, you could install kFind from the Synaptic Package Manager.

---

### Post by turbojugend_gr on 2006-11-29
Well Chamelion, are you sure your are typing your mail servers name in the correct case? again this might be caused bercause you type AOL.mail.com instead of aol.mail.com, as an example. Generally type all info in lower case letters, cause it is the most usual case when it comes to mail servers.

Please let us know of your progress, if this doesn't help you should try what nickburs is suggesting. Also make sure you clarify ,if you use pop, imap, or whatever else possible.

Cheers, TJ.

---

### Post by Chamelion on 2006-11-30
Thank you all again
The friendliness of this place does help in the transition. The case sensitive info has helped me to find my files. The mail server thing was entirely my fault. I did make a mistake. It is working now.
There are a few minor things I have to learn. I have a firewall sitting on my desktop and am not sure how to install. So I open a terminal and just start typing what is in the install instructions?
I also have a virus program installed. Thanks to your help I can find the files now. It does not show up under applications though. Do those things just run silently in the background in Linux? (Aegis virus scanner) Is there  any way to scan on demand?
I think I make it through "rehab" Zaen. Thanks for the encouragement.LOL
Cheers to all:-D

---

### Post by nickburns on 2006-11-30
So you have a firewall and antivirus installed?  Or you want them installed?

I have had Ubuntu for a while and I don't really think firewall and antivirus are necessary.

If they are installed and your having problems, then what is the software and the problems and we can help you out.

---

### Post by turbojugend_gr on 2006-11-30
i 've been saying it all around, but I can't help it, it's well documented, pretty well known, yet people don't seem to believe it i guess, don't be afraid  guys...it's true...Linux has NO viruses !

It is absolutelly safe and normal, you won't ever need an antivirus installed, except if you want to to scan your windoz partition, while in ubunt, or you massively forward e-mails, in any case that could be described as you being the Policeman to Microsoft's virus issues (as a fellow in here once said).

I don't mean to urge uninstalling your application, but I believe that you should know things here are different, better, safer for you. You should just enjoy your time here, no need to live in a virus-terror situation now.

I won't mess with helping you use that antivirus, cause I only believe ion prividing Helpful advice (if someone else here things it suits him to explain this to you, I 'll be glad, cause I 'll avoid the temptaion of solving your querry).

For the firewall now, which is only neccessary to open ports and stuff, rahter than guarding you sysstem I would be glad to help you (if I am able to), which one is it?

P.S: PLZ, oh PLZ, don't judge me bad now, keep your system for one whole year without a antivirus, see how great it is, and then you will be able to judge me better, all thisd of course only stand, if you are in the false impression you need an antivirus, so as to avoid ubuntu crashes. IMHO what you need to avoid this, is limited curiosity/energy to mess up with stuff, and learn by breaking your system, ;).

---

### Post by Chamelion on 2006-11-30
I installed the virus program through add/remove programs. (one of the packages, Aegis) I know it is there (I found the files) but I can't find the application itself.
I just wonder if it just runs in the background or if there is a way to run it on demand.
The Firewall is not installed yet. It just sits on my desktop. There is a file in it saying "Ubuntu-firewall-installer.sh". If I open it, it comes up with the options: Run in terminal, display, run. If I just click on run nothing happens. With run in terminal, Terminal pops up for a split second and disapears again.  Just clicking on things does not seem to work with Linux. 
Display gives install/uninstall directions. And they look confusing to an, hopefully,:D  ex MS user like me.

---

### Post by Chamelion on 2006-11-30
turbojugend_
Just read your message. I had it installed already. If that is the case I might consider uninstalling. I do not send many messages on and am very careful with what I open.
It just would be good to know how these things work in Linux.
That just would leve the firewall and maybe a few tips on installing in general. 
I might also go and read the tut's on the Linux site.

---

### Post by nickburns on 2006-11-30
I agree with turbojugend_gr, don't worry about the firewall and antivirus.  As an ex MS person, it is hard to believe that your protected without the other software, but you are.  It feels unusual, but your ok.

FEEL SAFE

---

### Post by TheRingmaster on 2006-11-30
> **Chamelion said:**
> turbojugend_
Just read your message. I had it installed already. If that is the case I might consider uninstalling. I do not send many messages on and am very careful with what I open.
It just would be good to know how these things work in Linux.
That just would leve the firewall and maybe a few tips on installing in general. 
I might also go and read the tut's on the Linux site.
get rid of that firewall that you have sitting there and install firestarter. Firestarter is all you really need in the case of firewalls. you can install it via add/remove packages. The first time you open it, it will give you a friendly start-up wizard. Just set it and forget it.

---

### Post by CaveRat on 2006-11-30
Here is a very helpful guide site for you to settle back and study up on the how to do things. If you want to use a firewall, definitely check out the Firestarter how to. [http://forums.scotsnewsletter.com/index.php?showtopic=17087](http://forums.scotsnewsletter.com/index.php?showtopic=17087)

---

### Post by turbojugend_gr on 2006-12-01
Hello, Chamelion.

Yup it is true, Linux in general and especially ubuntu are perfectly safe (PER-FEC-TLY !) out of the box, it's they way things are built. Linux is (generally) open source so if a security issue is discovered then we donm't have tocreate a program to cover it/guard it. We just change the code to eliminate that. So simple. Hail to Open Source Software.

Though it is not needed to guard your system, an antivirus might be helpfull if you wish to open ports and stuff (as I said earlier), again if you are to use the firewall for such use, then read on . If you are trying to protect your system, you a re just insulting it. It is there to pretect your data, as every OS should be supposed to do, not you trying to protect the OS.

Anyway in general, for whatever reason you would like to install a firewall, make sure it is open source (apart from the previous reasons, the ability to see the source ,is critical when it comes to  security applications), so go for Firestarter. To install it just open synaptic, search for Firestarter, check for installation and apply this. You should find Firestarter under Applicartions>>Internet.

Best Regards, TJ.

---

### Post by Chamelion on 2006-12-02
I have installed Firestarter now. I was not aware of the different setup for applications and the package manager. There is a lot I don't know I found out. Linux is a bit humbling when you arrive from Windows. I can consider myself an absolute beginner again. LOL.
I am amazed at the speed of my system though. It is going so much faster then with windows. Also the availability of applications and the feel is that much different.
I have installed chkrootkit from packages. No insult to the system here I am just playing around in a way to find out how things work. (And I was told that there is a vulnerability in Linux)
I previously noticed that sometimes after installing things they just do not show up anywhere. No Icons for access. Where are they:confused:

---

### Post by turbojugend_gr on 2006-12-02
Here m8, since you called yourself a linux beginner, here are some great guides to get you started, don't have to read 'em all, just the parts you care about learning.

1. Official [Ubuntu Desktop Guide]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html").
2. [Ubuntuguide.org's guide]("http://www.ubuntuguide.org")
3. [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")
4. Some great how-to's/guides from asyiu, on [psychocats]("http://www.psychocats.net/ubuntu/index.php")

I hope you 'll find them helpful, they are to be read on teh order I gave you, if you don't find sth in these guides, you can always ask here. (For a start read installing from the first guide, since you are still confused on this).

Now as for where the apps are, you are right you should been told that after installing a package. Usually, an appropriate menu entry will be created, aat the appropriate submenu. If the package you installed doesn't have a GUI (graphical interface) you 'll need to guess the command to start 'em, a good way would be trying for sth like the package name (for example you can start firestart, from the menu, and also by issuing "firestarter" in a terminal (note linux is case sensitive, A is not a, and R is different from r).

If you have more questions, keep 'em coming, this community will be sure to hit back. Welcome to Ubuntu (again).

P.S: Who ever told you "Linux is vulnerable", is true, but it would be like me saying "man has gone to the Moon". Both sentences can be considered correct, but it's not like they decribe the situations at the best possible way. That would be for the first sentence "It is possible to break into a Linux system, but it is like 10.000 tougher to do than if it was windows, so why bother anyway". While the second could be better like: "There are about 20 men that have gone to the moon, out of the 50 billion that have lived in earth". Of course both nubers are just ugly assuptions of mine, but I hope the example has some strength. If I may try again: if I say that Earth is not a sphere, you couldn't judge me wrong cause Earth is very close to that. That goes for Linux too, in such a manner Linux is invunerable (yet if you are sticking to accuracy that is not correct). I hope I am not boring you... :).

---

### Post by Chamelion on 2006-12-02
Ok I found the files for ex. chkrootkit. (Looked in file system.) How do I open it and run it though? I clicked on all the files. There is a lot of for me in the moment confusing  stuff about configuring etc.
I have had that with a few things now. It is probably right in front of my eyes somewhere. I just do not know where to look.
No you are not boring me and do make sense. Philosophy was born somewhere in your neck of the woods (at least officially) and I can appreciate it that it is used to explain something like Ubuntu.:-D

---

### Post by turbojugend_gr on 2006-12-03
Well try "chrootkit", in a terminal. The terminal is where you can put commands instead of using the guis. In gnome the terminal is under Applications>>Accessories>>Terminal. You just type this and hit enter. Of course I don't know if that's the command, just a guess.

If you wish to find it (or any command that calls a package you just installed), you can do the following trick: take a look to where it installed it's files, you can do that if you right click the package in Synaptic, and then go for properties/installed files. If there's anything installed in /usr/bin (the common location where ubuntu keeps it's app-start commands etc), then go in usr/bin using nautilus (ubuntu for explorer, the app that navigates you through your filesystem, just click on computer to open it...). In that catalogue, sort files by mod date, the last/first one named similar to your just installed app, should do it, remember it's name, and type that in a terminal.

Let me know how it did.

---

### Post by Chinkostu on 2006-12-03
> **turbojugend_gr said:**
>  IMHO what you need to avoid this, is limited curiosity/energy to mess up with stuff, and learn by breaking your system, ;).


haha, exactly. i'm sat here at 5am messing with a fresh install of ubuntu after breaking the last!

linux causes insomnia ;)

---

### Post by Chamelion on 2006-12-08
Sorry for this late reply. I have got smoke coming out of my ears for all this trying.
Turbojugend, yes I managed chkrootkit to work through the way you advised.
I have also installed Debian to make things a bit easier. Now the hassle really started. I cannot get it to show up under Applications. 
I went to System, Preferences, Menu Layout and tries to click on the box next to it. Couldn't tick it. Same with Accessibility, Education, Other, Programming and System tools.](*,) 
It is installed. I found the files. There is a lot of stuff that just refuses to work. 
I also found that I can only boot into XP on my other drive through Ubuntu. I am not able to set the other drive as first boot device anymore.
Doesn't matter that much, because I am not giving up on Linux, but it still annoys the *^#@ out of me. I probably learn heaps in the moment, but I think I have used Microsoft to long. That stuff breeds ignorance.
Hope you do not loose patience with me.
Firewall works brilliantly. There was not a single event. In or Out. I am amazed. There would be countless with Windows.
Cheers

---

### Post by Chamelion on 2006-12-08
Sorry I meant I installed "Gdebi package installer" to make it easier, please disregard the last post. I spend 2 full nights to find out things that where right in my face. I was looking in all the wrong places and frankly speaking I don't know whether I should be embarrassed or pissed of.LOL
I can install programs now and even manage to find them afterwards.:-D 
Thanx again for your patience and help

---

### Post by randytuggle on 2006-12-08
I am a convert myself. I have found that after a few days of making some adjustments to the Ubuntu install, I would never go back to MS Windows OR Mac OS X. Some things that I ran into after my initial install are below:

Sound problems with distortion? Just turn down the PCM volume by right-clicking on the volume icon in the upper right - select properties, then turn down PCM a little bit.

Video on games kinda slow and choppy? Make sure you have the correct video driver installed. If you have a slow/choppy video problem, come back to the forum and search for some help.

Want tons of free software? Check the ADD/REMOVE or Synaptic Package Manager (system>administration menu). Most things you'll want to tweak and upgrade your install are right in Synaptic!

Firefox can be a little buggy from my experience. Try Epiphany for your web browsing. I like it alot.

Missing windows a bit for a few applications? Look into VMWare Server if you want your windows OS back. DON'T LEAVE UBUNTU!!!! You won't have to! You can run any operating system WITHIN Ubuntu Linux! Mine works great when I need to go on Windows.

Any questions...come on back to the forum. Welcome!

---

