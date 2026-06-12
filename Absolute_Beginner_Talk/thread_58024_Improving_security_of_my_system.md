---
title: "Improving security of my system?"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by Solomon on 2005-08-18
Alright, I am corrupted by the Windows OS because I am so used to having to install virus scanners, adware removal tools, firewalls... What do I need for this OS (Ubuntu)?

Do I need a virus scanner? If so, a good one you recommend is?
Do I need a firewall? If so, a good one you recommend is?
Do I need an adware/spyware removal tool? If so, what is a good one?

---

### Post by sunrex on 2005-08-18
you souldent need any of that with linux, becouse almost everything out there is only attacking windows. and a few more things like no one can really hack you unless they have ur root password...

however just to be safe, i would love to know were to get firewalls virus scanners and spyware destroyers....

remember, only to be safe.....and by safe i mean since in one week iv gotten 2750 attacks on windows...so my firewall tells me...and in about 5 months iv reinstalled it 150 times....

im duel booting, why duel boot for me? well i play a ton of games, and i got sound on winodws...

---

### Post by aysiu on 2005-08-18
A firewall's never a bad thing to have. Try Guarddog.

---

### Post by Brunellus on 2005-08-18
[QUOTE=Solomon]Alright, I am corrupted by the Windows OS because I am so used to having to install virus scanners, adware removal tools, firewalls... What do I need for this OS (Ubuntu)?

Do I need a virus scanner? If so, a good one you recommend is?
Do I need a firewall? If so, a good one you recommend is?
Do I need an adware/spyware removal tool? If so, what is a good one?[/QUOTE]
 you need...none of the above.

clamav is a well-regarded anti-virus application in Linux.  I've never run it though, and it's really intended for use on Linux boxes that serve files to Windows users.

Your firewall needs are taken care of by the iptables program;  there are graphical frontends to this, but I don't know what they're called.

I'm not aware of any known linux spyware.  

All of the above make administering a linux machine easy for me, so I can spend more time doing photos, or surfing the net, or generally messing about.

---

### Post by lothar_m on 2005-08-18
[QUOTE=Brunellus]

Your firewall needs are taken care of by the iptables program;  there are graphical frontends to this, but I don't know what they're called.[/QUOTE]


I believe you are refering to firestarter (available through apt of course).

---

### Post by joaoeb on 2005-08-18
A firewall is always a good idea, I recommend firestarter. You can install it via Synaptic or by going in a terminal and typing:

sudo apt-get install firestarter

And no, you will not need an antivirus and will not need a spyware remover. In truth I like to have fun visiting spyware infested sites and purposely opening mail with virus :D

---

### Post by sunrex on 2005-08-18
were do i configure firestarter, it says its installed, i dont see it at all

---

### Post by Brunellus on 2005-08-18
[QUOTE=sunrex]were do i configure firestarter, it says its installed, i dont see it at all[/QUOTE]
 open a terminal, and type 'firestarter' at the prompt, I think.  not sure if you need to execute $sudo firestarter

---

### Post by sunrex on 2005-08-18
thks that worked i used sudo firestarter

---

### Post by Kvark on 2005-08-18
As everyone else said, you don't need anti virus/spyware/adware stuff for linux. Except for maybe some adblocker extension for firefox if you are allergic to banner ads or clamav to scan files before you send them to windows users.

As for firewall... Try some port/firewall scans on online security tests without a firewall and you'll see that all ports are closed anyway. So a firewall to protect against threats from the outside is not needed.

But on the other hand, the network manager in hoary sucks, so you might want to use a firewall anyway to manage network access for your own programs.

---

### Post by weasel fierce on 2005-08-18
If you send and receive a lot of files, documents etc, you will want virus protection, to avoid spreading viruses to friends or coworkers, since a file could contain something unpleasant, even if it doesnt show on your system

---

### Post by xequence on 2005-08-18
Spyware and viruses are not problems at all on Linux =D

Though a firewall to stop hackers is always a good idea for servers, nomatter what OS.

---

### Post by sunrex on 2005-08-18
you know whats reallllyyyy funny

i got that firewall

and everytime i go on your site it says im being attacked and its serious...it was like 36 attacks...

---

### Post by GreyFox503 on 2005-08-18
[QUOTE=sunrex]were do i configure firestarter, it says its installed, i dont see it at all[/QUOTE]

When I installed Firestarter, it placed an icon in Applications > System Tools > Firestarter.

---

