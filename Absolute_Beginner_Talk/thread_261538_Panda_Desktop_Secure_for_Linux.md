---
title: "Panda Desktop Secure for Linux"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by EddieA on 2006-09-20
[http://www.pandasoftware.com/products/DesktopSecure_part.htm?sitepanda=particulares]("http://www.pandasoftware.com/products/DesktopSecure_part.htm?sitepanda=particulares")

Has anybody tried this, if so is it any good ?

Security is such a complicated issue I don't mind paying subs to keep linux secure while I learn how to use it.
Although many say Linux doesn't need it - I feel better with it. :) 
I specially need antivirus so I can safely trade emails with  Windows users and not send them their own viruses.

Any help appreciated.

---

### Post by Metacarpal on 2006-09-20
I've not tried this, but as it looks like a paid software (with free trial, but still), I think there are better ways to go.

For starters, just in the antivirus arena alone there are a number of good systems you can get for free.  ClamAV and Aegis, both available for free download through the Add/Remove in your Applications menu, are excellent antivirus programs that won't cost you anything at all.

Also, Ubuntu already has a firewall, which you can configure through various means (Firestarter - again, free - is often mentioned, though I've never bothered with configuring my firewall).

---

### Post by EddieA on 2006-09-20
Just found this:
> Ubuntu’s parent company, Canonical, has made Panda Desktop Secure available via its repositories.
Here:
[http://opensource.apress.com/article/93/ubuntu-news-round-up]("http://opensource.apress.com/article/93/ubuntu-news-round-up")

So I suppose I'd better try it ;) 

If anybody has any experience please share your views , would like to hear about it.

---

### Post by skymt on 2006-09-20
I'd say don't bother. Linux doesn't really need antivirus yet, and software firewalls are only worthwhile in specific cases. Most users are best off connecting behind a router, and letting that be the firewall.

---

### Post by Kilz on 2006-09-20
My experence is that anti virus programs in linux are a waste of time and money. There are few viruses to guard against. Those that exist are mostly "proof of concept" viruses that you have to do something stupid like run as root for them to infect you. If you just want to feel good , download a free scanner like the one from [avast]("http://www.avast.com/eng/download-avast-for-linux-edition.html"). Dont pay cash for it. I realise that you are comming over from Windows where its a nesssity to have one. But you will soon learn its a wast of time with Linux. Save your money.

---

### Post by EddieA on 2006-09-20
That was quick  :)  - my second post crossed over your reply

> **Metacarpal said:**
> I've not tried this, but as it looks like a paid software (with free trial, but still),.

Don't mind paying a small amount if it's simple to setup and use - it leaves me free to learn Ubuntu (I've only started learning)

> **Metacarpal said:**
> 
 ClamAV and Aegis, both available for free download 
.

Haven't tried Aegis will look into it 

I am concerned that Antivirus may not be kept fully up to date with OSS AV products  as I need to protect correspondence to Windows users.

---

### Post by Kilz on 2006-09-20
> **EddieA said:**
> That was quick  :)  - my second post crossed over your reply



Don't mind paying a small amount if it's simple to setup and use - it leaves me free to learn Ubuntu (I've only started learning)



Haven't tried Aegis will look into it 

I am concerned that Antivirus may not be kept fully up to date with OSS AV products  as I need to protect correspondence to Windows users.

Unless you forward unknown attachments there is no way to infect a windows person getting an email from you.

---

### Post by EddieA on 2006-09-20
> **skymt said:**
>  Most users are best off connecting behind a router, and letting that be the firewall.

Does this mean just set up a wireless connection or do you mean some other router?

---

### Post by EddieA on 2006-09-20
> **Kilz said:**
> Unless you forward unknown attachments there is no way to infect a windows person getting an email from you.

Is it 100% only attachments?

But wouldn't you have to be really scrupulous checking every email you replied to especially those with cc's. 
Not trying to be awkward just a paranoid windows user - or Win survivor. :)

---

### Post by gn2 on 2006-09-20
If it's anything like it's Windows version then Panda for Linux should be avoided like the plague...

AVG Free version has been keeping my Windows PC's clear of viruses for over three years now. They do a Linux version...

[http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free](http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free)

---

### Post by Metacarpal on 2006-09-20
> **gn2 said:**
> If it's anything like it's Windows version then Panda for Linux should be avoided like the plague...

AVG Free version has been keeping my Windows PC's clear of viruses for over three years now. They do a Linux version...

[http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free](http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free)

Good call.  AVG is what I put on my girlfriend's XP laptop (since she won't let me install Linux on it ;) )

---

### Post by skymt on 2006-09-20
> **EddieA said:**
> Does this mean just set up a wireless connection or do you mean some other router?

I mean any router that does NAT (network address translation), which includes wireless ones. NAT basically acts as a hardware firewall as a side-effect of the way it works.

Wireless routers obviously have an added attack vector (for attackers in range, anyway), but are pretty safe as long as you turn on WPA (*not* WEP, it's broken).

EDIT: By the way, I've switched to ClamWin for my Windows AV. It's open-source and works well.

---

### Post by EddieA on 2006-09-20
Thank you all for your replies - think I'll go with AVG pro tem until i'm really comfortable with Ubuntu then I'll try to undertstand what the security forum is all about - too techie for me so far :confused: 

When my sub on Norton for windows (NIS) runs out I'll put AVG on there too.
I know a lot of people who don't use AV on Windows but send me email so my email protection has always been important and my real worry is inadvertently passing on an infection from one of those to another of my acquaintances.

Thanks again

---

### Post by Metacarpal on 2006-09-20
> **EddieA said:**
> Thank you all for your replies - think I'll go with AVG pro tem until i'm really comfortable with Ubuntu then I'll try to undertstand what the security forum is all about - too techie for me so far :confused: 

When my sub on Norton for windows (NIS) runs out I'll put AVG on there too.
I know a lot of people who don't use AV on Windows but send me email so my email protection has always been important and my real worry is inadvertently passing on an infection from one of those to another of my acquaintances.

Thanks again

That's really considerate of you.  Better to take the time and look out for your more vulnerable fellows than to turn into a carrier monkey!

---

### Post by EddieA on 2006-09-21
> look out for your more vulnerable fellows than to turn into a carrier monkey!

Isn't this what we all have to do ?
If a friend/ family member /or a customer sends you an email (or anything else), one *may* try to educate them about viruses, one should certainly check them and fix anything you've been sent and make sure not to pass it on.
Do you stop accepting mail from family or customers because they have been infected? 
I know people in their 70s who just can't grasp the idea of virus-checking, and others who can't be bothered. I have checked all my PCs for years and that is why I am paranoid about Linux - it seems too easy in this regard.

 I have had some good help on this forum but it still begs the question - if Linux is so secure why is there a whole forum devoted to security??? 
(A forum that I don't yet understand - they all seem too advanced for beginners)

I really like this OS and it is already my main OS, (I use Windows less each week), but while I am prepared to stumble along learning Ubuntu/linux I want to be sure I address the one area where I could do harm inadvertently -i.e:  all the viruses etc one can pass on to others.

---

### Post by Perfect Storm on 2006-09-21
It's more like security fixes etc. and firewall(s). 

The good thing with open source is everybody can have a look what's going on when you run X application/lib, so everybody who looks into the codes and say "AHA!" here's something that need a fix or a change. Then contacting the devs about the security hole and then it getting a fix or fixing themself.
That's the problem with close source. Noone knows if the X application/lib is a security risk, until it's too late.

Another view is that the diffrence that Windows contra Linux is build and how it's setup by default. Also to mention the diffrences between distros that makes it more harder to write a virus to hit every linux system.

Thirdly you have a central place to get packages for eg. Ubuntu if you stick to the official repo. your chances to get a virus = 0.

---

### Post by rovernaut on 2006-09-21
I'm trialing Panda at the moment. Being like you a ex windoze user so paranoid on security.
Especially with online banking etc. 
One thing I notice is my Kubuntu is now a lot slower with Panda installed.
 Boot time is also increased as it does a boot scan.
I tied a trial Panda version once on Windows and It was a real Pest to uninstall and get rid of off my stem.
Ubuntu has a few free AV's, There Guard dog Firewall, KlamAV or Clamav, aegis, etc.
But you have to manually scan files with those.

---

### Post by EddieA on 2006-09-21
I won't be too happy if it slows my system down - I'm using an old machine as it is. :( 

I've managed to work my way through this:
[  Re: Are firestarter and clamav really necessary]("http://www.ubuntuforums.org/showthread.php?t=131616")

-but I  still feel we need to take action to prevent sending infections to Win users - 'humanity to others' but also just being responsible. 

I'll set up some kind of firewall as this seems to be a good idea and use av for  emails.

Despite all the advice in the link above an 'automatic' system would still obviate some of the human error - we are all capable of doings something stupid like clicking on something we shouldn't have not checking when we install something as root. Beginners have enough problemns anyway. Anything that lessens the load on the general user must be a good thing - arguments about 'false sense of security' don't add up - anything that lessens the spread of viruses etc helps.

For beginners to Linux (and general users) it's also not much point saying everything is closed down when you install - how do you check it and keep it that way etc?  Saying 'only use the repository' may be good advice but there are many programs not available this way and there are also the many types of documents etc that one downloads. it seems that '.debs' shouldn't be trusted, 'binaries' avoided, can't check all the source code (even if I could read 'c'). As for Ubuntu updates 'Firefox' needs updating and it's still not available in the repos.

It also seems very complacent to say there are not many Linux viruses etc 'out there' , we aren't being targeted etc  - when do we start taking precautions?  Words like 'horses' and 'stable doors' come to mind.

A  simple checklist of do's and dont's for all users, a list of checks to perform on your system  and a program to sort out most of it  'automatically' would help most users. 
 
Sooooo confusing for newbies (hate that term) - I know i am a beginner but I am just trying to find definitive info , a good (not necessarily perfect, but that would help ) solution which enables people to still use their machines. 

Do users want to spend all their time looking over their shoulder or getting on with their tasks. 

Anyway here's a quote:

[Linux vs. Windows Viruses]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")
> Security is, as we all know, a process, not a product. So when you use Linux, you're not using a perfectly safe OS. There is no such thing. But Linux and Mac OS X establish a more secure footing than Microsoft Windows, one that makes it far harder for viruses to take hold in the first place, but if one does take hold, harder to damage the system, but if one succeeds in damaging the system, harder to spread to other machines and repeat the process. When it comes to email-borne viruses and worms, Linux may not be completely immune - after all, nothing is immune to human gullibility and stupidity - but it is much more resistant.

---

### Post by xyz on 2006-09-21
Just one question:
Why does Panda bother to 'offer' this to Ubuntu users when there's no need for it?  Or is there?

---

### Post by ramjet_1953 on 2006-09-21
I downloaed the 3 month trial, just because I too, have just escaped from Windows XP. It runs fine, auto updates and has a pop-up firewall like Zone Alarm.

I'm not sur why a previous post told you to avoid Panda, as it is one of the top rated AV packages available for windows, with heaps of awards.

I will probably only stay with it for the 3 month trial and then ditch it, as hopefully by then, my paranioa will have subsided.

Regards,
Roger :)

---

### Post by EddieA on 2006-09-21
> **ramjet_1953 said:**
> 
I will probably only stay with it for the 3 month trial and then ditch it, as hopefully by then, my paranioa will have subsided.

Regards,
Roger :)

Sounds like a plan :)

---

### Post by arkangel on 2006-09-21
1. there are  practically no viruses spyware or malware for linux, why to slow down your OS if you already know that the antivirus is not going to found  what it doesnt exist.  firewall,  there are several of free, well tested, well-integrated highly-configurable firewalls for linux, why to pay for one that noone knows how it works, if it works.

2. If you need an anti spy/malware is to protect other people when you send  an infected email (that wont affect you anyway),  still you would problably  know the content of what  you are delivering , it is not  like having  a hidden process  that does for you without you knowing it (like outlook )

---

### Post by Perfect Storm on 2006-09-21
> **xyz said:**
> Just one question:
Why does Panda bother to 'offer' this to Ubuntu users when there's no need for it?  Or is there?

They have discovered linux as potential market as more and more people are using linux. So the try to sell their stuff. It's something we'll see more off in the near future.

These anti-virus applications are good if you run an E-mail server or networking with win PCs to catch win virus' etc.

---

### Post by xyz on 2006-09-21
So if I understood you correctly, they (and more will do so in the future) try to create a market that has no need for their product...except email stuff?
A sort of "paranoia trick" which too_much_windowed_minded people might just blind walk into...

---

### Post by Perfect Storm on 2006-09-21
Aye. It's like selling sand to a person who lives in a dersert.


But as a I stated before, E-mail server and network it can come handy to protect win machines. Other than that it's waste computer power.

---

### Post by xyz on 2006-09-21
> Aye. It's like selling sand to a person who lives in a dersert.  LOL!!

...and why bother using Panda for E-mail server and network when you can get similar stuff for free!
I'm just hoping not too many freaked_out_Windows users will be buying just because spending money reassures!

---

### Post by EddieA on 2006-09-22
I don't think the last couple of replies are very helpful!  Do  you really think that a knowledge of Linux means you can tell people how the rest of the world works too?  I came for help not to be patronised and insulted.

The* vast majority* of computer users do not want to spend their time checking everything - if there is a way to cut out a lot of this then it is worth it - if there is  a way to automate a lot of this then it *is more likely to be done by the majority of users. *

Most people I come across don't even have basic knowledge of how not to proliferate viruses or spread malware etc. (and I should imagine that true also for the vast majority of users in the world- else all these things wouldn't be a problem)

Complaining about slowing your PC down is a pretty self-centred view IMO.
-  So your email gets sent a couple of seconds slower - how many seconds do you spend checking it's safe to send? Or  don't we bother bacause Linux boxes are allegedly OK and we're only sending to a Windows user anyway?

There is a laissez-faire among Linux users regarding communication with Win users' machines but ***we*** should take responsibility for what ***we*** send out - all I am trying to get is  some _definitive _answers. 

*Nobody* has stated categorically that Windows viruses etc cannot be sent inadvertently via email from a Linux machine to a Windows one (and all these undesirable things travel around the world on Linux/Unix server boxes anyway)

*Nobody* has stated categorically that OSS/Free AV programs keep their definitions up to date  - which is a prime requisite.

People ***have*** stated categorically (elsewhere) that Linux viruses do exist and will become more mumerous but it seems to be OK as they can't (yet) damage your system but they can just obliterate all that data you spent all your time on (which is the most valuable part of a PC anyway). Shouldn't we be encouraging good practice here and getting people in the habit of securing their systems?

I don't want to be mocked if I choose to use Panda - I'd rather waste money and clock cycles on that than be inconsiderate  or wilfully neglectful of my responsibilities as a member of the Internet community.

---

### Post by Perfect Storm on 2006-09-22
My replies wasn't to mock you (well it wasn't my intention). I stated hows the the whole picture looks like at current state.

If you keep your system up to date (security updates), you are best protected :)

---

### Post by xyz on 2006-09-22
Once in a while I need a little humor and I surely didn't mean or think to mock you or anybody else. Sorry if I did; I just wanted to lighten up a subject that isn't a real problem for the most part.
Besides, I also have Windows XP Home. It came pre-installed on an amazingly cheap Toshiba Satellite A 40.
Have a good day!

---

### Post by EddieA on 2006-09-22
OK - maybe I over-reacted - thanks for your replies and your help.

---

### Post by katiad on 2006-09-26
Have not used Panda for Linux. I have used it for Windows, and it was a disaster.

That said, here's my two cents on antivirus software, for windows & linux:

I run an XP box, an XP laptop (occasionally), and two ubuntu boxes behind a firewalled router. I do run a free virus program on my Windows box, though I've stopped updating it since I no longer use it for email or web browsing. I have never had a virus, except once, and that was years ago (4-5?). (Spyware is another story, but I've had little enough of it, also.)

I used to recieve a lot of viruses in my email. I wasn't notified of these through my virus scanner, but rather, simply by looking at the email I was recieving. Anything that wasn't from a friend, or a mailing list I signed up for, or something like that? Garbage, without reading it. Any attachments I wasn't expecting? Garbage, or a scan first. If you can see that you are recieving a virus (and the vast majority of the time, you can, easily, by using those methods described above), then you know better than to pass that message on to your Windows friends.

Most viruses reproduce themselves and send themselves out. That's what they're designed to do. They don't need much human interaction. They don't need YOU to do it for them. If you are infected with a virus, in Windows, you don't even need to send your friends an email to send the virus to them - the virus will do that /for you/. You just have to open your program. 

In that case, Linux is quite safe - you cannot become infected, and therefore, the *only* way to send a virus on is to actually forward someone an email with a virus attached to it, or a program with a virus attached to it. And as I said above - it's pretty easy to tell when you've got a virus attached to it. For one, don't forward random stuff to people. Especially attachments, unless you know what you're sending - and in the vast, vast majority of cases, you will. After all, if you recieve an email with an attachment titled: x8f72lfs8.pl  <--- and your friend never mentioned sending it to you, and more, you can't figure out what it is... why would you send it on to another friend? You wouldn't. I'd hope not, anyway. That's pretty common sense stuff. 

In other words - the odds of you actually sending out a virus without knowing it? If you pay ANY attention at all to what you're sending to people, you won't be doing that. Windows viruses cannot infect linux boxes, and therefore, they cannot quietly, secretly attach themselves to your emails. You would have to forward a windows virus recieved to a windows user in order to spread the infection. It's just not likely to happen unless you don't even LOOK at what you're forwarding - and they're not exactly hiding in Linux - you see every file, every attachment, even when in Windows they might be hidden from you. 

It doesn't really take much effort to "check everything" out for a virus. A simple glance at the attachments is all. If you don't recognize what it is (a photo of your cousin's dog, a music file you requested from your friend, whatever), then why forward it along?

That said, most linux anti-virus apps should be just as well updated as proprietary ones. ClamAV should be good, if you're set on installing one. I'm not discouraging you from it, by any means, but I'm not going to bother wasting resources on something that is completely useless to me. :)

---

### Post by nocturn on 2006-09-26
> **EddieA said:**
> I don't think the last couple of replies are very helpful!  Do  you really think that a knowledge of Linux means you can tell people how the rest of the world works too?  I came for help not to be patronised and insulted.


I understand that the previous answers where not helpful to you and I do understand your concern.

However, it is a common misconception that AV is a good repsonse to malware.  Because you are cataloging badness and only blocking these known culprits, you are by definition fighting a battle you cannot win as you can never catalog quick enough and never catalog everything.

I used E-mail on windows for years without ever getting or passing a virus.  But I did stear clear of Outlook (used Eudora) so I could only be infected by attachments and not by opening the mails themselves.

> 
Complaining about slowing your PC down is a pretty self-centred view IMO.
-  So your email gets sent a couple of seconds slower - how many seconds do you spend checking it's safe to send? Or  don't we bother bacause Linux boxes are allegedly OK and we're only sending to a Windows user anyway?


In part, it is.  But again, scanning on your computer, scanning on the sending SMTP, scanning on the receiving SMTP, scanning on the recipient computer and still having virusses slip through is a waste of resources and something that is bound to fail.

You can protect your windows using friends by not passing on attachments from untrusted sources (like FreeHotChicks.scr).  Secondly, you can strongly urge them to use something like Eudora, Thunderbird or The Bat! and pass on these recommendations. 

If  you like, run your attachments through a scanner (that does not have to be integrated in the mail client ans normal text mail cannot be infected).


> 
***we*** should take responsibility for what ***we*** send out - all I am trying to get is  some _definitive _answers. 


Yes, we should.  But being mindful of what you send to people goes much furhter than using a product that only detects known badness.

> 
*Nobody* has stated categorically that OSS/Free AV programs keep their definitions up to date  - which is a prime requisite.


To answer this truthfull.  It varies a lot and OSS programs like Clam do a lot better then a lot of the commercial products.  In a recent test by ISC during a virus outbreak, only one in 22 AV products had signatures for the malware in a reasonable time (which is still too slow).  ClamAV scored reasonably well, so there is no need to avoid it.

> Shouldn't we be encouraging good practice here and getting people in the habit of securing their systems?


Yes, definately.  But putting AV on everything under the sun will not solve this problem, it will only make everything so slow that it becomes useless (I'm not talking about your PC alone) while it still fails to catch malware until signatures are out (leaving thousands to hundreds of thousands of infected PC's that did have up-to-date AV).

With the rise of zero-day exploits, this exercise becomes completely futile.

Not sending out HTML mails is a good start.  Not forwarding dubious attachments a second one.  The beauty is that it will work regardless of the type of malware is known or not.

---

