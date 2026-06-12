---
title: "Office spying :)"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by 1oki on 2007-06-28
Ok so I am the main IT guy for my offices. I was wondering if there is a nix or win app out there that will allow me to monitor multiple desktops at the same time. Not necessarily interact with them, but just watch what they are doing. I know there are some ethical issues with this, but we have our reasons to try this. Users are going to unapproved websites, and other things that are causing damage to our practice and network. 


So any clue?

---

### Post by aeiah on 2007-06-28
cant you just look at your router logs?

---

### Post by Cypher on 2007-06-28
You don't want to monitor desktops (I'm sure there are SOME privacy rules that would be violated by this), what you want to do is just block the websites outright. If you don't employ a proper firewall to do this, you can implement a proxy server that can easily allow you to filter any website you don't want people visiting.

---

### Post by cogadh on 2007-06-28
Not to mention a proxy-based firewall will tell you exactly what sites your users are going to and when.

---

### Post by 1oki on 2007-06-28
> **Cypher said:**
> You don't want to monitor desktops (I'm sure there are SOME privacy rules that would be violated by this), what you want to do is just block the websites outright. If you don't employ a proper firewall to do this, you can implement a proxy server that can easily allow you to filter any website you don't want people visiting.

hmm not really, they all signed an agreement stating that they accept the fact that they can be monitored, and have their company emails read/scanned for inappropriate material. Basically, you are on company time and on a company machine... so you are subject to scrutiny. I know, because i wrote the waver.

---

### Post by Inxsible on 2007-06-28
I agree. If its only a bunch of websites you want to block, that can be easily done thru the firewall and/or router.
 
Why go thru the hassle of monitoring each machine? Not to mention the hit, the entire network will take due to increase in traffic to the machine you are monitoring from.

---

### Post by 1oki on 2007-06-28
> **cogadh said:**
> Not to mention a proxy-based firewall will tell you exactly what sites your users are going to and when.

good idea... still no clue as to how to do that though. Still a rather n00b when it comes to linux. Can you point me in the right direction?

---

### Post by cogadh on 2007-06-28
[http://www.grennan.com/Firewall-HOWTO.html](http://www.grennan.com/Firewall-HOWTO.html)

---

### Post by 1oki on 2007-06-28
> **Inxsible said:**
> I agree. If its only a bunch of websites you want to block, that can be easily done thru the firewall and or router.
 
Why go thru the hassle of monitoring each machine? Not to mention the hit, the entire network will take due to increase in traffic to the machine you are monitoring from.

Well, we don't have a real expensive router.. Only a little linksys. The sit blocking seems to not work completely... only the first page of the blocking works... (out of what 10?). So my office manager wanted to have videoed proof of them doing it... evidently logs could be tampered with.

---

### Post by 1oki on 2007-06-28
> **cogadh said:**
> [http://www.grennan.com/Firewall-HOWTO.html](http://www.grennan.com/Firewall-HOWTO.html)

Thanks... I will give it a go! we will be moving in a few months so I can really put it to use when we move to the new office.

---

### Post by Inxsible on 2007-06-28
[SIZE=2]Most workplaces will and should block all unappropriate websites. Most, if not all, also block the ports for the well known IM clients like yahoo, msn and gtalk. [/SIZE]
 
[SIZE=2]I have also worked in places, where all email providers like yahoo and msn were blocked too. you could still access the yahoo search engine, but not the email, movies sections of the yahoo portal.[/SIZE]
 
[SIZE=2]Depends on how strict you want to get.[/SIZE]

---

### Post by cogadh on 2007-06-28
> **1oki said:**
> Thanks... I will give it a go! we will be moving in a few months so I can really put it to use when we move to the new office.
That How-to is a little old, but all of the principle still apply. If you Google around a little, you may find something a little more modern.

---

### Post by 1oki on 2007-06-28
> **Inxsible said:**
> [SIZE=2]Most workplaces will and should block all unappropriate websites. Most, if not all, also block the ports for the well known IM clients like yahoo, msn and gtalk. [/SIZE]
 
[SIZE=2]I have also worked in places, where all email providers like yahoo and msn were blocked too. you could still access the yahoo search engine, but not the email, movies sections of the yahoo portal.[/SIZE]
 
[SIZE=2]Depends on how strict you want to get.[/SIZE]

yeah, I did have all those blocked. But was told to unblock the email for some reason. We also use msn for inter-office communications. 5 offices through out the county. easier than calling.

---

### Post by Seisen on 2007-06-28
You could also try Dansguardian w/Smoothwall.

[http://dansguardian.org/]("http://dansguardian.org/")
[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by hyper_ch on 2007-06-28
I dunno how it is handled in the US but here in Switzerland, even if your employees did sign such a contract, it has no meaning as those are terms violating law here...
Before really going to monitor their screens, be sure that what you do is legally ok.

---

### Post by cogadh on 2007-06-28
In the US, the computers and the connection they use at work are the property of the company you work for and can therefore be restricted or monitored in any way the company deems appropriate, provided that restriction or monitoring does not violate any other laws. It is common practice to monitor internet usage and restrict that usage to business-specific sites. 

For example, the company I used to work for only gave internet access to specific employees and in many cases that access was restricted to one particular site they need for some aspect of their job. All internet activity, including those who had open access, was monitored and anyone caught going to inappropriate sites had their access either removed completely or severely restricted. Oh, the stories I could tell of the things people will do on a work computer...

---

### Post by 1oki on 2007-06-28
^^ Exactly what we are trying to put a squash on! :) not my choice... I could care less. But the higher ups have spoken and I need to do something about it

---

### Post by Seisen on 2007-06-28
You don't go to work to goof off, you go to work to work.

---

### Post by hyper_ch on 2007-06-28
well, here you have granted rights - most notably the dignity and this one will be jeopardized by such monitoring

---

### Post by RanulfWolfSage on 2007-06-28
Oh, you mean I should be working?  hehe Technically though, I've been tasked with learning and becoming more knowledgeable with Linux, so this could be construed as fulfilling that task!

---

### Post by az on 2007-06-28
> **1oki said:**
> Ok so I am the main IT guy for my offices. I was wondering if there is a nix or win app out there that will allow me to monitor multiple desktops at the same time. Not necessarily interact with them, but just watch what they are doing. I know there are some ethical issues with this, but we have our reasons to try this. Users are going to unapproved websites, and other things that are causing damage to our practice and network. 


So any clue?

Ubuntu includes a VNC server.  You can configure it so that you can VNC into any machine at any time.  I am not sure how to go about getting rid of the notification dialogues, though.  There must be a way.

---

### Post by Inxsible on 2007-06-28
> **az said:**
> Ubuntu includes a VNC server. You can configure it so that you can VNC into any machine at any time. I am not sure how to go about getting rid of the notification dialogues, though. There must be a way.
You mean a VNC server is installed by default  in Ubuntu ?
 
How would I access it, do I need to install any app ?

---

### Post by cogadh on 2007-06-28
> **hyper_ch said:**
> well, here you have granted rights - most notably the dignity and this one will be jeopardized by such monitoring
You have the right to dignity at work here to. But what is dignified about using your work PC to access porn or for illegal file sharing? Just save that stuff for your home PC and do your job.

Plus, whatever you do with your work PC makes the company you work for liable for your actions. So, for example, if an employee illegally downloads software, the company is liable for any fines if the software is caught by an audit.

---

### Post by Inxsible on 2007-06-28
> **cogadh said:**
> You have the right to dignity at work here to. But what is dignified about using your work PC to access porn or for illegal file sharing? Just save that stuff for your home PC and do your job.
 
Plus, whatever you do with your work PC makes the company you work for liable for your actions. So, for example, if an employee illegally downloads software, the company is liable for any fines if the software is caught by an audit.
 
My company has a policy that they own the computers and all proprietary software installed on the system. So if I install a legally purchased software, its theirs. But if I install something illegally, then only I am held responsible !!
 
So they have the best of both. But then again, I have 5 machines at home...so I dont need to do anything on my work laptop except work anyway ;)

---

### Post by digitalbenji on 2007-06-28
For windows there is a free program call gencontrol.  It allows you to connect to any PC at any time assuming you have the appropriate credentials.  We use it quite a bit for remote desktops when our enterprise software fails.  It does not notify the user  you have connected, and I would imagine that it could be configured so you would not have control, though I've never tried, since that is both unethical and against our company policy.  I think you will find that spying reduces peoples job satisfaction, and overall performance.  Not to mention that will all think of you as a creep.

---

### Post by cogadh on 2007-06-28
> **Inxsible said:**
> My company has a policy that they own the computers and all proprietary software installed on the system. So if I install a legally purchased software, its theirs. But if I install something illegally, then only I am held responsible !!
Your company may hold you responsible, but the BSA holds the company responsible for the actions of its employees. If you install something illegally, you would probably get fired, but the company could still get sued.
 > Many businesses, both large and small, face serious legal risks because of software piracy. Under the law, a company can be held liable for its employees&#8217; actions. If an employee is installing unauthorized software copies on company computers or acquiring illegal software through the Internet, the company can be sued for copyright infringement. This is true even if the company&#8217;s management was unaware of the employee&#8217;s actions.
[http://www.bsa.org/usa/antipiracy/Piracy-and-the-Law.cfm](http://www.bsa.org/usa/antipiracy/Piracy-and-the-Law.cfm)

---

### Post by escalated on 2007-06-28
A bit ago I was reading about a program called driftnet(i think!) - it just sniffs the lan for any jpeg images and can display them on your computer etc..seems like this would be close to what you want to do - and also keep traffic low.

Only problem is I dont remember if it had ip logging, or if the thread I was reading was just talking about implementing it.

The program seems to be rather old also, you'd most likely have to compile it etc -- but that's not too hard.

---

### Post by Motoxrdude on 2007-06-28
Somethings not right here. Why would an 'IT' need help with something like this? Surely an 'IT' would be able to figure it out on his own. That and the thread starter doesn't seem like he wants to block anything, just monitor desktops. I don't know about you but something just isn't right here.

---

### Post by tribaal on 2007-06-28
Did you start by sending an email to all staff (including a non-hidden copy to the boss)? That's probably the first thing to do.

I don't want to start a flamewar, but this is pretty borderline from a moral point of view.
You're supposed to trust your employees, for a start. If one doesn't deserve your trust (like this seems to be the case), install a firewall/proxy, log his IP address, and go talk to him/her. If he/she persists, fire him/her.
One single misbehaving employee is not an excuse to spy on all employees...

That's the right way to react, in my humble opinion.

Setting up a recording of the user's desktop in a permanent way is illegal here, as it should in a democracy.

- trib'

---

### Post by cogadh on 2007-06-28
> **Motoxrdude said:**
> Somethings not right here. Why would an 'IT' need help with something like this? Surely an 'IT' would be able to figure it out on his own. That and the thread starter doesn't seem like he wants to block anything, just monitor desktops. I don't know about you but something just isn't right here.

If he's taking advice on setting up firewalls, proxy servers and application that require network administrator access, I don't see how there could be anything funny going on here. If his requests are not legitimate, there's nothing he could do with the suggestions we are giving him if he isn't an IT guy or Net Admin on his network.

---

### Post by dpar on 2007-06-28
I was thinking the same thing, Motoxrdude, while I was reading through this. Of course, most "IT" people that I have seen don't know any more about computers than a 3 yr old anyway.:biggrin:

---

### Post by cogadh on 2007-06-28
> **dpar said:**
> I was thinking the same thing, Motoxrdude, while I was reading through this. Of course, most "IT" people that I have seen don't know any more about computers than a 3 yr old anyway.:biggrin:
As an IT guy, I take some offense to that, but I know what you mean. There are way to many supposedly qualified IT people who's only real qualification is owning a copy of "Networking For Dummies". :)

However, this guy already said he was new to Linux and needed help with using Linux to monitor his network. This is the beginners forum, after all.

---

### Post by 1oki on 2007-06-28
> **az said:**
> Ubuntu includes a VNC server.  You can configure it so that you can VNC into any machine at any time.  I am not sure how to go about getting rid of the notification dialogues, though.  There must be a way.

Yeah there is a registry hack... I have done that before. But was hoping if there were something like a security camera... always displaying the desktop in a small window where even when i mouse over it it wont move their mouse...  But I will just try smoothwall... Again.

---

### Post by 1oki on 2007-06-28
> **dpar said:**
> I was thinking the same thing, Motoxrdude, while I was reading through this. Of course, most "IT" people that I have seen don't know any more about computers than a 3 yr old anyway.:biggrin:

Well I am the netadmin of the doctors office. They call me the IT guy...( no respect). I just started using linux about a year ago. That is when i picked it up for the first time. If you must know, we have had problems of people using myspace, file sharing, going to stock websites, and even porn sites. Like I said, we are not all that equipped for monitoring, and was thinking of an easy way to do it. 

As for not knowing anything about computers, uh huh... Just a n00b in linux with moderate knowledge. School only focused on win networking... I had to venture on my own into linux. the first thing i did in ubuntu was to create a PDC for our network. I was rather impressed how I was able to handle myself.  As for blocking services and sites, I have, and I continue to. But the users are those sudo techno know it all's and find ways around them. I would like to be able to have an active monitoring. Something like ntop (which i use but without netflow so its pointless). If there were something strange going on than why would i consider just using smoothwall and proxying the traffic? besides, I wouldnt be able to monitor desktops without the appropriate credentials... Which I have because I am the net admin! Seriously people, don't be paranoid! just looking for suggestions on monitoring. Anyways, I have used smoothwall before personally, along with proxies... But to set them up for my office... I would be lost. So any info on that would be great!

---

### Post by xpod on 2007-06-28
Etherape & wireshark are a couple of good network monitors.... if you can decipher the information your getting of course:DEtherape actually displays the network traffic graphically.

Loads of other network monitor tools on here too
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by 1oki on 2007-06-28
> **xpod said:**
> Etherape & wireshark are a couple of good network monitors.... if you can decipher the information your getting of course:DEtherape actually displays the network traffic graphically.

Loads of other network monitor tools on here too
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

cool, I am installing it now! thanks! Etherape that is!

---

### Post by pancakelizard on 2007-06-28
websense
isa firewall

real vnc for monitoring - you can configure it so they dont know you are watching them

---

### Post by 1oki on 2007-06-28
> **pancakelizard said:**
> websense
isa firewall

real vnc for monitoring - you can configure it so they dont know you are watching them

yeah i know... and isn't websense a paid for product... Maybe I will suggest it.

---

### Post by Sunforge on 2007-06-28
Loki,

It may be worth considering some other things:

Before you start, it's worth checking the basics: 
What privileges does each user have on their PC and what could be done to reasonably manage and restrict them without stopping them from getting their job done and without putting monitoring in place?
Have you got appropriate virus and spyware scanning in place? This is critical with Microsoft.
Have you employees been educated about the software they use and why it's important for them to exercise their common sense when using the web?

Work with the management to establish a clear goal. Is it to catch a single individual in the office who is setting a bad example? Is it to stop general abuse? Is it to send out a signal that nothing is for free? Each has a different solution.

You can then work out what it would take to establish a regime that delivers the above. You've got lots of advice from the forum about potential solutions.

Discuss your solution with management and if costs aren't acceptable (say you want a new router etc) then modify requirements with their agreement until you reach an acceptable standard of cost/monitoring and more critically the cost of your time. Make sure that you manage your manager: he or she has to have their expectations set quite clearly by you. 

The above sounds like a lot of work but in a small network you could dispose of all of the above in a few hours.

If you've got this far - all well and good. I'd suggest running your monitoring solution past a lawyer to ensure that you are 100% above board. The objective of this part is to protect yourself from your own assumptions about what is and what isn't legal.

It's essential that the general manager, managing partner etc puts out a company wide mail, memo or stone tablet plus burning bush that re-states the contract and tells people what will be monitored and what the consequences of breaking the rules are. If you have a particularly problematic employee read this out to the person in question with a witness present and get them to sign the statement that was read out.

Put your monitoring in place (whatever level has been decided on) and let time pass, then review what's happened with management. Sometimes you get results you don't expect. I won't give you concrete examples but trust me - you'll learn more than you want to know if you start looking for it. 

I would recommend persevering with Smoothwall though as it's a good firewall and has some very good features. Logging is solid and if you're on a small network it should work just fine. If on the other hand you have more freedom with cash there are other proprietary solutions that are rock solid and perform very well.

Oh and one more thing: when you get sick of maintaining the firewall, trawling log files, locking people down, dealing with the management and being asked for the umpteenth time why person x can't browse site y feel free to step outside and take a deep breath before saying something that you might later regret. It's just a job and it's not worth getting too worked up about.

Oh and one more thing, have you seen this:

[http://www.untangle.com/](http://www.untangle.com/)

---

### Post by az on 2007-06-28
> **Inxsible said:**
> You mean a VNC server is installed by default  in Ubuntu ?
 
How would I access it, do I need to install any app ?

System - Preferences - Remote Desktop


> **1oki said:**
> Yeah there is a registry hack... I have done that before. But was hoping if there were something like a security camera... always displaying the desktop in a small window where even when i mouse over it it wont move their mouse...  But I will just try smoothwall... Again.

What are you talking about?  The Registry is a windows thing.  There is no registry in Ubuntu.

---

### Post by silverglade00 on 2007-06-28
You might want to check with a lawyer on the monitoring and your waiver. You work in a doctor's office and want to see what's on people's desktops? If you load up someone's desktop and they are looking at someone's medical records, haven't you committed a breach of confidentiality? Even if you have clearance to view confidential materials, someone looking over your shoulder might not. Just something to think about.

---

### Post by randomjohn on 2007-06-28
Depending on the version of your linksys router, you might look into changing the firmware to something like dd-wrt

Also, if you're planning to take employment action based on the websites someone is visiting, "the IT guy was monitoring remotely and he saw it" isn't nearly as good evidence as "here's our proxy server log with the exact urls, times, http requests, etc."

The only thing monitoring the desktops would be better for is allowing you to look at the unauthorized websites on someone else's machine ;)


Disclaimer- I'm a lawyer, but I'm not your lawyer.  Get one and ask him for legal advice.

---

### Post by HermanAB on 2007-06-28
Two words:
squid-proxy and tcpdump

---

### Post by Keen101 on 2007-06-28
This probably won't be helpful at all, but thought it should be mentioned.

can't mention anything for monitoring, but for blocking.


If the default browser is Firefox, then you could install WOT and Foxfilter on each machine. I know it's a little tedious, but they both offer some good blocking services. You can set WOT to actually block bad websites that have bad reputations, and for foxfilter, you can add special key words, like "images.google", so that all forms of google images can be blocked whether it is in english or in russian. 


you would just then need to set Internet explorer to block EVERYTHING, which should be easy with "contet advisor" built into ie.

p.s. hope you get a better job with better respect.

-keen101

---

### Post by Keen101 on 2007-06-28
p.s.: forgot to mention that foxfilter has the option to block access to the add-ons "link" for firefox, s o your employees cannot remove foxfilter or WOT without your password.


-keen101

---

### Post by 1oki on 2007-06-29
> **az said:**
> SWhat are you talking about?  The Registry is a windows thing.  There is no registry in Ubuntu.

On the desktop side (windows) there is a registry hack that will allow VNC to be in use without the user being aware. The vnc viewer icon (whichever one you use, realvnc, tightvnc. etc.) you can hack it in the registry to not display the connection status.

---

### Post by 1oki on 2007-06-29
> **Keen101 said:**
> This probably won't be helpful at all, but thought it should be mentioned.

can't mention anything for monitoring, but for blocking.


If the default browser is Firefox, then you could install WOT and Foxfilter on each machine. I know it's a little tedious, but they both offer some good blocking services. You can set WOT to actually block bad websites that have bad reputations, and for foxfilter, you can add special key words, like "images.google", so that all forms of google images can be blocked whether it is in english or in russian. 


you would just then need to set Internet explorer to block EVERYTHING, which should be easy with "contet advisor" built into ie.

p.s. hope you get a better job with better respect.

-keen101
Thanks for the advice... but unfortunately the default browser is IE... we use an EMR and the requirements for that emr is IE... I can always use the access restrictions through the site privacy... but thats a pain in the butt when you have 50-100 computers throughout the country. 

> silverglade00  	You might want to check with a lawyer on the monitoring and your waiver. You work in a doctor's office and want to see what's on people's desktops? If you load up someone's desktop and they are looking at someone's medical records, haven't you committed a breach of confidentiality? Even if you have clearance to view confidential materials, someone looking over your shoulder might not. Just something to think about.

I am fully aware of the legalities behind the medical records issue. I am the offices "Chief Security Officer" (whatever that means). But I took plenty of courses in HIPAA to know what I can and cant do. Thanks though :)


Ok people, I have lots of input! Thanks to all that have given me some things to look into! I will check out smoothwall and not get frustrated when people complain about the site blocking! I will just tell them that it keeps them out of trouble! Thanks again!

---

### Post by dptxp on 2007-06-29
I can only see that none of our private information with anyone is private any more. We do not know who can access what and do what with it. It is not just Big Brother, it can be the guy on the street who knows that you sat on a burning cigarette 6 month and 4 days back. Actually he may know much more.

---

### Post by phr0ze on 2007-06-29
I used to use a standard command to tell X to grab a shot of screen 0:0 or something like that. This was on every system by default and I had a lot of fun with it. However this was so many years ago I can't remember what I used.

type man xwd in terminal to see if you can get that working, or install xgrab on machines.

---

### Post by 1oki on 2007-06-29
> **dptxp said:**
> I can only see that none of our private information with anyone is private any more. We do not know who can access what and do what with it. It is not just Big Brother, it can be the guy on the street who knows that you sat on a burning cigarette 6 month and 4 days back. Actually he may know much more.

very true... It is scary how much information is out there floating around. It is equally scary how much information gets exchanged from person to person legally. And people think I am paranoid for trying to stay anonymous as much as I can...

---

