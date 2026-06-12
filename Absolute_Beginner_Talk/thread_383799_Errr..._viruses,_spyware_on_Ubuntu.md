---
title: "Errr... viruses, spyware on Ubuntu??"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-13
Hi

This may be my dumbest question yet but what do you do to protect yourself against the nasties? Do you get much in the way of viruses etc in Linux?

Kind Regards
Bob

---

### Post by noob_saioke45601 on 2007-03-13
thats what the automatic updates are for but there security updates. linux isnt vulnerable to viruses and spyware. in other words linux cant get infected.

---

### Post by Kobalt on 2007-03-13
I have never ever heard of any spyware or 'natsy' in Linux... And virsues, well, so far there aren't any threats to Linux.
By default, Ubuntu has no open ports at all and a very very powerful Firewall (iptables). With the security of installing software only from Ubuntu repos, you end up with one of the most secure desktop of the moment...

---

### Post by bwallum on 2007-03-13
It just gets better here! 

Thanks for your quick response.
Bob

---

### Post by jem7v on 2007-03-13
Technically, a Linux system Could get infected with a Linux-specific virus, but because of the way it has to happen the chances of it are very very low... i.e., unless the virus is already packaged for your specific distribution of Linux (which would still require you to give it administrative priviledges and run it anyway), it would have to be the source code for the virus, thus meaning that in Most cases you would actually have to knowingly configure, compile, install, and run the virus with administrative priviledges if you wanted it to do anything to your system.  That's why Ubuntu doesn't auto-run attachments in emails and the likes.

I'm sure that eventually somebody will just do something nasty like release a virus-laden .deb and hope people don't notice, but that won't be an issue if you stick to installing programs from trusted sources (such as the official repositories instead of downloading .debs off of random peoples' websites).

In short, some viruses do Exist, but they don't really Work.

---

### Post by 23meg on 2007-03-13
[QUOTE=bwallum]Hi

This may be my dumbest question yet but what do you do to protect yourself against the nasties? Do you get much in the way of viruses etc in Linux?
[/QUOTE]

This should answer all your questions:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[QUOTE=noob_saioke45601]thats what the automatic updates are for but there security updates. linux isnt vulnerable to viruses and spyware. in other words linux cant get infected.[/QUOTE]

Wrong. There are just not many viruses and spyware, and Ubuntu's security model, as well as the generally encouraged usage practices that settle pretty well, means that they're not much of a worry. Theoretically, you can still get hurt by malware, and the most likely reason would be bad security practices.

[QUOTE=Kobalt]By default, Ubuntu has no open ports at all and a very very powerful Firewall.[/QUOTE]

There's no firewall by default.

---

### Post by penp on 2007-03-13
> **bwallum said:**
> Hi

This may be my dumbest question yet but what do you do to protect yourself against the nasties? Do you get much in the way of viruses etc in Linux?

Kind Regards
Bob

As other users have already indicated, it's not impossible, but pretty unlikely to get a virus or other such malware in any linux os (unless you have bad security practices). The main reason for this is that most spy/adware is written to infect windows systems, because it's the majority of what's out there. They want to affect the most computers possible, and if most of the computers that will be browsing their content will have windows installed, then they've achieved their desired effect. As such, most malware is written to affect windows pcs (more specifically, ones running internet explorer, I stopped having spy/adware problems altogether just by switching to firefox on my windows pc, and as long as you're careful about what files you run when you download them, you really don't have to worry about viruses that much, either)

still thinking about switching back to debian or ubuntu though :lolflag:

---

### Post by x1a4 on 2007-03-13
> **23meg said:**
> There's no firewall by default.

Really?? Have things changed in Feisty or something?  When I installed Edgy iptables was installed by default.

---

### Post by m1135 on 2007-03-13
this may also seem lik a stupid question, but...
i have a virus-ladden XP with ubuntu partition.
could viruses get from one to other THEORETICALLY?

---

### Post by Belyel on 2007-03-13
> **m1135 said:**
> this may also seem lik a stupid question, but...
i have a virus-ladden XP with ubuntu partition.
could viruses get from one to other THEORETICALLY?

Definitely not.  Windows and unix systems are organized (under the surface) completely differently.  The only possible way for a windows system and a linux system to have the same virus would be if you downloaded the same source code, compiled one verison in linux and one in windows, then installed it on each.  Nothing on your windows drive will transfer or execute by itself in linux.

---

### Post by 23meg on 2007-03-13
> **x1a4 said:**
> Really?? Have things changed in Feisty or something?  When I installed Edgy iptables was installed by default.

iptables isn't a firewall per se, though it can be used as one. Since there are no predefined rules in the default installation, there's no firewall in effect.

---

### Post by konungursvia on 2007-03-13
You can't catch windows viruses. However, if you're not experienced, or not confident, don't add too many outside repositories and download less secure stuff. Not that you'd likely get malware, but you will get some less stable stuff if you do that.

---

### Post by Guinness Bug on 2007-03-13
> **23meg said:**
> iptables isn't a firewall per se, though it can be used as one. Since there are no predefined rules in the default installation, there's no firewall in effect.

I'm glad I followed this thread. I have learned some things that I've had questions about regarding ubuntu security. One question remains with me, though. Is iptables something that I need to configure, or is it done automatically?

Danke

---

### Post by 23meg on 2007-03-13
> **Guinness Bug said:**
> I'm glad I followed this thread. I have learned some things that I've had questions about regarding ubuntu security. One question remains with me, though. Is iptables something that I need to configure, or is it done automatically?

Danke

You need to configure it. There are ready made firewall scripts that you can use, as well as frontends that make configuring easier, such as Firestarter.

---

### Post by Guinness Bug on 2007-03-13
> **23meg said:**
> You need to configure it. There are ready made firewall scripts that you can use, as well as frontends that make configuring easier, such as Firestarter.

Danke

---

### Post by mi_were on 2007-03-13
> **23meg said:**
> You need to configure it. There are ready made firewall scripts that you can use, as well as frontends that make configuring easier, such as Firestarter.

I have definitely found this thread really helpful. In fact it was better than... well not quite!

Really good stuff, I am configuring my firewall right now. Thanks everyone

---

### Post by bravemosquito on 2007-03-15
It's possible to create a .deb package which includes keylogger, written in bash or sh. When you install .deb package (usually as root on desktop system) there's a big chance that this keylogger is tuned to start as system service. Hidden as keyboard important process, and that's why you (or we) cannot sure is or not harmful proc, just there are no guarantees for that.

But when we talk about servers, used from specialist (administrator or whatever), the chance is and MUST be lower to get "infection" of this type. If the man with root privileges has lower knowledge than us then the server is like swiss cheese :mrgreen:

---

### Post by mahy on 2007-03-15
> **noob_saioke45601 said:**
> thats what the automatic updates are for but there security updates. linux isnt vulnerable to viruses and spyware. in other words linux cant get infected.

It'd be foolish to say that Linux and Unix can never ever get infected. Such statements have to be treated with caution. There are scores of security advantages over windows on one side of the equation, but hordes of hackers and criminals on the other. Mac OSX can get infected, why not Linux? Please don't take it as an insult. I'm a Linux fan, don't worry, but i'd love to be frank and honest about these things.

---

### Post by Zzl1xndd on 2007-03-15
> **mahy said:**
> It'd be foolish to say that Linux and Unix can never ever get infected. Such statements have to be treated with caution. There are scores of security advantages over windows on one side of the equation, but hordes of hackers and criminals on the other. Mac OSX can get infected, why not Linux? Please don't take it as an insult. I'm a Linux fan, don't worry, but i'd love to be frank and honest about these things.

Gotta agree here we can be infected but its not likely for a number of reasons. all *nix's are better at dealing with issues then Windows. Unix, Linux, BSD, OSX are all strong on this front.

---

### Post by herbster on 2007-03-15
This is a really good thread, and thanks for that link to the psychocats website. I knew I loved Ubuntu  for all the other stuff I have learned and been able to do in here, but I forgot about the added security which is really great :)

---

### Post by 23meg on 2007-03-16
> **bravemosquito said:**
> It's possible to create a .deb package which includes keylogger, written in bash or sh. When you install .deb package (usually as root on desktop system) there's a big chance that this keylogger is tuned to start as system service. Hidden as keyboard important process, and that's why you (or we) cannot sure is or not harmful proc, just there are no guarantees for that.

There's no difference between double clicking a Setup.exe whose origin you don't trust, and a cool_application.deb whose origin you don't trust, assuming you don't study the source code. You give them both equal access on your system; in Windows you're most likely running as the default user who's an administrator, and on Ubuntu you're most likely using the account you created during installation, who is a sudoer, which means it can use sudo to give system-wide access to administrative apps.

If you don't have the technical means to be sure something isn't going to do harm, the factor that comes into play is trust. The centralized repository model has the advantage that it provides pretty much everything the non-technical user will need, and is trustworthy. The "use Google to find third party proprietary app, download and double click" model is in theory more prone to abuse, since the source of the software can't be authenticated, there's no way of checking the source code, and no well intentioned community to place trust in.

In the end, the weakest link in the chain is almost certainly the user. Misuse can ruin the best security model, and good practices can let you survive with the worst.

> **bravemosquito said:**
> But when we talk about servers, used from specialist (administrator or whatever), the chance is and MUST be lower to get "infection" of this type. If the man with root privileges has lower knowledge than us then the server is like swiss cheese :mrgreen:

As the single user of a typical Ubuntu desktop installation, you don't have any less control, and thus any less responsibility, over your system. You're a sudoer, which means you can become root at will.

---

### Post by matchstich on 2007-03-18
i just reinstalled my os due to trojan 55808.A
don't have any idea how i got infected.
but i will keep a closer watch on my system from here on out.

---

### Post by bwallum on 2007-03-21
Hi Matchstick

Have you come across any anti virus software, or even anti spyware? I used to run Spybot on my Windows pc and I am looking for something similar to use in Ubuntu. I am sitting here with an open door at the moment and it is feeling uncomfortable.

Regards
Bob

---

### Post by AlanD on 2007-03-21
A question on Linux firewalls:
Coming from Windows XP and ZoneAlarm (which blocked all traffic until allowed, however it did it by program, not by IP) I am finding managing a Linux firewall slightly daunting. I installed Firestarter, which seems to have a "allow everything until blocked" policy. Is Firestarter actually a secure solution? Is there a firewall available that manages traffic by program, akin to ZoneAlarm? Any help on this topic would be much appreciated.

---

### Post by matchstich on 2007-03-23
> **bwallum said:**
> Hi Matchstick

Have you come across any anti virus software, or even anti spyware? I used to run Spybot on my Windows pc and I am looking for something similar to use in Ubuntu. I am sitting here with an open door at the moment and it is feeling uncomfortable.

Regards
Bob

search the forums for f-prot and avast, avg, and go to package manager and get rkhunter and chkrootkit.

also, search security, there are a few threads on the many different programs available. i have a few  others that i am still learning how to use.

being an old windows user, i got most of them and run them regularly.
and i don't do porn, music or open attachments.

ubuntu is tight, but, nothing is bullet proof.

 one thread on here was on a guy who had his bios wiped by an infection.

---

